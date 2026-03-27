# 📘 System Design – Repo Day 10
## 🏗️ Vertical vs Horizontal Scaling

---

# 1️⃣ What is Scaling?

Scaling refers to:

> Increasing system capacity so that it can handle more load.

Scaling becomes necessary when:

Incoming Traffic > Current System Capacity

If we do not scale:
- Latency increases
- Requests get queued
- System may crash

Scaling ensures the system can handle increasing demand smoothly.

---

# 2️⃣ Vertical Scaling (Scale Up)

Vertical scaling means:

> Increasing the power of a single server by upgrading its hardware resources.

This can include:
- Adding more CPU cores
- Increasing RAM
- Using faster SSD storage
- Upgrading to a more powerful machine

---

## 📌 Example

Existing server:
- 4 GB RAM
- 2 CPU cores

Upgraded server:
- 16 GB RAM
- 8 CPU cores

The same server can now handle more requests.

---

## ✅ Advantages of Vertical Scaling

- Simple to implement
- No major architectural changes required
- No load balancer needed
- Easy for early-stage applications

---

## ❌ Disadvantages of Vertical Scaling

- Hardware limit exists (cannot scale infinitely)
- Expensive upgrades
- Single point of failure
- If the server crashes, entire system goes down

Vertical scaling works well for small systems but is limited for large-scale applications.

---

# 3️⃣ Horizontal Scaling (Scale Out)

Horizontal scaling means:

> Increasing system capacity by adding more servers instead of upgrading one.

Instead of using:
- One powerful server

We use:
- Multiple smaller servers

Traffic is distributed among them using a load balancer.

---

## 📌 Example

Instead of:
- 1 server handling 1000 RPS

We use:
- 5 servers handling 200 RPS each

Total capacity increases while distributing load.

---

## ✅ Advantages of Horizontal Scaling

- Can scale almost infinitely
- Better fault tolerance
- High availability
- No single point of failure
- Suitable for unpredictable traffic spikes

If one server fails:
Other servers continue serving requests.

---

## ❌ Disadvantages of Horizontal Scaling

- More complex architecture
- Requires load balancer
- Session management becomes challenging
- Data consistency becomes more complex

---

# 4️⃣ Real-World Comparison

| Vertical Scaling | Horizontal Scaling |
|------------------|-------------------|
| Upgrade single machine | Add more machines |
| Simple | More complex |
| Limited scaling | Highly scalable |
| Single point of failure | Fault tolerant |
| No load balancer required | Requires load balancer |

---

# 5️⃣ Real-World Scenario: IPL Ticket Booking System

During IPL final:
- Traffic may increase 10x or even more
- Sudden spike in user requests
- Payment and booking requests surge rapidly

Vertical scaling is not ideal because:
- Hardware limits exist
- Cannot scale instantly
- Single server failure causes system outage

Horizontal scaling is preferred because:
- Additional servers can be added
- Load balancer distributes traffic
- System can handle unpredictable spikes
- Fault tolerance improves availability

---

# 6️⃣ Interview Insight

If asked:

“How will you handle increasing traffic?”

A strong SDE-1 level answer:

> We can horizontally scale the application servers and use a load balancer to distribute traffic evenly. This allows the system to handle higher traffic and improves fault tolerance.

---

# 🔒 Memory Lock

Scaling → Increase system capacity  
Vertical Scaling → Upgrade single server  
Horizontal Scaling → Add more servers  

Vertical → Simple but limited  
Horizontal → Scalable and fault tolerant  

Modern large-scale systems prefer horizontal scaling.