# 📘 System Design – Repo Day 22
## ⚖️ CAP Theorem

---

# 1️⃣ Why CAP Theorem Exists

Modern distributed systems:
- Store data across multiple servers
- Operate over networks
- Face possible network failures

In such systems, an important question arises:

> Can a distributed system always provide:
- Consistent data
- High availability
- Fault tolerance

all at the same time?

CAP theorem explains the trade-offs involved.

---

# 2️⃣ What is CAP Theorem?

CAP theorem states:

> A distributed system can guarantee only TWO out of the following THREE properties simultaneously:

- Consistency (C)
- Availability (A)
- Partition Tolerance (P)

---

# 3️⃣ Understanding the Three Properties

---

# 🟢 Consistency (C)

Consistency means:

> Every user sees the latest updated data immediately.

After a data update:
- All servers return the same latest value

---

## 📌 Example

Bank account balance:
- Updated from ₹1000 → ₹500

Consistency means:
- Every user and every server immediately shows ₹500
- Nobody sees outdated value ₹1000

---

# 🟢 Availability (A)

Availability means:

> The system always responds to requests.

Even during failures:
- Users receive some response
- System remains operational

The returned data may or may not be the latest version.

---

## 📌 Example

User requests profile information:
- System responds successfully
- Request does not hang indefinitely

---

# 🟢 Partition Tolerance (P)

Partition tolerance means:

> The system continues functioning even if network communication between servers fails.

---

## 📌 Example

Suppose:
- Database Server A
- Database Server B

Network connection between them breaks.

Partition tolerance means:
- System still continues operating despite communication failure.

---

# 4️⃣ Why Partition Tolerance is Important

In real distributed systems:
- Network failures are unavoidable
- Servers may become temporarily disconnected

Therefore:
👉 Modern distributed systems must tolerate partitions.

This means:
- Partition tolerance is usually mandatory

As a result, the practical trade-off becomes:

👉 CP or AP

---

# 5️⃣ CP Systems (Consistency + Partition Tolerance)

CP systems prioritize:
- Correct and consistent data
- Partition tolerance

Even if:
- Some requests become temporarily unavailable

---

## 📌 Behavior During Network Partition

If servers cannot communicate:
- System may reject or delay requests
- But incorrect data is avoided

---

## 📌 Example

Banking systems

Showing incorrect account balance is unacceptable.

Better to:
- Reject request temporarily
than:
- Return inconsistent balance

---

# 6️⃣ AP Systems (Availability + Partition Tolerance)

AP systems prioritize:
- Continuous availability
- Partition tolerance

Even if:
- Data becomes temporarily inconsistent

---

## 📌 Behavior During Network Partition

System continues responding:
- Even if some servers have stale data

Eventually:
- Data becomes synchronized later

This is called:
👉 Eventual Consistency

---

## 📌 Example

Social media systems:
- Likes count
- Comments count
- Feed updates

Temporary inconsistency is acceptable.

But application should remain available.

---

# 7️⃣ What is Eventual Consistency?

Eventual consistency means:

> Different servers may temporarily contain different data, but over time all servers eventually become consistent.

---

## 📌 Example

Instagram likes:
- One server shows 100 likes
- Another shows 102 likes

After synchronization:
- Both eventually show same value

---

# 8️⃣ CA Systems

CA systems provide:
- Consistency
- Availability

But:
- Do not tolerate network partitions

In real-world distributed systems:
- Network failures are unavoidable

Therefore:
👉 Pure CA systems are rare in large-scale distributed environments.

---

# 9️⃣ Real-World Examples

| System Type | Preferred Model |
|--------------|----------------|
| Banking systems | CP |
| Payment systems | CP |
| Social media feeds | AP |
| Likes/comments systems | AP |
| DNS systems | AP |

---

# 🔟 Important Interview Insight

CAP theorem applies:

> During network partition or communication failure.

It is NOT mainly about normal system operation.

This is a very important interview point.

---

# 1️⃣1️⃣ Trade-Off Understanding

When network partition occurs:

A distributed system usually chooses between:

---

## 🟢 Consistency

- Return correct data
- May reject requests temporarily

---

## 🟢 Availability

- Continue serving requests
- May return stale/inconsistent data temporarily

---

# 🔒 Memory Lock

CAP Theorem →
Distributed system can guarantee only two of:
- Consistency
- Availability
- Partition Tolerance

Consistency →
All users see latest data

Availability →
System always responds

Partition Tolerance →
System survives network failures

CP Systems →
Prioritize correctness

AP Systems →
Prioritize availability

Eventual Consistency →
Data becomes consistent over time

Modern distributed systems usually choose:
- CP
or
- AP
