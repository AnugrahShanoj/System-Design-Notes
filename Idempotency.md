# 📘 System Design – Repo Day 27
## 🔁 Idempotency in Distributed Systems

---

# 1️⃣ What is Idempotency?

Idempotency means:

> Performing the same operation multiple times produces the same final result as performing it once.

The operation may be executed repeatedly, but the final state of the system remains unchanged after the first successful execution.

---

## 📌 Simple Example

Suppose a user's profile name is updated to:

Name = "Anugrah"

Whether the same request is sent:

- Once
- Twice
- Ten times

The final value remains:

Name = "Anugrah"

Therefore, this operation is idempotent.

---

# 2️⃣ Why Idempotency is Important

In distributed systems:

- Network failures occur
- Responses may be delayed
- Timeouts happen
- Connections may drop unexpectedly

As a result:

The client may not know whether the request was successfully processed.

To be safe, the client retries the request.

Without idempotency:

> The same operation may be executed multiple times.

This can lead to serious problems.

---

# 3️⃣ Real-World Problem Without Idempotency

Consider an online payment:

User pays:

₹1000

Flow:

1. Payment request reaches server
2. Server processes payment successfully
3. Response is lost due to network issue

The user sees:

"Payment Failed"

User retries payment.

Now the payment is processed again.

Result:

₹2000 deducted instead of ₹1000

This creates:

- Duplicate payment
- Incorrect financial records
- Poor user experience

---

# 4️⃣ Food Ordering Example

User clicks:

Place Order

Network becomes slow.

User clicks button again.

Without idempotency:

- Order #1 created
- Order #2 created

Result:

- Duplicate orders
- Possible duplicate payments

This is a common real-world issue.

---

# 5️⃣ Idempotent vs Non-Idempotent Operations

---

## 🟢 Idempotent Operation

Example:

Update user profile:

PUT /users/1

Request:

{
  "name": "Anugrah"
}

Repeated requests:

Still produce:

name = "Anugrah"

Final state remains unchanged.

---

## 🔴 Non-Idempotent Operation

Example:

Create payment:

POST /payments

Every request creates:

- New payment record

Repeated requests create:

- Payment #1
- Payment #2
- Payment #3

Final state changes each time.

Therefore:

POST operations are generally not idempotent.

---

# 6️⃣ HTTP Methods and Idempotency

| HTTP Method | Idempotent? | Reason |
|------------|------------|---------|
| GET | ✅ Yes | Only reads data |
| PUT | ✅ Yes | Replaces resource with same value |
| DELETE | ✅ Usually Yes | Resource remains deleted |
| POST | ❌ Usually No | Creates new resource each time |
| PATCH | ⚠️ Depends | Depends on update logic |

---

## GET Example

GET /users/1

Multiple requests:

- No data modification
- Same state

Idempotent.

---

## PUT Example

PUT /users/1

Repeated update:

Same final resource state.

Idempotent.

---

## DELETE Example

DELETE /users/1

First request:

User deleted.

Second request:

User already deleted.

Final state:

User remains deleted.

Generally considered idempotent.

---

## POST Example

POST /orders

Every request:

Creates a new order.

Not idempotent.

---

# 7️⃣ Idempotency Key

Most common solution for making requests safe.

---

## What is an Idempotency Key?

An idempotency key is:

> A unique identifier attached to a request that allows the server to recognize duplicate requests.

Example:

Idempotency-Key: abc123

---

# 8️⃣ How Idempotency Key Works

Step 1:

Client sends request:

POST /payments

Idempotency-Key: abc123

---

Step 2:

Server:

- Processes payment
- Stores result

Example:

abc123 → Payment Success

---

Step 3:

Client retries request due to timeout.

Same request:

POST /payments

Idempotency-Key: abc123

---

Step 4:

Server checks key.

Finds:

abc123 already processed

Instead of processing again:

- Returns previous response

No duplicate payment occurs.

---

# 9️⃣ Payment System Example

User pays:

₹1000

Request:

Idempotency-Key = txn_101

Server:

Processes payment successfully.

Stores:

txn_101 → Success

---

User retries due to timeout.

Request again:

txn_101

Server recognizes duplicate request.

Returns existing result.

Result:

Only one payment is processed.

---

# 🔟 Idempotency in Message Queues

Message brokers like:

- Kafka
- RabbitMQ

may sometimes deliver the same message more than once.

Example:

OrderPlaced

arrives twice.

Without idempotency:

- Stock deducted twice
- Invoice generated twice

Wrong behavior.

---

## Idempotent Consumer

Consumer tracks processed messages.

If message already processed:

- Ignore duplicate
- Do not execute again

This prevents duplicate actions.

---

# 1️⃣1️⃣ Advantages of Idempotency

---

## ✅ Prevents Duplicate Processing

Avoids:

- Duplicate orders
- Duplicate payments
- Duplicate emails
- Duplicate notifications

---

## ✅ Enables Safe Retries

Clients can retry requests safely.

---

## ✅ Improves Reliability

System remains correct even during:

- Timeouts
- Network failures
- Connection drops

---

## ✅ Essential for Distributed Systems

Modern distributed systems heavily rely on retries.

Idempotency ensures retries do not create incorrect results.

---

# 1️⃣2️⃣ Real-World Use Cases

Commonly used in:

- Payment systems
- Order creation systems
- Banking applications
- Inventory updates
- Message queue consumers
- External API integrations

---

# 1️⃣3️⃣ Interview Insight

Strong SDE-1 answer:

> Idempotency ensures that executing the same operation multiple times produces the same final state as executing it once. It is used to prevent duplicate processing in distributed systems, especially for payments, orders, retries, and message queues.

---

# 🔒 Memory Lock

Idempotency →
Same operation executed multiple times gives same final result.

Needed because:
- Timeouts
- Retries
- Network failures

Idempotent Examples:
- GET
- PUT
- DELETE

Non-Idempotent Example:
- POST

Idempotency Key →
Unique request identifier used to prevent duplicate processing.

Benefits:
- Safe retries
- Prevent duplicate payments
- Prevent duplicate orders
- Improve reliability

Common Usage:
- Payments
- Orders
- Message queues
- Banking systems
