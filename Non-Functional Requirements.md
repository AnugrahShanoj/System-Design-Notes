# 📘 System Design – Repo Day 2
## 🔥 Non-Functional Requirements (Deep Dive – Part 1)

---

# 1️⃣ Non-Functional Requirements (NFRs)

Non-Functional Requirements define:

> How the system should behave.

They describe quality attributes, performance constraints, and system characteristics.

Unlike Functional Requirements (which define features),  
NFRs define performance, capacity, reliability, and user experience expectations.

---

# 2️⃣ Scalability

## 📌 Definition

Scalability is:

> The ability of a system to handle increasing load without breaking.

Load can mean:
- More users
- More requests
- More data
- More transactions

---

## 📌 Why Scalability Matters

Example:
A food delivery app may handle:
- 1,000 users normally
- 100,000 users during peak hours

Without scalability:
- System crashes
- Orders fail
- Revenue is lost

---

## 📌 Types of Scaling

### 🟢 Vertical Scaling (Scale Up)

Increase resources of a single machine.

Examples:
- Add more RAM
- Add more CPU
- Upgrade hardware

Advantages:
- Simple to implement

Disadvantages:
- Hardware limit exists
- Expensive
- Single point of failure

---

### 🟢 Horizontal Scaling (Scale Out)

Add more machines to distribute load.

Example:
- Instead of 1 server → use 10 servers behind a load balancer

Advantages:
- Can handle massive traffic
- Better fault tolerance

Disadvantages:
- More complex to manage

---

## 🎯 Interview Insight

At SDE-1 level, a good answer is:

> We can scale horizontally by adding more application servers behind a load balancer.

---

# 3️⃣ Availability

## 📌 Definition

Availability is:

> The percentage of time a system remains operational and accessible.

Examples:
- 99% availability → ~3.65 days downtime/year
- 99.9% availability → ~8.7 hours downtime/year
- 99.99% availability → ~52 minutes downtime/year

Higher availability = better user trust.

---

## 📌 Why It Matters

If a payment system goes down:
- Transactions fail
- Business loses revenue
- Users lose trust

---

## 📌 How Availability is Improved

- Multiple servers
- Load balancing
- Database replication
- Failover mechanisms

---

# 4️⃣ Reliability

## 📌 Definition

Reliability means:

> The system performs correctly and consistently.

A reliable system:
- Does not duplicate operations
- Does not lose data
- Maintains correctness

---

## 📌 Example: Payment System

If a user pays:
- Money must be deducted once
- Order must be confirmed
- No double charge
- No lost transaction

In payment systems:

> Reliability is more important than latency.

Correctness > Speed

---

# 5️⃣ Latency vs Throughput

These are often confused but very different.

---

## 🟢 Latency

Latency is:

> The time taken to respond to a single request.

Example:
User clicks “Order Now”
Response arrives in 150ms.

Lower latency = better user experience.

---

## 🟢 Throughput

Throughput is:

> The number of requests a system can handle per second.

Example:
System handles 10,000 requests per second.

Higher throughput = higher capacity.

---

## 🔥 Key Difference

Latency = Speed of one request  
Throughput = Total capacity of the system  

---

## 🍽 Real-World Analogy

Restaurant example:

Latency → Time to serve one customer  
Throughput → Total customers served per hour  

---

# 6️⃣ Prioritizing Non-Functional Requirements

Different systems prioritize different NFRs.

| System | Most Important NFR |
|--------|--------------------|
| Payment System | Reliability |
| Banking System | Consistency + Reliability |
| Instagram Feed | Low Latency |
| YouTube Streaming | High Throughput |
| Messaging App | Availability |

System design maturity means understanding these trade-offs.

---

# 7️⃣ Trade-Off Thinking

In real systems, you cannot maximize everything.

Examples:

- Reliability vs Latency
- Availability vs Consistency
- Simplicity vs Scalability

Payment systems prioritize:
Reliability > Latency

Social media feeds prioritize:
Latency > Strong consistency

---
