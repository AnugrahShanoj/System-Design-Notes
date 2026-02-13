# 📘 System Design – Repo Day 1
## 🧠 What is System Design? (From Repository – Section 1)

---

# 1️⃣ What is System Design?

System Design is:

> The process of defining the architecture, components, interfaces, and data of a system to satisfy specific requirements.

It is the planning phase before implementation.

System design answers:

- What components should exist?
- How will they communicate?
- How will data flow?
- How will the system satisfy requirements?
- How will it perform under load?

System design is NOT coding.
It is structured thinking before coding.

---

# 2️⃣ Breaking Down the Definition

The definition contains four key elements:

---

## 🏗 Architecture

Architecture is the high-level structure of the system.

Example:

Client → Load Balancer → App Servers → Database → Cache

Architecture defines how the system is organized.

---

## 🧩 Components

Components are individual building blocks.

Examples:

- API server
- Authentication service
- Database
- Cache
- CDN

Each component has a clear responsibility.

---

## 🔌 Interfaces

Interfaces define how components communicate.

Examples:

- HTTP APIs
- gRPC
- Database queries
- Message queues

Interfaces act as contracts between components.

---

## 💾 Data

Data refers to how information is stored and accessed.

Examples:

- Tables
- Collections
- Indexes
- Relationships

Data design is a core part of system design.

---

# 3️⃣ Why System Design is Important

Without proper system design:

- Code becomes messy
- Scaling becomes difficult
- Performance degrades
- Failures cascade
- Maintenance becomes hard

A good system design ensures:

- Reliability
- Scalability
- Maintainability
- Performance
- Security

System design is like a blueprint before constructing a building.

---

# 4️⃣ Functional vs Non-Functional Requirements

This is a foundational concept in system design.

---

## 🟢 Functional Requirements (FR)

Functional requirements define:

> What the system should do.

They describe features.

Examples:

- User can register
- User can login
- User can upload profile picture
- User can place an order
- User can track order

Functional = Features

---

## 🔵 Non-Functional Requirements (NFR)

Non-functional requirements define:

> How the system should behave.

They describe quality attributes.

Examples:

- System should respond within 200ms
- System should handle 1 million users
- System should ensure 99.99% uptime
- System should be secure
- System should be scalable

Non-Functional = Quality / Constraints / Performance

---

# 5️⃣ Example: Food Delivery App

## Functional Requirements

- User registration & login
- View nearby restaurants
- View restaurant menu
- Add items to cart
- Remove items from cart
- Place order
- Track order
- Restaurant can update menu
- Delivery partner updates order status
- Make payment

---

## Non-Functional Requirements

- Low latency for order tracking
- Handle high traffic during peak hours
- High availability (e.g., 99.9% uptime)
- Secure user data and payments
- Easy to extend (e.g., add coupons, offers)

---

# 6️⃣ Key Distinction

If it describes a feature → Functional  
If it describes quality/performance/constraint → Non-Functional  





