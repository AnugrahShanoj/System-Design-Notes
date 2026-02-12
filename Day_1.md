# 🧠 Foundations: What is a System? What is System Design?

---

## 1️⃣ What is a System?

A system is:

> A collection of interconnected components working together to achieve a specific goal.

### 🔎 Important Keywords

- **Collection** → More than one component  
- **Interconnected** → Components communicate with each other  
- **Goal-oriented** → Built to solve a specific problem  

---

### 📌 Example 1 – College System

- Students  
- Teachers  
- Classrooms  
- Attendance  
- Exams  

All these components together achieve the goal of education.

---

### 📌 Example 2 – Web Application System (e.g., Instagram)

Components:

- Mobile App / Web App (Client)  
- Backend Server  
- Database  
- Image Storage  
- Network  

All these working together = Complete System.

---

### 💡 Key Understanding

A backend project (like NeoAegis) is also a system.

It includes:

- Express server  
- Routes  
- Controllers  
- Database  
- Authentication  
- Middleware  

All of these are components working together.

---

## 2️⃣ What is System Design?

System Design is:

> The process of planning how different components of a system will connect, communicate, and work together before implementation.

It focuses on:

- Architecture planning  
- Data flow  
- Database structure  
- API structure  
- Performance considerations  
- Scalability thinking  

---

### 🚫 What System Design is NOT

- Not coding  
- Not writing syntax  
- Not framework-specific  
- Not language-dependent  

It is structured thinking before implementation.

---

## 3️⃣ Basic Web Architecture (3-Tier Architecture)

Most web systems follow this pattern:

> Client → Server → Database

This is called **3-Tier Architecture**.

---

### 🟢 1. Client (Presentation Layer)

The Client:

- Provides user interface (UI)  
- Takes user input  
- Sends HTTP requests  
- Displays HTTP responses  

**Examples:**

- Browser  
- Mobile app  
- React app  

Client does NOT:

- Handle core business logic  
- Directly access database  

---

### 🟡 2. Server (Application Layer)

The Server is the brain of the system.

It:

- Receives requests  
- Validates input  
- Applies business rules  
- Communicates with database  
- Sends structured response  

**Example: User clicks “Create Note”**

- Server checks authentication  
- Server validates data  
- Server saves to DB  
- Server sends success response  

---

### 🔵 3. Database (Data Layer)

The Database:

- Stores persistent data  
- Maintains relationships  
- Ensures data integrity  
- Supports efficient querying  

Without a database:

- Data disappears on restart  
- No long-term storage  

Most business systems require a database.

---

## 4️⃣ Mini System Thinking Example – To-Do App

### 🎯 Features

- Add task  
- View tasks  
- Mark complete  
- Delete task  

---

### 🔹 Step 1: Identify Components

> Client → Server → Database

---

### 🔹 Step 2: Identify Data Structure

**Table: `tasks`**

Fields:

- `id`  
- `user_id`  
- `title`  
- `completed` (boolean)  
- `created_at`  

**Why `user_id`?**  
Because multiple users will use the system.

This is **multi-user thinking** — important in system design.

---

### 🔹 Step 3: Identify APIs

- `POST /tasks`  
- `GET /tasks`  
- `PATCH /tasks/{id}`  
- `DELETE /tasks/{id}`  

System design = thinking in:

- Data  
- APIs  
- Flow  

---

## 5️⃣ Bottlenecks & Basic Failure Thinking

We explored basic failure scenarios:

---

### Scenario 1: 1 Million Users Send Requests

Possible bottleneck:

- Application Layer (server)  
- Database (if queries are heavy)  

Important concept introduced:  
👉 **Scalability**

---

### Scenario 2: Database is Slow

Effects:

- Server waits for DB response  
- Increased latency  
- Requests pile up  
- Possible cascading failure  

---

### Scenario 3: Server Crashes

Effects:

- UI may load (if static)  
- API calls fail  
- Errors like 500 / 502 / 503  
- Dynamic functionality stops working  

---

## 6️⃣ Core Formula of System Design

System Design =

1. Understand Requirements  
2. Design Architecture  
3. Design Database  
4. Design APIs  
5. Think About Scalability  

This structure will be followed for every design problem.
