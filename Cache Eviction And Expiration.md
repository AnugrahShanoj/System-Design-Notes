# 📘 System Design – Repo Day 8
## 🧠 Cache Eviction & Expiration

---

# 1️⃣ Why Can't We Store Everything in Cache?

Caching improves performance by storing frequently accessed data in memory (RAM).

However, cache is usually stored in:
- RAM (memory)

RAM is:
- Very fast
- Limited in size
- Expensive compared to disk storage

Because of limited memory:

> We cannot store all application data permanently in cache.

For example:

An e-commerce application may contain:
- Millions of products
- Millions of users

Cache cannot store all product and user data.

So:
The system must decide which data to keep and which data to remove.

---

# 2️⃣ What is Cache Eviction?

Cache eviction refers to:

> Removing some existing data from the cache to make space for new incoming data.

When cache memory becomes full:
- New data cannot be stored
- Some old data must be removed

The system must decide:
Which cached data should be removed?

This decision is made using:

👉 Cache Eviction Policies

---

# 3️⃣ Common Cache Eviction Policies

Cache eviction policies define:

> Which cached data should be removed first when cache memory becomes full.

---

## 🟢 LRU (Least Recently Used)

LRU removes:

> The data that has not been accessed for the longest time.

Assumption:
Recently accessed data is more likely to be used again in the near future.

Example:
If a product page has not been viewed for a long time,
it may be removed from cache.

---

## 🟢 LFU (Least Frequently Used)

LFU removes:

> The data that has been accessed the least number of times.

Assumption:
Frequently accessed data is more important and should remain in cache.

Example:
Rarely viewed products or content may be evicted from cache.

LFU is useful when:
Some items are consistently more popular than others.

---

## 🟢 FIFO (First In First Out)

FIFO removes:

> The data that was added to the cache earliest.

It does not consider:
- How often data is accessed
- How recently data was accessed

This makes FIFO simple but less efficient in many real-world scenarios.

---

# 4️⃣ What is Cache Expiration?

Even if cache memory has available space,
some cached data may become outdated over time.

Example:
- Product price updated in database
- Cache still holds the old price

This results in:

> Stale Data (Outdated data in cache)

So cached data should not remain in cache forever.

---

# 5️⃣ TTL (Time To Live)

TTL defines:

> How long a piece of data should remain in cache before expiring.

After the TTL duration expires:
- Cached data is removed automatically
- Next request fetches fresh data from the database
- Updated value is stored again in cache

Example:
Cache product price for 10 minutes.

After 10 minutes:
- Cache entry expires
- System retrieves fresh data from DB

---

# 6️⃣ Why Expiration is Important?

Using outdated cached data may lead to:

- Incorrect product prices
- Wrong stock availability
- Inconsistent user experience

Cache expiration ensures:
- Data freshness
- System accuracy

---

# 7️⃣ Example: YouTube Trending Videos Cache

Trending videos are:
- Accessed frequently
- Requested by millions of users

To ensure:
- Popular videos remain in cache
- Rarely watched videos are removed

LFU (Least Frequently Used) policy is preferred.

LFU helps in:
- Retaining frequently accessed content
- Improving response time
- Reducing database load

FIFO or LRU may remove popular content unintentionally.

---

# 🔒 Memory Lock

Cache Eviction → Remove old data to store new data  
LRU → Remove least recently used data  
LFU → Remove least frequently used data  
FIFO → Remove oldest cached data  
TTL → Time after which cached data expires  

Cache expiration prevents stale data.

LFU is useful for caching frequently accessed content like trending videos.

