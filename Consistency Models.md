# 📘 System Design – Repo Day 23
## ⚖️ Consistency Models in Distributed Systems

---

# 1️⃣ What is a Consistency Model?

A Consistency Model defines:

> The rules that determine when updated data becomes visible to users and servers in a distributed system.

It answers an important question:

> After data is updated, when should others see the updated value?

Different systems use different consistency models depending on:
- Business requirements
- Performance needs
- User experience expectations

There is no single consistency model suitable for every system.

---

# 2️⃣ Why Consistency Models Exist

Distributed systems involve:
- Multiple servers
- Data replication
- Network delays
- Replication lag
- Partition failures

Synchronizing all servers immediately can:
- Increase latency
- Reduce availability
- Slow down the system

Therefore systems make:

> Trade-offs between consistency, performance, and availability.

---

# 3️⃣ Strong Consistency

Strong consistency means:

> After data is updated, every read immediately returns the latest value.

No stale or outdated data is allowed.

---

## 📌 Example

Bank account balance:

Before update:
₹1000

After withdrawal:
₹500

Strong consistency guarantees:
- Every server
- Every user
- Every read request

Immediately shows:
₹500

Nobody sees outdated balance.

---

## 🧠 System Behavior

To guarantee strong consistency:
- System may wait for synchronization
- Responses may become slower

But correctness is guaranteed.

---

## 📌 Suitable For

- Banking systems
- Payment systems
- Financial transactions

Where:
- Incorrect data is unacceptable

---

# 4️⃣ Eventual Consistency

Eventual consistency means:

> Data may be temporarily inconsistent, but all replicas eventually become synchronized.

Temporary stale data is acceptable.

---

## 📌 Example

Instagram likes:

Server A:
100 likes

Server B:
102 likes

Initially:
- Values may differ

Later:
- Replicas synchronize
- Same value appears everywhere

---

## 🧠 System Behavior

System prioritizes:
- Availability
- Faster response

Temporary inconsistency is tolerated.

---

## 📌 Suitable For

- Social media feeds
- Likes/comments
- Recommendation systems

Where:
- Immediate correctness is less critical

---

# 5️⃣ Weak Consistency

Weak consistency means:

> No guarantee exists regarding when updated data becomes visible.

Synchronization occurs on a best-effort basis.

---

## 📌 Example

Multiplayer gaming state:

Small inconsistencies:
- Slight movement lag
- Temporary mismatch

May be acceptable.

Priority:
- Speed
- Responsiveness

---

## 📌 Suitable For

- Real-time gaming
- Streaming applications

Where:
- Latency matters more than perfect accuracy

---

# 6️⃣ Read-Your-Writes Consistency

Read-your-writes consistency means:

> After a user updates data, that same user should immediately see their own update.

This is a very practical and commonly used consistency model.

---

## 📌 Example

User updates:
- Delivery address
- Profile picture
- Username

Immediately refreshes page.

Expectation:
- User sees updated data

---

## 🧠 Why This Matters

If old data appears:
- User may think update failed
- Confidence reduces
- Poor user experience

Read-your-writes consistency improves:
- User trust
- User satisfaction

---

## 📌 Important Insight

This is not necessarily strong consistency.

Because:
- Only the updating user needs latest data
- Entire system does not require instant synchronization

This makes it:
- Practical
- Efficient

---

# 7️⃣ Monotonic Reads Consistency

Monotonic reads means:

> Once a user sees newer data, they should never see older data later.

System should move:
- Forward only
- Never backward

---

## 📌 Example

News feed:

User sees:
Version 5

Later:
Should not see:
Version 3

This would feel broken and inconsistent.

---

## 📌 Suitable For

- News feeds
- Timeline systems
- Content platforms

Where:
- Consistency of viewing experience matters

---

# 8️⃣ Comparison of Consistency Models

| Consistency Model | Guarantee | Example |
|-------------------|------------|---------|
| Strong Consistency | Latest data always | Banking |
| Eventual Consistency | Eventually synchronized | Social media |
| Weak Consistency | No timing guarantee | Gaming |
| Read-Your-Writes | User sees own updates | Profile updates |
| Monotonic Reads | Never see older data after newer data | Feed systems |

---

# 9️⃣ Why Consistency Models Matter

Consistency choice affects:

- Performance
- Latency
- Availability
- Correctness
- User experience

Different features may require:
- Different consistency guarantees

---

# 🔟 Real-World Example

E-commerce system:

Different features use different consistency models.

---

## Payment System

Needs:
👉 Strong consistency

Reason:
- Incorrect payment data unacceptable

---

## Product Recommendations

Uses:
👉 Eventual consistency

Reason:
- Small delay acceptable

---

## User Profile Update

Uses:
👉 Read-your-writes consistency

Reason:
- User should immediately see personal changes

---

# 1️⃣1️⃣ Interview Insight

Strong SDE-1 level explanation:

> Consistency models define how and when updated data becomes visible in distributed systems, allowing trade-offs between correctness, latency, and availability.

---

# 🔒 Memory Lock

Consistency Model →
Rules deciding when updated data becomes visible

Strong Consistency →
Latest data always

Eventual Consistency →
Eventually synchronized

Weak Consistency →
No timing guarantee

Read-Your-Writes →
User sees own update

Monotonic Reads →
Never move backward to older data

Different systems and features require:
- Different consistency guarantees