# 📘 System Design – Repo Day 24
## 🗳️ Leader–Follower Replication (Primary–Replica Replication)

---

# 1️⃣ Why Replication is Needed

In large-scale systems:

A single database may need to handle:
- Millions of reads
- Millions of writes
- Large traffic spikes

This creates problems:

- Single database bottleneck
- High load
- Limited scalability
- Risk of failure

To solve this, systems use:

> Replication

Replication means:

> Maintaining multiple copies of the same database data across multiple servers.

Replication improves:
- Availability
- Fault tolerance
- Read scalability

---

# 2️⃣ What is Leader–Follower Replication?

Leader–Follower Replication is:

> A database replication strategy where one database server acts as the Leader (Primary) and handles writes, while other servers act as Followers (Replicas) and copy data from the leader.

This model is also called:
- Primary–Replica Replication
- Master–Slave Replication (older term)

Modern systems prefer:
👉 Leader–Follower terminology.

---

# 3️⃣ Leader Database

Leader is:

> The primary database responsible for handling write operations.

All writes go to leader.

Examples:
- INSERT
- UPDATE
- DELETE

---

## 📌 Example

User updates profile:

UPDATE user_profile

Request goes to:

👉 Leader DB

Leader updates data first.

---

# 4️⃣ Follower Database

Followers are:

> Replica databases that maintain copies of leader data.

Followers commonly handle:

👉 Read operations

Example:

SELECT profile

May be served from follower databases.

This reduces load on leader.

---

# 5️⃣ How Replication Works

Basic flow:

---

## Step 1

Leader receives write request.

Example:

OrderPlaced

---

## Step 2

Leader updates its local database.

---

## Step 3

Leader sends replication changes to followers.

---

## Step 4

Followers update their local copies.

Now:
- Multiple databases contain same information.

---

# 6️⃣ Types of Replication

Two common replication approaches exist.

---

# 🟢 Synchronous Replication

Synchronous replication means:

> Leader waits until followers confirm update before considering write successful.

---

## 📌 Flow

Leader:
1. Update local database
2. Wait for followers
3. Receive confirmation
4. Return success

---

## ✅ Advantages

Strong consistency.

All replicas contain:
- Same latest data

Minimal stale reads.

---

## ❌ Disadvantages

Higher latency.

Because:
- Leader must wait for followers.

Write performance may reduce.

---

# 🟢 Asynchronous Replication

Asynchronous replication means:

> Leader confirms write immediately and followers update later.

---

## 📌 Flow

Leader:
1. Update local DB
2. Return success immediately
3. Replicate later

---

## ✅ Advantages

- Faster writes
- Better performance
- Lower latency

---

## ❌ Disadvantages

Replication lag.

Followers may temporarily contain:
- Older data

This creates:
- Temporary inconsistency

---

# 7️⃣ Replication Lag

Replication lag means:

> Delay between leader update and follower synchronization.

This is common in:
- Asynchronous replication

---

## 📌 Example

User updates profile:

Leader:
- Updated immediately

Follower:
- Updates after delay

During delay:
- Follower contains stale data

---

# 8️⃣ Read-After-Write Problem

Suppose:

1. User updates profile
2. Immediately refreshes page

If read request goes to follower:

Problem:

Follower may still have:
- Old profile data

User sees:
- Stale information

This creates:

👉 Read-after-write inconsistency

and causes:
- Poor user experience
- Reduced user confidence

---

## 📌 Practical Solution

Real systems often use:

Immediately after write:
👉 Read from Leader

Normal reads:
👉 Read from Followers

This provides:
- Read-your-writes consistency
- Better UX

---

# 9️⃣ Failover

What if:

Leader crashes?

Need:

👉 Failover

Failover means:

> Promoting a follower to become the new leader.

This ensures:
- Writes continue
- System remains available

---

## 📌 Example

Leader fails.

Follower 2 promoted:

Follower → New Leader

System continues operating.

---

# 🔟 Advantages of Leader–Follower Replication

---

## ✅ Read Scalability

Followers handle read traffic.

Leader load decreases.

---

## ✅ Better Availability

Multiple replicas available.

System remains operational during failures.

---

## ✅ Fault Tolerance

Leader failure can be recovered using failover.

---

## ✅ Backup and Recovery

Followers can act as backup copies.

---

# 1️⃣1️⃣ Challenges of Leader–Follower Replication

---

## ❌ Replication Lag

Followers may return:
- Stale data

---

## ❌ Failover Complexity

Leader election and promotion:
- Complex process

Incorrect election may create:
- Split-brain issues

(Advanced topic)

---

## ❌ Write Bottleneck

All writes still go through:
👉 Leader

Leader may become bottleneck under heavy write load.

---

# 1️⃣2️⃣ Real-World Usage

Leader–Follower replication is widely used in:

- MySQL replication
- PostgreSQL replication
- MongoDB replica sets
- Cloud databases

Very common architecture.

---

# 1️⃣3️⃣ Real-World Example

Instagram:

Leader:
- Handles post creation
- Handles profile updates

Followers:
- Serve feed reads
- Handle profile viewing

This supports:
- Massive read traffic
- Better scalability

---

# 🔒 Memory Lock

Replication →
Multiple copies of data

Leader →
Handles writes

Followers →
Handle reads

Synchronous Replication →
Strong consistency, slower writes

Asynchronous Replication →
Fast writes, replication lag

Replication Lag →
Delay between leader and follower update

Failover →
Follower promoted to leader

Read-after-write issue →
Follower may return stale data

Practical solution:
- Immediate reads → Leader
- Normal reads → Followers