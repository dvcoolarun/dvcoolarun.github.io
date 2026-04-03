# System-Design-Isn’t-About-Working-Code-It’s-About-Surviving-Change

> *Sharing this publicly because interviews are humbling — and someone going through the same thing might find it useful.*

I failed a system design round today. The topic: **Cart and Order modeling for an e-commerce / food delivery system.**

Looking back, I made two mistakes that I want to dissect carefully — because they're not just interview mistakes. They're the kind of design decisions that quietly become **technical debt** in real systems.

---

## Mistake #1: "Cart is just frontend state"

My first instinct was:

> *"Cart doesn't need to live on the backend. It's just what the user is looking at — local state in the browser or app."*

For simple apps, this holds up. A to-do list of items the user picked. No harm done.

But then the interviewer pushed:

- What if the user can only order from **one restaurant at a time**?
- What if you can't mix **grocery and food items** in the same cart?
- What if adding a new item needs to **override** a previous incompatible cart?

And suddenly, my "it's just UI state" model collapsed.

### Why cart becomes a backend concern

Cart management is one of the most critical backend functions, as it determines how users accumulate items, apply rules, and progress toward conversion. The backend must maintain cart state, handle multiple device sessions, validate availability, enforce pricing logic, and manage time-based expiry of cart data.

In the Shopping Cart bounded context, Cart is an Entity. The cart has different behaviors such as add a product, remove the product, checkout, etc. The cart also has identity and a lifecycle associated with it.

This is the key insight: **Cart has identity and lifecycle.** It's not a dumb container — it's a domain object with rules.

### The mental shift: Frontend vs. Backend ownership

```
❌ Naive mental model:

  User picks items
        │
        ▼
  Frontend stores it locally
        │
        ▼
  User hits "checkout" → backend sees it for first time

Problems:
  - No validation until checkout
  - Business rules enforced too late
  - Multi-device sync breaks
  - No single source of truth
```

```
✅ Correct mental model:

  User picks items
        │
        ▼
  Frontend sends request to Cart Service
        │
        ▼
  Cart Service enforces rules immediately:
    ├── Is this from the same outlet? ✅ / ❌
    ├── Does this mix grocery + food? ✅ / ❌
    └── Should existing cart be cleared? ✅ / ❌
        │
        ▼
  Frontend only reflects what the backend confirms

Single source of truth. Rules enforced at the right layer.
```

### Who owns what

| Concern | Owner |
|---------|-------|
| Showing items visually | Frontend |
| Enforcing "one outlet per cart" | Backend |
| Calculating totals in real-time | Backend (with cache) |
| Handling cross-device sessions | Backend |
| Business rule: max cart size | Backend |
| Animations, loading states | Frontend |

> **Rule of thumb:** If a rule can affect money, availability, or business integrity — the backend owns it.

