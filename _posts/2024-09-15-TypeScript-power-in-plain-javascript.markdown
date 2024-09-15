---
layout: post
title:  "TypeScript's Power in Plain JavaScript"
date:   2024-09-02
categories: typescript jsdoc
---

In the ever-evolving landscape of JavaScript development, static typing has become increasingly popular, with TypeScript leading the charge. But what if you could harness the power of TypeScript without fully committing to it? Enter JSDoc typings - a hidden gem that allows you to leverage TypeScript's benefits while writing plain JavaScript. Let's dive into this powerful technique and see how it can revolutionize your coding experience.

## What is JSDoc Typing?

JSDoc typing is a method of adding type information to your JavaScript code using specially formatted comments. These comments are then interpreted by TypeScript, enabling type checking, autocompletion, and other TypeScript features without actually writing TypeScript code.

## The Benefits of JSDoc Typing

1. **No Transpilation Required**: Write plain JavaScript that runs directly in Node.js or browsers.
2. **Gradual Adoption**: Add type safety to your existing JavaScript projects incrementally.
3. **TypeScript Compatibility**: Utilize TypeScript's type system and tooling without switching languages.
4. **Enhanced Documentation**: JSDoc comments serve as both type definitions and code documentation.
5. **Improved Developer Experience**: Enjoy better autocomplete, refactoring, and error detection in JavaScript files.

## Getting Started with JSDoc Typing

Let's walk through some examples to see how JSDoc typing works in practice.

### Basic Function Typing

```javascript

/**
 * @param {number} a - The first number.
 * @param {number} b - The second number.
 * @returns {number} The sum of a and b.
 */

function add(a, b) {
  return a + b;
}

console.log(add(5, 3)); // 8
console.log(add(5, '3')); // TypeScript will flag this as an error
```

In this example, we've added type information to our add function using JSDoc comments. TypeScript will now catch type mismatches, like trying to add a string to a number.

### Complex Object Typing

```javascript
/**
 * @typedef {Object} User
 * @property {string} name - The user's name.
 * @property {number} age - The user's age.
 * @property {string} email - The user's email address.
 */

const user = {
  name: 'John Doe',
  age: 30,
  email: 'john.doe@example.com'
};
```

### Advanced TypeScript Features

```javascript
/**
 * Represents a point in 2D space.
 * @typedef {Object} Point
 * @property {number} x - The x-coordinate.
 * @property {number} y - The y-coordinate.
 */

/**
 * Calculates the distance between two points.
 * @param {Point} p1 - The first point.
 * @param {Point} p2 - The second point.
 * @returns {number} The distance between p1 and p2.
 */
function distance(p1, p2) {
  return Math.sqrt(Math.pow(p2.x - p1.x, 2) + Math.pow(p2.y - p1.y, 2));
}

const point1 = { x: 0, y: 0 };
const point2 = { x: 3, y: 4 };
console.log(distance(point1, point2)); // Output: 5
```

### Using TypeScript Types  

```javascript
/**
 * @typedef {Object} User
 * @property {string} name - The user's name.
 * @property {number} age - The user's age.
 * @property {string} email - The user's email address.
 * @property {string} role - The user's role.
 */

/**
 * @param {User} user - The user to greet.
 * @returns {string} A greeting message.
 */
function greetUser(user) {
  return `Hello, ${user.name}!`;
}
```


```javascript
/**
* @param {import ('./types').config} config - The configuration object.
*/

function configureApp(config) {
  // ...
}
```

```javascript
/**
  * Return the first element of the array.
  * @template T
  * @param {T[]} array - The array to get the first element from.
  * @returns {T} The first element of the array.
*/

function getFirst(array) {
  return array[0];
} 
``` 


## Conclusion

JSDoc typing is a powerful technique that allows you to leverage TypeScript's benefits without switching languages. By adding type information to your JavaScript code, you can enjoy better autocomplete, refactoring, and error detection. Whether you're starting a new project or modernizing an old one, JSDoc typing is a valuable skill to have in your toolkit.

So, what are you waiting for? Dive into JSDoc typing and unlock the full potential of TypeScript in your JavaScript projects!
