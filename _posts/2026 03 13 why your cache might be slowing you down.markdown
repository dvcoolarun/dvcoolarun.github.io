---
layout: post
title:  "Why Your Cache Might Be Slowing You Down"
date:   2026-03-13
categories: system-design caching scale
---

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Roboto+Mono:ital,wght@0,100..700;1,100..700&display=swap" rel="stylesheet">
<style>
body {
  background-color: #2b2b2b;
  color: #d4d4d4;
  font-family: "Roboto Mono", monospace;
  line-height: 1.5;
  margin: 0;
  padding: 0;
  font-size: 16px;
}
</style>

Most engineers reach for a cache the moment a system feels slow.

The instinct makes sense. Caches reduce latency. They offload the database. They are one of the most well-known patterns in system design.

But caches only help when data is reused frequently. If it is not, the cache is just adding overhead.

## The Standard Architecture

Take a URL shortener. The typical design looks like this:

```
Client → Load Balancer → API → Redis Cache → Database
```

Add Base62 encoding for IDs, shard the database, and the diagram looks complete.

Then the real question arrives.

**What happens at 10 million writes per second?**

And suddenly the diagram does not feel that convincing.

## The First Bottleneck: Writes

A traditional relational database handles maybe tens of thousands of writes per second on a single node. At scale, writes are expensive because they involve:

```
disk I/O
replication
index updates
network overhead
```

The solution is horizontal partitioning.

```
Total writes / Writes per node = Number of shards needed
```

At 10 million writes per second, with each node handling around 100k, you need roughly 100 shards.

But sharding introduces new problems: routing, hot partitions, and replication lag.

ID generation also shifts. Auto-increment IDs make the database the bottleneck. Systems at scale generate IDs externally using approaches like Snowflake-style generators or preallocated ranges.

## The Real Problem: Reads

URL shorteners are read-heavy. Most URLs are created once and clicked many times.

But traffic is not evenly distributed. It follows a power law.

A tiny number of URLs receive most of the traffic. The rest are barely touched.

This creates the **hot key problem**. One viral link generates millions of requests hitting the same shard. That shard becomes the bottleneck.

The instinct is to add a cache. But this is where it gets interesting.

## When the Cache Hurts

Suppose 90% of shortened URLs are clicked only once. Only 10% of requests will ever get a cache hit.

Every miss still looks like this:

```
check cache → miss → go to database
```

A cache lookup adds half a millisecond. A database lookup costs around 5 milliseconds. The total becomes:

```
cache miss + database = slightly slower than just the database
```

A low hit rate means the cache adds latency without reducing database load. It makes things worse.

## Cache Only the Hot Data

A better design is selective caching.

Detect which URLs receive frequent traffic and cache only those. Everything else goes directly to the database.

```
Hot URLs  →  cache
Cold URLs →  database
```

Ways to detect hot keys:

```
sliding window counters
count-min sketches
background traffic analysis
```

The cache now holds a small subset of data that accounts for most of the traffic. That is when caching actually works.

## The Thundering Herd

One more subtle failure mode.

When a cache entry expires and a thousand requests arrive at the same moment, all thousand hit the database simultaneously.

The solution is **request collapsing**. One request performs the database lookup while the others wait. When it completes, all waiting requests get the same result.

This dramatically reduces database pressure during traffic spikes.

## The Real Question

System design is not about assembling known components.

It starts with questions.

```
What is the read/write ratio?
What does the traffic distribution look like?
What are the latency requirements?
Where are the actual bottlenecks?
```

The architecture follows from the answers, not from memorized diagrams.

A useful mental shift:

Instead of asking **what should I add**, ask **what can I remove**.

If the database already handles the load, maybe a cache is unnecessary. If data is immutable, consistency problems disappear. If most requests are unique, optimizing direct lookups matters more than caching.

Removing complexity before adding it is where clear system thinking begins.
