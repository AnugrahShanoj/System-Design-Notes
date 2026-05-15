# 📘 System Design – Repo Day 18
## 🔐 API Gateway – Central Entry Point in Modern Systems

---

# 1️⃣ What is an API Gateway?

An API Gateway is:

> A centralized entry point that receives client requests and routes them to the appropriate backend services.

In modern systems, applications are often divided into multiple backend services such as:
- Authentication Service
- Payment Service
- Order Service
- Notification Service

Instead of clients directly communicating with all these services, requests first go through the API Gateway.

---

# 2️⃣ Why API Gateway is Needed

Without an API Gateway:

Frontend applications must:
- Know all backend service URLs
- Handle authentication separately for each service
- Manage failures and retries
- Maintain multiple network connections

This increases:
- Complexity
- Security risks
- Tight coupling between frontend and backend services

---

## 📌 With API Gateway

Frontend communicates with:
👉 A single centralized endpoint

The API Gateway then:
- Validates requests
- Routes traffic
- Handles security
- Applies request policies

This simplifies the overall system architecture.

---

# 3️⃣ Real-World Analogy

Imagine an airport.

Passengers:
- Do not directly enter airplanes

Instead:
- Everyone first passes through a central security checkpoint

That checkpoint:
- Verifies identity
- Checks permissions
- Directs passengers to correct gates

Similarly:

API Gateway:
- Receives all incoming requests
- Validates them
- Routes them to correct backend services

---

# 4️⃣ Request Flow

---

## 📌 Without API Gateway

Client directly communicates with:
- Auth Service
- Payment Service
- Order Service
- Notification Service

This makes the frontend complex.

---

## 📌 With API Gateway

Client → API Gateway → Backend Services

The client interacts with only one endpoint.

The gateway handles communication with internal services.

---

# 5️⃣ Responsibilities of API Gateway

API Gateway performs multiple important tasks.

---

# 🟢 Request Routing

The gateway decides:

> Which backend service should process a request.

Example:
- `/login` → Authentication Service
- `/orders` → Order Service
- `/payment` → Payment Service

---

# 🟢 Authentication & Authorization

The gateway can validate:
- JWT tokens
- API keys
- User permissions

This centralizes security handling.

Backend services do not need to implement authentication separately.

---

# 🟢 Rate Limiting

API Gateway can limit:
- Requests per user
- Requests per IP address

This helps prevent:
- Abuse
- Spam
- DDoS attacks
- Excessive traffic

---

# 🟢 Load Balancing

Traffic can be distributed across multiple instances of backend services.

This improves:
- Scalability
- Availability

---

# 🟢 Logging & Monitoring

Since all requests pass through the gateway:
- Logs can be collected centrally
- Failures can be monitored
- Traffic analytics can be generated

Useful for:
- Debugging
- Observability
- System monitoring

---

# 6️⃣ Advantages of API Gateway

---

## ✅ Simplifies Frontend

Frontend interacts with only one endpoint.

No need to manage multiple backend service URLs.

---

## ✅ Centralized Security

Authentication and authorization handled in one place.

---

## ✅ Better Monitoring

All requests pass through one centralized layer.

---

## ✅ Easier Backend Evolution

Backend services can evolve independently without affecting frontend clients.

---

# 7️⃣ Disadvantages of API Gateway

---

## ❌ Single Point of Failure

If API Gateway becomes unavailable:
- Entire system may become inaccessible

Therefore:
- High availability setup is important

---

## ❌ Additional Latency

Every request passes through an additional layer before reaching backend service.

This slightly increases response time.

---

## ❌ Increased Complexity

Large-scale gateways become complex because they handle:
- Security
- Routing
- Rate limiting
- Monitoring
- Traffic management

---

# 8️⃣ Real-World Example

Food Delivery Application:

Frontend sends request:

POST /place-order

API Gateway:
- Validates JWT token
- Applies rate limiting
- Routes request to Order Service

Order Service:
- Processes order

Notification Service:
- Sends confirmation asynchronously

---

# 9️⃣ Interview Insight

A strong SDE-1 level answer:

> API Gateway acts as a centralized entry point for frontend clients. It handles routing, authentication, rate limiting, monitoring, and communication with backend services.

---

# 🔒 Memory Lock

API Gateway →
Central entry point for backend services

Responsibilities:
- Request routing
- Authentication
- Authorization
- Rate limiting
- Load balancing
- Monitoring

Benefits:
- Simpler frontend
- Centralized security
- Better scalability

Drawbacks:
- Single point of failure
- Additional latency
- Increased system complexity