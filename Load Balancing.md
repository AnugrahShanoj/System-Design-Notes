# 📘 System Design – Repo Day 9
## 🧭 Load Balancing – Conceptual Foundation

---

# 1️⃣ What is Load Balancing?

Load balancing is:

> The process of distributing incoming network traffic across multiple servers so that no single server becomes overloaded.

Instead of sending all incoming user requests to a single server, load balancing distributes the requests across multiple servers.

This helps in:
- Improving system performance
- Reducing response time (latency)
- Increasing system availability
- Preventing server overload

---

## 📌 Real-World Analogy

Consider a supermarket with only one billing counter.

All customers stand in one queue:
- Waiting time increases
- Billing becomes slow

Now imagine the supermarket opens five billing counters.

Customers are distributed across these counters:
- Waiting time reduces
- Billing becomes faster

In this analogy:

- Customers → Incoming requests  
- Billing counters → Application servers  
- Queue manager → Load balancer  

Load balancer distributes work efficiently among servers.

---

# 2️⃣ Why Do We Need Load Balancing?

Without load balancing:

If all incoming traffic is handled by a single server:
- That server may become overloaded
- Response time increases
- Requests may timeout
- System may crash

Even if other servers are idle.

Load balancing ensures:
Traffic is evenly distributed across multiple servers.

---

# 3️⃣ How Load Balancer Works?

Incoming request flow:

Client → Load Balancer → Server 1  
                        → Server 2  
                        → Server 3  

The load balancer receives the request first.

It then decides:
Which server should handle the request based on a load balancing algorithm.

---

# 4️⃣ Common Load Balancing Algorithms

Load balancers use different strategies to decide which server should receive the next request.

---

## 🟢 Round Robin

Requests are distributed sequentially across servers.

Example:
- Request 1 → Server A  
- Request 2 → Server B  
- Request 3 → Server C  
- Request 4 → Server A  

Ensures equal distribution of traffic.

---

## 🟢 Least Connections

Requests are sent to:

> The server with the least number of active connections.

Useful when:
Some requests take longer to process than others.

Helps in better resource utilization.

---

## 🟢 IP Hash

Requests are routed based on:

> The client's IP address.

The same user IP is always mapped to the same server.

Useful for:
Session-based systems such as login systems.

Ensures:
Session consistency.

---

# 5️⃣ Load Balancing in Login Systems

In login systems:

- User logs in
- Session data is created on a specific server

If future requests from the same user are sent to a different server:
- That server may not have session data
- User may appear logged out

This results in session inconsistency.

Using IP Hash:
- Requests from the same user are routed to the same server
- Session data remains available
- User experience remains consistent

---

# 6️⃣ Benefits of Load Balancing

Load balancing helps in:

- Improving system performance  
- Increasing system availability  
- Handling higher traffic  
- Preventing server overload  
- Providing fault tolerance  

If one server fails:
Load balancer can redirect traffic to other servers.

---

# 🔒 Memory Lock

Load Balancing → Distributes incoming traffic across multiple servers  

Round Robin → Sequential request distribution  
Least Connections → Server with fewer active connections  
IP Hash → Same user routed to same server  

IP Hash is useful for:
Session-based systems to maintain session consistency.
