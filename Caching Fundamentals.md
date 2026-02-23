# 📘 System Design – Repo Day 7
## ⚖️ Caching – Conceptual Foundation

---

# 1️⃣ What is Caching?

Caching is a technique used in system design to improve system performance.

It refers to:

> Temporarily storing frequently accessed data in a faster storage layer so that future requests for the same data can be served quickly.

Instead of fetching the same data repeatedly from a slow database, the system can retrieve it from a faster memory location.

---

## 📌 Real-World Analogy

Imagine you frequently refer to the same page in a textbook.

Instead of opening the book every time, you take a photo of that page on your phone.

Next time:
- Accessing the photo is faster than opening the book again.

In this analogy:
- Phone gallery → Cache  
- Textbook → Database  

Cache provides faster access to frequently used data.

---

# 2️⃣ Why Do We Need Caching?

Database operations are:
- Time-consuming
- Resource-intensive
- Slower compared to in-memory access

Accessing data from:
- RAM (memory) → Very fast  
- Disk (database) → Comparatively slow  

If every user request requires fetching data directly from the database:
- Database becomes overloaded
- System latency increases
- Performance degrades

Caching helps by:
- Reducing database load
- Improving response time
- Enhancing user experience

---

## 📌 Example

In social media platforms like Instagram:

Millions of users frequently open the homepage.

If each request fetches feed data from the database:
- Database load increases
- Response time increases

Instead:
- Frequently accessed feed data is cached in memory

This allows faster data retrieval without hitting the database every time.

---

# 3️⃣ Where is Caching Used?

Caching can be implemented at different levels in a system.

---

## 🟢 Application-Level Cache

Stores frequently accessed data inside the application's memory.

Example:
User profile information that is accessed repeatedly.

---

## 🟢 Database Query Cache

Stores results of frequently executed database queries.

Example:
Top trending products or popular posts.

---

## 🟢 CDN (Content Delivery Network)

Used for caching static content such as:
- Images
- Videos
- CSS files
- JavaScript files

Example:
YouTube video thumbnails or website images.

---

# 4️⃣ Reading Data: Cache vs Database

---

## Without Cache

Client → Server → Database → Server → Client

Every request directly queries the database.
This results in higher latency and increased database load.

---

## With Cache

Client → Server → Cache → Server → Client

If requested data is present in cache:
- Database query is avoided
- Response is returned quickly

This reduces latency significantly.

---

# 5️⃣ Cache Hit vs Cache Miss

---

## 🟢 Cache Hit

When requested data is found in the cache:

- Data is returned immediately
- No database query is needed
- System responds faster

This results in low latency.

---

## 🔵 Cache Miss

When requested data is not present in the cache:

- System fetches data from the database
- Stores it in the cache
- Returns response to the client

Future requests for the same data can now be served faster.

---

# 6️⃣ Cache Invalidation (Introduction)

When data stored in the database is updated:

Cache may still contain the old value.

This leads to:

> Stale Data (Outdated data in cache)

Example:

Product price is updated in the database,  
but the cache still stores the old price.

In such cases:
- Cache must be updated or invalidated.

Cache invalidation ensures that users always receive accurate data.

Detailed invalidation strategies will be studied later.

---

# 7️⃣ What Should Be Cached? (Practical Understanding)

Caching is best suited for:

- Frequently read data
- Rarely updated data
- Non-critical consistency data

---

## Example: E-commerce Product Page

| Data Type | Should Be Cached? | Reason |
|-----------|-------------------|--------|
| Product Description | Yes | Rarely changes |
| Product Price | Yes (with care) | Frequently read |
| Product Stock Count | No | Requires real-time accuracy |
| User Cart Details | No | Frequently changing |

Avoid caching:
- Highly dynamic data
- Frequently updated data
- User-specific data requiring strong consistency

---

# 🔒 Memory Lock

Caching:
- Reduces database load
- Improves response time
- Enhances system performance

Cache Hit → Faster response  
Cache Miss → Fetch from DB  

Cache best suited for:
Frequently read, rarely updated data.

Avoid caching:
Frequently changing or accuracy-critical data.
