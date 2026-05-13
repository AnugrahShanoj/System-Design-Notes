# 📘 System Design – Repo Day 16
## 🌐 Content Delivery Network (CDN)

---

# 1️⃣ What is a CDN?

CDN stands for:

> Content Delivery Network

A CDN is:

> A geographically distributed network of servers used to deliver static content to users faster.

Instead of serving content from a single central server:
- Multiple CDN servers are placed in different locations around the world
- Users receive content from the nearest CDN server

This reduces:
- Network travel distance
- Latency
- Load on the origin server

---

# 2️⃣ Why CDN is Needed?

Without a CDN:

- Every user request goes directly to the main server
- Long-distance network communication increases latency
- Main server receives huge traffic load

This leads to:
- Slow loading
- Increased server load
- Poor user experience

---

## 📌 Example

Suppose:
- Main server is located in the USA
- User accesses website from India

Without CDN:
- Request travels India → USA → India
- Response becomes slower

With CDN:
- Content is served from nearby CDN node in India
- Faster response time

---

# 3️⃣ Real-World Analogy

Imagine a pizza shop located only in Delhi serving customers across India.

If someone orders from Kerala:
- Delivery takes a long time

Now imagine:
- Small pizza branches exist in every state

Customers receive pizza from nearest branch:
- Faster delivery
- Reduced load on main branch

In this analogy:
- Main branch → Origin Server
- Nearby branches → CDN servers

---

# 4️⃣ What Type of Content is Stored in CDN?

CDNs mainly store:

> Static Content

Static content does not change frequently and is accessed by many users.

---

## 📌 Examples of Static Content

- Images
- Videos
- CSS files
- JavaScript files
- Audio files
- Website assets
- Movie thumbnails

---

## ⚠️ Dynamic Content

Dynamic content changes frequently and is often user-specific.

Examples:
- User profile
- Shopping cart
- Live bank balance
- Subscription details

Such data is usually not directly cached in CDN because:
- Data freshness is important
- Personalized responses are required

---

# 5️⃣ How CDN Works

---

## 📌 Without CDN

Client → Origin Server

Every request reaches the main server.

This increases:
- Latency
- Bandwidth usage
- Server load

---

## 📌 With CDN

Client → Nearby CDN Server

If content exists in CDN:
- CDN serves content immediately

If content does not exist:
- CDN fetches content from origin server
- Stores a cached copy
- Future requests become faster

---

# 6️⃣ Benefits of CDN

---

## ✅ Reduced Latency

Users receive content from nearby geographical servers.

Result:
- Faster page loading
- Reduced buffering

---

## ✅ Reduced Origin Server Load

Static content is served by CDN instead of the main server.

This reduces:
- Database load
- Server bandwidth usage
- Processing overhead

---

## ✅ Better Scalability

CDNs help systems handle millions of users simultaneously.

Traffic gets distributed across multiple CDN nodes.

---

## ✅ Improved Availability

If one CDN node fails:
- Other CDN nodes continue serving content

This improves fault tolerance.

---

# 7️⃣ CDN and Caching

A CDN is essentially:

> Distributed caching at global scale

Instead of:
- One local cache server

We use:
- Multiple geographically distributed cache servers

This helps users worldwide receive faster responses.

---

# 8️⃣ Real-World Example – Netflix

In Netflix:

Suitable content for CDN:
- Movie thumbnails
- Video streaming files
- Static assets

These are:
- Frequently accessed
- Shared across many users
- Mostly static

---

## ❌ Not Suitable for CDN

Examples:
- User watch history
- Subscription details
- Personalized recommendations

Reason:
- User-specific
- Frequently changing
- Require accurate real-time data

---

# 🔒 Memory Lock

CDN → Geographically distributed caching system  

Used for:
- Static content
- Frequently accessed files

Examples:
- Images
- Videos
- CSS
- JS files

Benefits:
- Reduced latency
- Better scalability
- Reduced origin server load
- Improved availability

Avoid CDN for:
- Dynamic data
- Personalized data
- Frequently changing content