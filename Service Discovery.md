# 📘 System Design – Repo Day 20
## 🧭 Service Discovery in Microservices Architecture

---

# 1️⃣ What is Service Discovery?

Service Discovery is:

> A mechanism that helps services dynamically find and communicate with each other in a distributed system.

In microservices architecture:
- Multiple services run independently
- Services scale dynamically
- IP addresses and ports may change frequently

Instead of hardcoding service locations:
- Services discover each other dynamically using a discovery mechanism.

---

# 2️⃣ Why Service Discovery is Needed

In distributed systems:
- Services are continuously added or removed
- Containers restart frequently
- Cloud infrastructure changes dynamically

As a result:
- Service IP addresses may change frequently

Without service discovery:
- Services would need hardcoded addresses
- Communication becomes unreliable and difficult to maintain

---

## 📌 Example

Order Service wants to communicate with:
- Payment Service
- Notification Service

If Payment Service scales from:
- 2 instances → 20 instances

Managing all instance addresses manually becomes extremely difficult.

---

# 3️⃣ Real-World Analogy

Service discovery works similar to a phone contact list.

Instead of memorizing phone numbers:
- You search contact name
- Phone provides latest number

Similarly:
- Services ask the discovery system:
  “Where is Payment Service running?”

The discovery system provides:
- Available service instances
- Their latest addresses

---

# 4️⃣ Basic Service Discovery Flow

---

## 📌 Step 1: Service Registration

When a service starts:
- It registers itself with the Service Registry

The registry stores:
- Service name
- IP address
- Port
- Health status

Example:
Payment Service registers itself in the registry.

---

## 📌 Step 2: Service Lookup

Another service requests:
- “Where is Payment Service?”

Registry returns:
- Available healthy instances

---

## 📌 Step 3: Communication

The requesting service communicates with the discovered instance.

---

# 5️⃣ What is a Service Registry?

A Service Registry is:

> A centralized database that stores information about available service instances.

It maintains:
- Service names
- IP addresses
- Ports
- Health information

---

## 📌 Examples of Service Registries

Common tools:
- Eureka
- Consul
- Zookeeper

At SDE-1 level, conceptual understanding is sufficient.

---

# 6️⃣ Health Checks

The registry must know whether a service instance is healthy.

---

## 📌 Example

Suppose:
- Payment Service crashes

If registry still routes requests there:
- Requests fail

So service registries perform:
👉 Health checks

Unhealthy instances are automatically removed from active routing.

---

# 7️⃣ Types of Service Discovery

You only need basic understanding.

---

# 🟢 Client-Side Discovery

The client/service:
- Directly queries the registry
- Selects a service instance

Flow:

Order Service → Registry → Payment Service

---

# 🟢 Server-Side Discovery

The client sends request to:
- API Gateway
- Load Balancer

Gateway/load balancer:
- Queries registry
- Routes request to appropriate service

Flow:

Order Service → Load Balancer → Payment Service

---

# 8️⃣ Advantages of Service Discovery

---

## ✅ Supports Dynamic Scaling

Services can:
- Scale up
- Scale down

Without manual reconfiguration.

---

## ✅ Better Fault Tolerance

Unhealthy instances are removed automatically.

Requests are routed only to healthy instances.

---

## ✅ Simplifies Service Communication

No need to hardcode:
- IP addresses
- Ports

---

## ✅ Cloud & Container Friendly

Works efficiently with:
- Kubernetes
- Docker containers
- Cloud infrastructure

---

# 9️⃣ Problems Without Service Discovery

Without service discovery:

Teams must manually manage:
- Service IP addresses
- Ports
- Instance tracking
- Health monitoring

This creates:
- Operational complexity
- Maintenance difficulty
- Increased failure chances

---

## 📌 Dynamic IP Problem

In cloud/container systems:
- Services restart frequently
- IP addresses change dynamically

Hardcoded addresses become unreliable quickly.

---

# 🔟 Real-World Example

Food Delivery Application:

Order Service communicates with:
- Payment Service
- Notification Service

Instead of hardcoding service addresses:
- Services are discovered dynamically using service registry.

This makes the system:
- Flexible
- Scalable
- Easier to maintain

---

# 🔒 Memory Lock

Service Discovery →
Mechanism for services to dynamically find each other

Service Registry →
Stores:
- Service names
- IPs
- Ports
- Health status

Flow:
Service registers → Registry stores info → Other services discover it

Benefits:
- Dynamic scaling
- Better fault tolerance
- Easier communication
- Cloud-friendly architecture

Without service discovery:
- Manual IP management becomes difficult
- Hardcoded addresses become unreliable