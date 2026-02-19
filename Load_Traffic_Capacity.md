# 📘 System Design – Repo Day 5
## 📊 Load, Traffic & System Capacity

---

# 1️⃣ What is Load?

In system design, **Load** refers to:

> The total amount of work that a system needs to perform at a given time.

This work can include:
- Handling incoming user requests
- Processing business logic
- Performing database queries
- Fetching or storing data
- Serving files such as images or videos

---

## 📌 Example:

Consider a food delivery application:

At a given time:
- 100 users are browsing restaurants
- 50 users are placing orders
- 30 users are tracking delivery

Each of these actions generates:
- API calls to the backend
- Database read/write operations
- Server-side processing

All of this combined workload is called **System Load**.

---

## 📌 Why Load Matters?

Every system has limited resources such as:
- CPU
- Memory (RAM)
- Disk storage
- Network bandwidth

If the amount of work (load) increases beyond what the system can handle, system performance starts degrading.

---

# 2️⃣ What is Traffic?

Traffic refers to:

> The number of incoming requests reaching the system over a period of time.

Traffic is usually measured in:
- Requests Per Second (RPS)
- Queries Per Second (QPS)

---

## 📌 Example:

If your backend server receives:

- 1000 requests every second  
→ Traffic = 1000 RPS

Higher traffic results in higher load on the system.

Traffic directly contributes to system load.

---

# 3️⃣ Read-Heavy vs Write-Heavy Systems

Different systems behave differently depending on how users interact with them.

---

## 🟢 Read-Heavy Systems

In read-heavy systems:

> Most operations involve reading data from the system.

Examples:
- Instagram feed
- News websites
- YouTube video streaming
- Product browsing in e-commerce websites

Users mainly:
- View content
- Scroll feeds
- Search information

Few write operations occur.

---

## 🔵 Write-Heavy Systems

In write-heavy systems:

> Most operations involve modifying data.

Examples:
- Payment systems
- Banking applications
- Order placement systems
- Messaging applications

Write operations include:
- Insert new data
- Update existing data
- Delete data

Writes usually:
- Consume more resources
- Require stronger consistency
- Take more processing time

---

## 📌 Why This Matters?

System design decisions change based on system usage type.

For example:

Read-heavy systems:
- Use caching to reduce database load

Write-heavy systems:
- Focus more on consistency and reliability

---

# 4️⃣ What is Capacity?

Capacity refers to:

> The maximum amount of load a system can handle without performance degradation.

---

## 📌 Example:

If a server can process:

- 500 requests per second smoothly  
→ System Capacity = 500 RPS

If incoming traffic becomes:

- 700 RPS

Then:
- Server cannot process all requests immediately
- Some requests get delayed
- Latency increases
- Requests may fail or timeout

---

# 5️⃣ How Systems Get Overloaded?

System overload occurs when:

> Incoming Traffic > System Capacity

---

## 📌 Example:

Server capacity:
- 10 RPS

Incoming traffic:
- 20 RPS

System behaviour:
- Processes 10 requests
- Queues remaining 10 requests
- Queue continues to grow
- Latency increases
- Eventually, timeouts occur
- System may crash due to resource exhaustion

---

## 📌 Internal Effects of Overload

Over time, overload may cause:
- CPU overload
- Memory exhaustion
- Thread pool saturation
- Increased latency
- Request failures

System failure is usually gradual, not instant.

---

# 6️⃣ Basic Load Handling Idea

To handle increasing load, systems must:

- Increase processing capacity
- Reduce request processing time
- Distribute work across multiple components

This leads to system design techniques such as:
- Scaling
- Load balancing
- Caching
- Performance optimization

These techniques will be covered in upcoming topics.

---

# 🔒 Memory Lock

Load → Amount of work system performs  
Traffic → Incoming requests per unit time  
Capacity → Maximum load system can handle  
Overload → Traffic exceeds capacity  

System crash usually occurs due to:
Continuous overload → Increased latency → Resource exhaustion

