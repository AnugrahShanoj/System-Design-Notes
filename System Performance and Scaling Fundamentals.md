# 📘 System Design – Repo Day 4
## 📊 System Performance & Scaling Fundamentals

---

# 1️⃣ Latency

## 📌 Definition

Latency is:

> The time taken to process a single request from start to finish.

It is usually measured in:
- Milliseconds (ms)
- Seconds

---

## 📌 What Latency Includes

When a user sends a request, total latency includes:

1. Network travel time (request → server)
2. Server processing time
3. Database query time
4. Response travel time (server → client)

Total of all these = End-to-End Latency

---

## 📌 Why Latency Matters

High latency leads to:
- Poor user experience
- User frustration
- Lower engagement

Example:
If Instagram feed loads in 3 seconds, it feels slow.

Lower latency = better user experience.

---

# 2️⃣ Throughput

## 📌 Definition

Throughput is:

> The number of requests a system can process per second.

Measured in:
- Requests Per Second (RPS)
- Queries Per Second (QPS)

---

## 📌 Example

If a server processes:

- 10 requests per second → Throughput = 10 RPS
- 1000 requests per second → Throughput = 1000 RPS

Higher throughput = higher capacity.

---

## 📌 Latency vs Throughput

Latency = Time per request  
Throughput = Requests per second  

They are different but related.

Example:
If latency = 100ms (0.1 sec)

Theoretical throughput (single-threaded):
1 / 0.1 = 10 RPS

⚠ Important:
Throughput also depends on concurrency and available resources.

---

# 3️⃣ QPS (Queries Per Second)

QPS is commonly used for databases.

Definition:

> Number of database queries handled per second.

Example:
If database handles 5000 QPS,
any load beyond that may degrade performance.

---

## 📌 Why QPS Matters

During system design interviews, you may be asked:

- Expected traffic?
- Peak QPS?
- Estimated load?

Even rough estimation shows system maturity.

---

# 4️⃣ Concurrency vs Parallelism

These terms are often confused.

---

## 🟢 Concurrency

Concurrency means:

> Multiple tasks are in progress at the same time.

Example:
A server handling 1000 open connections.
Tasks may share CPU time.

---

## 🟢 Parallelism

Parallelism means:

> Multiple tasks are executing at the exact same time.

Requires:
- Multiple CPU cores
- Multiple machines

---

## 📌 Analogy

One chef cooking 5 dishes:
- Switching between dishes → Concurrency

Five chefs cooking 5 dishes:
- Cooking simultaneously → Parallelism

---

# 5️⃣ Bottlenecks

## 📌 Definition

A bottleneck is:

> The component that limits overall system performance.

A system is only as fast as its slowest component.

---

## 📌 Common Bottlenecks

- Database queries
- CPU-heavy processing
- Network bandwidth
- Disk I/O
- External API calls
- Application server thread pool

---

## 📌 Example Scenario

If:
- Application server handles 10,000 RPS
- Database handles only 1,000 QPS

Database becomes the bottleneck.

---

# 6️⃣ Performance Degradation Scenario

Example:

- 1 server
- Each request takes 100ms (0.1 sec)
- Single-threaded processing

Throughput ≈ 10 RPS

If incoming traffic becomes 20 RPS:

- Server can only process 10 RPS
- Extra requests queue up
- Latency increases
- Requests may timeout

This is how overload happens.

---

# 🔒 Memory Lock

Latency → Time per request  
Throughput → Requests per second  
QPS → Database capacity  
Concurrency → Multiple tasks in progress  
Parallelism → Multiple tasks executing simultaneously  
Bottleneck → Performance limiting component  

System performance depends on:
- Latency
- Concurrency
- Resource capacity
- Bottlenecks

