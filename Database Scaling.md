# 📘 System Design – Repo Day 11
## 🗄️ Database Scaling – Introduction

---

# 1️⃣ Why Database Scaling is Important

In any real-world system, the database plays a critical role because it stores and retrieves all application data.

When traffic increases:
- More users send requests
- More application servers are added (horizontal scaling)
- Each server sends queries to the database

This increases the load on the database significantly.

---

## 📌 Key Insight

> Even if your application servers are scalable, your system is NOT scalable unless your database can handle the increased load.

If the database becomes slow:
- API response time increases
- Requests start queueing
- Overall system performance degrades

In many systems, the database becomes the **first bottleneck**.

---

# 2️⃣ Types of Database Scaling

There are two main ways to scale a database:

1. Vertical Scaling (Scale Up)
2. Horizontal Scaling (Scale Out)

---

# 3️⃣ Vertical Scaling in Database

Vertical scaling means:

> Increasing the capacity of a single database server by upgrading its hardware.

This includes:
- Increasing RAM (for better caching and faster reads)
- Increasing CPU (for query processing)
- Using faster storage like SSD

---

## 📌 Example

A database server with:
- 8 GB RAM → upgraded to 32 GB RAM  
- 4 CPU cores → upgraded to 16 CPU cores  

This allows the database to process more queries.

---

## ✅ Advantages

- Simple to implement
- No need to change database architecture
- No need to split data

---

## ❌ Disadvantages

- Hardware limit exists (cannot scale infinitely)
- Very expensive as upgrades increase
- Single point of failure (if DB crashes, entire system fails)

---

## 🧠 When to Use

Vertical scaling is suitable:
- In early-stage applications
- When traffic is moderate

---

# 4️⃣ Horizontal Scaling in Database

Horizontal scaling means:

> Distributing data across multiple database servers instead of using a single server.

Instead of storing all data in one database:
- Data is divided and stored across multiple databases

---

## 📌 Example

User data can be split as:

- DB1 → Users 1 to 1000  
- DB2 → Users 1001 to 2000  
- DB3 → Users 2001 to 3000  

Each database handles only a portion of the total data.

This reduces load on each database.

---

## ❗ Challenges

Unlike application servers, database scaling is more complex because:

- Data is interconnected
- Queries may require multiple datasets
- Maintaining consistency is difficult

---

# 5️⃣ Why Database Scaling is Difficult

Database scaling is one of the hardest parts of system design.

---

## 🧩 Data Dependency

Different tables depend on each other.

Example:
- Orders depend on Users
- Payments depend on Orders

If data is split incorrectly:
- Relationships break
- Queries become complex

---

## 🔄 Consistency Issues

When data is distributed:
- Multiple copies may exist
- Keeping all copies consistent becomes difficult

---

## ⚙️ Complex Queries

Operations like:
- JOINs
- Aggregations

Become harder when data is spread across multiple databases.

---

# 6️⃣ Real-World Insight

In most systems:

- Database scaling is harder than application scaling
- Systems often optimize database usage instead of scaling it immediately

Common strategies include:
- Caching frequently accessed data
- Optimizing database queries
- Reducing unnecessary database calls

More advanced techniques (to be learned later):
- Read replicas
- Sharding

---

# 🔒 Memory Lock

Database → Most critical component of system  
DB Bottleneck → Slows entire system  

Vertical Scaling → Upgrade single DB server  
Horizontal Scaling → Split data across multiple DBs  

Database scaling is difficult because:
- Data dependencies
- Consistency challenges
- Complex queries  

System is only scalable if database is scalable.