# 📘 System Design – Repo Day 12
## 🗄️ Database Scaling – Read Replicas

---

# 1️⃣ What is a Read Replica?

A Read Replica is:

> A copy of the primary (main) database that is used only to handle read operations.

In this approach:
- **Primary Database** → Handles all write operations (INSERT, UPDATE, DELETE)
- **Replica Databases** → Handle read operations (SELECT queries)

This separation helps reduce load on the primary database.

---

# 2️⃣ Why Do We Need Read Replicas?

In most real-world systems:

> The number of read operations is much higher than write operations.

---

## 📌 Example

In a social media application:
- Millions of users view posts (read operations)
- Fewer users create or update posts (write operations)

If all read and write requests go to a single database:
- Database becomes overloaded
- Query response time increases
- System performance degrades

---

## 📌 Solution

Introduce read replicas:

- Primary DB handles writes  
- Replica DBs handle reads  

This distributes the load and improves system performance.

---

# 3️⃣ How Read Replicas Work

The system works as follows:

1. Write operations go to the Primary Database
2. The Primary Database updates its data
3. Data is copied (replicated) to Replica Databases
4. Read operations are served from Replica Databases

This process of copying data is called:

👉 Replication

---

# 4️⃣ Replication and Replication Lag

Replication is usually:

> Asynchronous (happens after the write operation)

This means:
- Data is first written to the primary database
- After a small delay, it is copied to replicas

---

## 📌 Replication Lag

Because replication is not instant:

> There is a small delay between primary update and replica update

---

## 📌 Example

User updates their profile name:

- Primary DB → Updated immediately  
- Replica DB → Updated after a few milliseconds  

If user reads data immediately:
- They may see old (stale) data from replica

This delay is called:

👉 Replication Lag

---

# 5️⃣ Advantages of Read Replicas

---

## ✅ Improved Performance

- Read load is distributed across multiple replicas
- Faster response time for users

---

## ✅ Better Scalability

- More replicas can be added as traffic increases
- System can handle more read requests

---

## ✅ Reduced Load on Primary DB

- Primary focuses only on write operations
- Improves overall system efficiency

---

## ✅ High Availability

- If one replica fails, others can still serve read requests

---

# 6️⃣ Limitations of Read Replicas

---

## ❌ Stale Data Problem

Due to replication lag:
- Replica may return outdated data

---

## ❌ Not Suitable for Critical Reads

For operations where correctness is very important, replicas should not be used.

Examples:
- Bank balance check
- Payment confirmation
- Order status immediately after update

These require strong consistency.

---

# 7️⃣ Read-After-Write Consistency

After a write operation:

> The next read should return the latest updated data.

---

## 📌 Correct Strategy

- Normal read operations → Replica DB  
- Immediate read after write → Primary DB  

---

## 📌 Example

User updates profile and refreshes page:

If read from replica:
- Old data may appear (due to replication lag)

If read from primary:
- Latest data is guaranteed

---

## 🧠 Key Insight

Replica → Improves performance  
Primary → Ensures correctness  

System design always involves balancing:
👉 Performance vs Data Consistency

---

# 🔒 Memory Lock

Read Replica → Copy of primary DB for handling reads  

Primary DB → Handles writes  
Replica DB → Handles reads  

Replication → Copying data from primary to replica  
Replication Lag → Delay in data synchronization  

Use replicas for:
- Read-heavy operations  

Avoid replicas for:
- Critical or immediate reads  

After write → Read from primary  
Normal cases → Read from replica