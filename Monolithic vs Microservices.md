# 📘 System Design – Repo Day 19
## 🧱 Monolithic vs Microservices Architecture

---

# 1️⃣ What is Monolithic Architecture?

Monolithic architecture is:

> A software architecture where the entire application is built as a single unified codebase and deployed as one unit.

All application modules exist inside one backend application.

---

## 📌 Example

Food delivery application:

Single backend application contains:
- Authentication
- Orders
- Payments
- Notifications
- Restaurant management

Everything runs together inside one server application.

---

## 📌 Architecture Flow

Client → Monolithic Backend → Database

The backend handles all functionalities together.

---

# 2️⃣ Characteristics of Monolithic Architecture

In a monolithic system:
- Entire application has one codebase
- One deployment package
- Usually one shared database
- Modules are tightly connected

All components are dependent on the same application runtime.

---

# 3️⃣ Advantages of Monolithic Architecture

---

## ✅ Simpler Initial Development

Monoliths are easier for:
- Startups
- Small teams
- Early-stage products

Because:
- Development setup is straightforward
- Less infrastructure complexity

---

## ✅ Easier Local Development

Everything runs in one application.

Developers do not need to manage:
- Multiple services
- Service communication
- Distributed networking

---

## ✅ Easier Testing

Entire application can be tested together in one environment.

---

## ✅ Simpler Deployment

Only one application needs to be deployed.

---

# 4️⃣ Problems with Monolithic Architecture

As applications grow larger, monoliths become difficult to manage.

---

## ❌ Large Codebase

Over time:
- Code becomes difficult to understand
- Maintenance becomes harder
- Development slows down

---

## ❌ Difficult Scaling

Suppose:
Only payment functionality receives heavy traffic.

In monolithic architecture:
- Entire application must be scaled

This wastes resources.

---

## ❌ Slower Deployment

Even a small change requires:
- Rebuilding
- Testing
- Deploying the entire application

This increases deployment risk.

---

## ❌ Tight Coupling

Modules are strongly dependent on each other.

A problem in one module may affect the entire application.

---

# 5️⃣ What are Microservices?

Microservices architecture is:

> An architectural style where the application is divided into multiple small independent services.

Each service:
- Handles a specific business functionality
- Has its own logic
- Can be deployed independently

---

## 📌 Example

Food delivery application split into services:

- Auth Service
- Order Service
- Payment Service
- Notification Service

Each service works independently.

---

## 📌 Architecture Flow

Client → API Gateway → Microservices

The API Gateway routes requests to the appropriate service.

---

# 6️⃣ Characteristics of Microservices

Each microservice:
- Has independent codebase
- Can scale independently
- Can be deployed independently
- Often owns its own database

Services communicate using:
- APIs
- Message queues
- Events

---

# 7️⃣ Advantages of Microservices

---

## ✅ Independent Scaling

Only heavily used services need scaling.

Example:
- High payment traffic
- Scale only Payment Service

This improves resource efficiency.

---

## ✅ Faster Team Development

Different teams can work independently on different services.

---

## ✅ Independent Deployment

One service can be updated and deployed without redeploying the entire system.

---

## ✅ Better Fault Isolation

If Notification Service fails:
- Order Service may still continue working

Entire application does not necessarily fail.

---

# 8️⃣ Challenges of Microservices

Microservices improve scalability but introduce significant complexity.

---

## ❌ Complex Architecture

Need to manage:
- Service communication
- Networking
- Security
- Monitoring

---

## ❌ Distributed System Challenges

Problems include:
- Network failures
- Data consistency issues
- Communication delays

---

## ❌ Difficult Debugging

Requests may pass through multiple services.

Tracking failures becomes more difficult.

---

## ❌ Higher Operational Complexity

Additional infrastructure may be needed:
- API Gateway
- Service discovery
- Monitoring tools
- Load balancers

---

# 9️⃣ Monolith vs Microservices Comparison

| Monolithic Architecture | Microservices Architecture |
|--------------------------|-----------------------------|
| Single application | Multiple independent services |
| Simple initially | More complex initially |
| Easier deployment | Independent deployment |
| Hard selective scaling | Independent scaling |
| Tightly coupled | Loosely coupled |

---

# 🔟 When to Use What?

---

## 🟢 Monolith is Suitable For

- Startups
- Small teams
- Early-stage products
- Simpler systems

---

## 🟢 Microservices are Suitable For

- Large-scale systems
- Large engineering teams
- High scalability requirements
- Complex applications

---

# 1️⃣1️⃣ Real-World Insight

Many companies:
- Initially build monolithic systems
- Later gradually migrate to microservices

Reason:
- Monoliths are simpler to start
- Microservices add operational complexity

Microservices are not automatically better.

They provide:
- Better scalability
- Better flexibility

But also:
- Higher complexity

---

# 🔒 Memory Lock

Monolith →
Single large application

Microservices →
Multiple small independent services

Monolith Advantages:
- Simple
- Easy to develop
- Easy deployment

Monolith Problems:
- Hard scaling
- Tight coupling
- Large codebase

Microservices Advantages:
- Independent scaling
- Independent deployment
- Better fault isolation

Microservices Challenges:
- Complex architecture
- Distributed system problems
- Difficult debugging