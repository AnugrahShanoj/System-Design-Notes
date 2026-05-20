# 📘 System Design – Repo Day 21
## 📡 Event-Driven Architecture (EDA)

---

# 1️⃣ What is Event-Driven Architecture?

Event-Driven Architecture (EDA) is:

> A software design pattern where services communicate by producing and consuming events instead of directly calling each other.

In this architecture:
- Services become more independent
- Communication becomes asynchronous
- Systems become more scalable and loosely coupled

---

# 2️⃣ What is an Event?

An Event is:

> A notification that something important has happened in the system.

Events describe actions or state changes that already occurred.

---

## 📌 Examples of Events

- UserRegistered
- OrderPlaced
- PaymentCompleted
- FoodDelivered
- ProductAddedToCart

Events help different services react independently.

---

# 3️⃣ Traditional Direct Communication

In traditional systems:

Service A directly calls Service B.

Example:

Order Service → Notification Service

This creates:
- Tight coupling
- Dependency between services
- Failure propagation risk

---

## ⚠️ Problem

If Notification Service becomes slow or unavailable:
- Order Service may also become slow
- Entire request flow may be affected

This can create cascading failures.

---

# 4️⃣ Event-Driven Communication

Instead of direct communication:

Services publish events.

Other services independently consume those events.

---

## 📌 Example

Food Delivery Application:

User places order.

---

### Step 1: Order Service

- Saves order in database
- Publishes event:

OrderPlaced

---

### Step 2: Other Services Consume Event

Different services react independently:

- Notification Service → Sends confirmation
- Analytics Service → Updates metrics
- Delivery Service → Assigns delivery partner

The Order Service does not directly communicate with these services.

---

# 5️⃣ Core Components of Event-Driven Architecture

---

# 🟢 Event Producer

The service that creates/publishes events.

Example:
- Order Service publishes `OrderPlaced`

---

# 🟢 Event Broker / Message Broker

Central system responsible for:
- Receiving events
- Distributing events to consumers

Examples:
- Apache Kafka
- RabbitMQ

---

# 🟢 Event Consumer

Services that listen to and process events.

Examples:
- Notification Service
- Analytics Service
- Delivery Service

---

# 6️⃣ Architecture Flow

Basic event-driven flow:

Producer → Event Broker → Consumers

Steps:
1. Producer publishes event
2. Broker receives event
3. Broker distributes event to interested consumers
4. Consumers process event independently

---

# 7️⃣ Advantages of Event-Driven Architecture

---

## ✅ Loose Coupling

Services do not directly depend on each other.

Example:
- Order Service does not need to know about Notification Service internals

This improves flexibility.

---

## ✅ Better Scalability

Consumers can scale independently.

Example:
- High notification traffic
- Scale only Notification Service

---

## ✅ Improved Reliability

If one consumer fails:
- Other consumers continue processing events

Entire system does not fail.

---

## ✅ Easy Feature Addition

New services can subscribe to existing events without modifying producers.

Example:
- Add Fraud Detection Service later
- Simply subscribe to `PaymentCompleted` event

---

# 8️⃣ Real-World Example

E-commerce Application:

Event:
PaymentCompleted

Consumers:
- Email Service → Send receipt
- Shipping Service → Start delivery
- Inventory Service → Reduce stock
- Analytics Service → Update revenue metrics

All operate independently.

---

# 9️⃣ API Communication vs Event-Driven Communication

| Direct API Communication | Event-Driven Communication |
|--------------------------|-----------------------------|
| Tight coupling | Loose coupling |
| Synchronous | Asynchronous |
| Services depend directly | Services independent |
| Failure may cascade | Better fault isolation |

---

# 🔟 Challenges of Event-Driven Architecture

Event-driven systems improve scalability but introduce new complexities.

---

## ❌ Difficult Debugging

Requests may flow through multiple asynchronous services.

Tracing complete flow becomes harder.

---

## ❌ Event Ordering Problems

Events may arrive:
- Out of sequence

This can create inconsistent state.

---

## ❌ Event Duplication

Sometimes the same event may be processed multiple times.

Consumers must safely handle duplicates.

---

## ❌ Eventual Consistency

Updates across services may not happen instantly.

Different services may temporarily show slightly different data.

This is called:
👉 Eventual Consistency

---

# 1️⃣1️⃣ Real-World Insight

Modern large-scale systems heavily use event-driven architecture because it provides:
- Better scalability
- Better fault isolation
- Flexible service communication

However:
- System complexity increases
- Monitoring and debugging become more difficult

---

# 1️⃣2️⃣ Interview Insight

Strong SDE-1 level answer:

> Event-driven architecture allows services to communicate asynchronously using events, improving scalability, loose coupling, and fault isolation.

---

# 🔒 Memory Lock

Event →
Notification that something happened

EDA →
Services communicate using events

Producer →
Publishes events

Broker →
Distributes events

Consumer →
Processes events

Benefits:
- Loose coupling
- Better scalability
- Improved reliability
- Easier feature expansion

Challenges:
- Debugging complexity
- Event ordering issues
- Event duplication
- Eventual consistency