# 📘 System Design – Repo Day 3
## 🔥 Non-Functional Requirements (Deep Dive – Part 2)

---

# 1️⃣ Consistency

## 📌 Definition

Consistency means:

> All users see the same data at the same time.

If data is updated, every user should read the latest value.

---

## 📌 Example

Bank account transfer:

If ₹1000 is deducted:
- Mobile app shows updated balance
- ATM shows updated balance
- Bank server shows updated balance

If one system shows old balance → inconsistency.

---

## 📌 Types of Consistency (Basic Understanding)

### 🟢 Strong Consistency

- After a write, every read returns the latest value.
- No stale data is allowed.
- Used in banking and payment systems.

Example:
After transferring money, balance must update immediately everywhere.

---

### 🟢 Eventual Consistency

- Data may not update instantly everywhere.
- Eventually, all copies become consistent.
- Temporary stale reads are acceptable.

Used in:
- Social media feeds
- Like counts
- View counts

Example:
You like a post and see 101 likes, but your friend may see 100 for a few seconds.

---

# 2️⃣ CAP Theorem (Basic Understanding)

CAP stands for:

- C → Consistency
- A → Availability
- P → Partition Tolerance

---

## 📌 What is Partition?

Partition means:

> A network failure between system components.

Example:
Two servers cannot communicate due to network issues.

---

## 📌 What CAP Theorem Says

In distributed systems, you can only guarantee **two out of these three**:

- Consistency
- Availability
- Partition Tolerance

It is impossible to guarantee all three simultaneously.

---

## 📌 Trade-Off Explanation

If network partition occurs:

You must choose:

Option 1:
Maintain Consistency  
→ Possibly reject some requests  
→ Availability reduces  

Option 2:
Maintain Availability  
→ May serve stale or inconsistent data  

Trade-offs are unavoidable.

---

## 📌 Example Systems

Banking System:
- Prioritizes Consistency + Partition Tolerance
- May reject requests to prevent wrong data

Social Media:
- Prioritizes Availability + Partition Tolerance
- May show slightly stale data

---

⚠ Note:
At SDE-1 level, conceptual understanding of CAP is enough.

---

# 3️⃣ Fault Tolerance

## 📌 Definition

Fault tolerance is:

> The ability of a system to continue operating even if some components fail.

---

## 📌 Example

If one application server crashes:
- Other servers continue handling requests
- Users do not notice major disruption

Fault tolerance improves availability.

---

## 📌 How It Is Achieved

- Multiple servers
- Load balancing
- Database replication
- Automatic failover mechanisms

---

# 4️⃣ Redundancy

## 📌 Definition

Redundancy means:

> Having backup components to reduce impact of failures.

Examples:

- Multiple application servers
- Multiple database replicas
- Multiple data centers

Redundancy adds safety through duplication.

---

## 📌 Redundancy vs Fault Tolerance

Redundancy → Extra copies exist  
Fault Tolerance → System continues working despite failures  

Redundancy enables fault tolerance.

---