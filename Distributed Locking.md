# 📘 System Design – Repo Day 25
## 🔒 Distributed Locking

---

# 1️⃣ Why Distributed Locking is Needed

Modern distributed systems often run:

- Multiple servers
- Multiple service instances
- Multiple users performing actions simultaneously

When multiple systems access the same shared resource at the same time, conflicts can occur.

This creates:

> Race Conditions

Distributed locking is used to prevent such conflicts.

---

# 2️⃣ What is a Race Condition?

A race condition occurs when:

> Multiple processes or services try to access and modify the same shared resource simultaneously, leading to inconsistent results.

Outcome depends on:
- Timing
- Execution order

This makes system behavior unpredictable.

---

## 📌 Example – Inventory Problem

Suppose:

Stock:

Quantity = 1

Two users:

- User A buys product
- User B buys same product

Both requests arrive simultaneously.

Without coordination:

Both servers may:

1. Read stock = 1
2. Deduct stock
3. Confirm purchase

Result:

- Overselling
- Incorrect inventory
- Data inconsistency

This is a race condition.

---

# 3️⃣ What is a Lock?

A lock is:

> A mechanism that allows only one process to access or modify a resource at a time.

Think of a lock like:

👉 Room key

If:
- One person has key

Others:
- Must wait

This prevents simultaneous access.

---

# 4️⃣ What is Distributed Locking?

Distributed locking means:

> A locking mechanism used across multiple servers or distributed systems to ensure that only one process performs a critical operation at a time.

Unlike local locks:
- Distributed locks work across machines
- Multiple servers coordinate through shared lock system

This maintains consistency.

---

# 5️⃣ How Distributed Lock Works

Basic flow:

---

## Step 1

Service requests lock.

Example:

Lock(product_101)

---

## Step 2

Lock system checks:

- Is lock available?

If yes:
- Lock granted

---

## Step 3

Service performs critical operation.

Examples:
- Deduct stock
- Process payment
- Book ticket

---

## Step 4

Service releases lock.

Example:

Unlock(product_101)

Now:
- Other requests can proceed

---

# 6️⃣ Ticket Booking Example

Very common real-world example.

Suppose:

Movie ticket system:

Only:
- 1 seat left

Two users:

Attempt:
- Book same seat

---

## Without Lock

Both requests:

- Read seat available
- Confirm booking

Result:

- Double booking
- Inconsistent system

---

## With Distributed Lock

User A:
- Acquires lock
- Books seat
- Releases lock

User B:
- Waits
- Sees seat unavailable

Correct behavior achieved.

---

# 7️⃣ Why Local Locks Are Not Enough

Inside a single server:

We can use:
- Mutex
- Thread locks

These protect:
- One process
- One machine

---

## Problem

Distributed systems contain:

- Multiple servers

Local lock on Server A:

Does not affect:
- Server B
- Server C

Other servers know nothing about it.

Therefore:

> Local locking is insufficient for distributed systems.

Need:

👉 Distributed locking

---

# 8️⃣ Common Distributed Lock Systems

Popular distributed locking tools:

- Redis locks
- ZooKeeper
- etcd

Most common:

👉 Redis-based locking

At SDE-1 level:
Conceptual understanding is sufficient.

---

# 9️⃣ Challenges in Distributed Locking

Locks solve problems but introduce complexity.

---

## ❌ Deadlock

Deadlock occurs when:

- Lock acquired
- Never released

Other systems:
- Wait forever

This blocks progress.

---

## ❌ Lock Timeout Problem

Suppose:

Server acquires lock and crashes.

Lock may remain stuck.

Need:

👉 Automatic expiry

---

## ❌ Network Failure

Server may:
- Acquire lock
- Lose connection

This creates coordination challenges.

---

# 🔟 Lock Expiry (TTL)

Real systems use:

👉 TTL (Time To Live)

Meaning:

> Lock automatically expires after fixed duration.

Example:

Lock expires:
After 30 seconds

This prevents:
- Permanent lock blocking
- Dead systems holding lock forever

---

# 1️⃣1️⃣ Distributed Cron Job Problem

Very practical real-world scenario.

Suppose:

Application runs on:

- Server 1
- Server 2
- Server 3
- Server 4
- Server 5

All servers have same cron job:

Generate Monthly Report

Scheduled:

12:00 AM

---

## Problem Without Distributed Lock

At midnight:

All servers think:

> "I should execute this job."

Result:

All servers:

- Generate report
- Run heavy queries
- Perform same work

This causes:

- Duplicate execution
- Duplicate data
- Resource waste
- Possible inconsistency

---

## Solution Using Distributed Lock

Before execution:

Servers request:

Lock(monthly_report_job)

Only:

One server gets lock.

Example:

Server 3

Server 3:
- Runs job
- Generates report
- Releases lock

Other servers:
- Skip execution

---

## Result

Without lock:

5 executions ❌

With lock:

1 execution ✅

Correct and efficient behavior.

---

# 1️⃣2️⃣ Real-World Uses

Distributed locking commonly used in:

- Inventory systems
- Ticket booking
- Payment processing
- Distributed cron jobs
- Scheduled reports
- Leader election

Very common in distributed systems.

---

# 1️⃣3️⃣ Interview Insight

Strong SDE-1 explanation:

> Distributed locking ensures that only one distributed process can access or modify a shared resource at a time, preventing race conditions and maintaining consistency.

---

# 🔒 Memory Lock

Race Condition →
Simultaneous modification causing inconsistency

Lock →
One process accesses resource at a time

Distributed Lock →
Lock across multiple servers

Used for:
- Booking
- Inventory
- Payments
- Cron jobs

Challenges:
- Deadlock
- Timeout
- Network failure

TTL →
Automatic lock expiry

Cron Job Scenario →
Distributed lock prevents duplicate execution