This aligns with what [GeeksforGeeks describes in their e-commerce architecture guide](https://www.geeksforgeeks.org/system-design/e-commerce-architecture-system-design-for-e-commerce-website/) — the Cart Service is a distinct component that handles pricing, taxes, discounts, and the full checkout workflow.

---

## Mistake #2: Modeling Order with Boolean Flags

My second mistake was in how I modeled the Order entity. I did something like this:

```
Order {
  id
  user_id
  items[]
  is_grocery: boolean
  is_food: boolean
  is_scheduled: boolean
  is_express: boolean
  ...
}
```

It felt clean at first. Simple flags. Easy to query.

The interviewer let me run with it. Then asked:

> *"What happens when you add a new order type next quarter? Or when an order needs different validation logic depending on type? Or when you need to add behavior, not just data?"*

And I saw the problem.

### Why boolean flags don't scale

```
Year 1:
  is_grocery | is_food
  ──────────────────────
  true       | false      → grocery order
  false      | true       → food order

Year 2:
  is_grocery | is_food | is_medicine | is_alcohol
  ─────────────────────────────────────────────────
  ...

Year 3:
  if is_grocery:
    validate_expiry()
    check_cold_storage()
  elif is_food:
    validate_restaurant_hours()
    check_delivery_radius()
  elif is_medicine:
    check_prescription()
    verify_age()
  ...

💥 Conditionals everywhere.
   Every new type touches existing code.
   Tests become nightmares.
   Bugs hide in edge cases.
```

The Strategy pattern suggests that you take a class that does something specific in a lot of different ways and extract all of these algorithms into separate classes called strategies. The context delegates the work to a linked strategy object instead of executing it on its own.

Every new shipping method requires modifying the existing calculator class. You are constantly opening a class that should be stable. Each modification risks breaking existing functionality.

This is the exact trap boolean flags create — a class that should be stable keeps getting opened and modified.

### The better model: Behavior over flags

Instead of asking **"what type is this?"**, ask **"what behavior changes?"**

```
❌ Flag-based:

  Order {
    is_grocery: true
    is_food: false
  }

  // Somewhere in the codebase...
  if order.is_grocery:
    do_grocery_stuff()
  elif order.is_food:
    do_food_stuff()


✅ Strategy / Polymorphism-based:

  interface OrderType {
    validate()
    calculate_fees()
    get_fulfillment_rules()
  }

  class GroceryOrder implements OrderType { ... }
  class FoodOrder    implements OrderType { ... }
  class MedicineOrder implements OrderType { ... }

  // Usage:
  order.type.validate()     ← works for any type
  order.type.calculate_fees() ← no if/else needed
```

The Strategy Pattern makes it simple to adapt or add new behaviors without changing the existing code. Since each strategy is independent, it is possible to change or expand it without impacting other system components.

Adding a new order type? Create a new class. **Zero changes to existing code.**

### Visual comparison

```
Boolean flags — "open heart surgery" for every new type:

  GroceryOrder ──┐
  FoodOrder ─────┤──▶ One giant if/else block  ← touch this every time
  MedicineOrder ─┘


Strategy pattern — "plug in a new module":

  OrderType (interface)
       │
       ├── GroceryOrder   ← add new behavior here
       ├── FoodOrder      ← independent, isolated
       └── MedicineOrder  ← open/closed principle ✅
```

The strategy pattern enables selecting an algorithm at runtime. Instead of implementing a single algorithm directly, code receives runtime instructions as to which in a family of algorithms to use. Strategy lets the algorithm vary independently from clients that use it.

---

## The Bigger Lesson: Interviews Test for Evolution, Not Just Correctness

Both of my mistakes worked at small scale. A cart in localStorage works fine for a simple app. Boolean flags work fine when there are two types.

The interview wasn't testing whether my design **runs today**. It was testing whether my design **survives growth**.

```
What interviewers are actually evaluating:

  Your design today
        │
        ▼
  New requirement added
        │
        ├── Does it require rewriting core logic?    ← BAD
        ├── Does it touch multiple unrelated files?  ← BAD
        ├── Does it introduce new conditional chains? ← BAD
        │
        └── Or does it just add a new module/class?  ← GOOD
```

Domain Events like ProductAddedToCart, ProductRemovedFromCart, CartCheckedOut are important to business teams. Domain Events can be used as a communication mechanism between different bounded contexts.

Good system design is about modeling **real-world behavior**, not just structuring data.

---

## Key Takeaways

```
1. Frontend → manages interaction and display
   Backend  → enforces business rules

2. If a rule can affect money, availability, or
   business logic → backend owns it

3. Critical state must have a single source of truth
   Cart is not "UI state" — it's a domain entity

4. Model behavior, not flags
   Flags → conditionals → fragile code
   Strategy/polymorphism → isolated → extensible

5. Interviews test:
   "Will this survive change?" not just "Does this work?"
```

---

## What I'd Do Differently

**On Cart:**
- Model Cart as a backend service from the start
- Validate business rules at the API layer (not checkout)
- Use an event like `CartItemAdded` to trigger downstream logic (conflict detection, pricing)

**On Order:**
- Model as a base `Order` with a pluggable `OrderType` strategy
- Each type owns its own `validate()`, `calculate()`, `notify()` behavior
- Adding a new type = adding a new class, not editing existing ones

---

## Resources That Helped Me Think Through This

- [Microservices Powered by Domain-Driven Design — DZone](https://dzone.com/articles/microservices-powered-by-domain-driven-design) — excellent breakdown of Cart as an Aggregate Root in DDD
- [Scalable E-Commerce Architecture Part 2: Shopping Cart — DEV](https://dev.to/savyjs/scalable-e-commerce-architecture-part-2-shopping-cart-3blg) — deep dive on cart state management and async calculation
- [Strategy Pattern — Refactoring Guru](https://refactoring.guru/design-patterns/strategy) — the clearest explanation of strategy pattern with examples
- [Strategy Pattern in e-commerce — AlgoMaster](https://algomaster.io/learn/lld/strategy) — practical LLD walkthrough with shipping calculator example
- [E-Commerce System Design — GeeksforGeeks](https://www.geeksforgeeks.org/system-design/e-commerce-architecture-system-design-for-e-commerce-website/) — solid high-level architecture reference

---

Rejection stings. But this one was a useful one.

If you're preparing for system design interviews — practice asking not just *"does this work?"* but *"what breaks first when the requirements change?"*

That's the shift.

---

*If you've made similar mistakes or have thoughts on cart modeling — I'd genuinely love to discuss in the comments.*
