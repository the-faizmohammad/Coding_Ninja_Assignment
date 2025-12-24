# Module 2 — What We Are Building (System Design First)

> **Mindset before code:**  
> "If you don't know what you're building, you will secure the wrong thing."

---

## 🎯 Goal of This Module

Before writing a single line of code, you will clearly understand:

- **What system you are building**
- **Why each component exists**
- **How data flows through the system**
- **What 'success' looks like at the end**

This module ensures you don't treat authentication as random routes, but as a **designed security system**.

This is a **self-paced conceptual module** — no coding yet.

---

## 🧠 Why System Design Comes First

Most beginners start authentication like this:

> "Let me add a `/login` route."

Professionals start like this:

> "What threats does this system face, and where should trust begin and end?"

Authentication is not a feature.  
It is a **trust contract** between:
- Users
- Your backend
- Your database
- Your protected resources

---

## 🏗 What You Will Build (End Vision)

You will build a **Zerodha-style authentication backend**, inspired by real fintech systems.

This is **backend-only**, because:
- Security lives on the server
- Frontend is never trusted
- Fintech systems treat clients as hostile by default

---

## 🔐 Core Features of the System

By the end of this course, your backend will support:

### 1️⃣ User Registration
- Accepts user credentials
- Never stores passwords in plaintext
- Prepares data for secure login

### 2️⃣ Secure Password Storage
- Uses hashing (bcrypt)
- Uses salting automatically
- Uses a configurable cost factor

> Passwords are **never reversible**

### 3️⃣ JWT-Based Login
- Verifies user credentials
- Issues a signed token (JWT)
- No server-side sessions

### 4️⃣ Token Expiry
- Every login token expires automatically
- Prevents infinite access
- Reduces damage from token leaks

### 5️⃣ Role Foundation (User / Admin)
- Roles stored on server
- Roles embedded inside JWT
- Never trusted from frontend input

### 6️⃣ Protected Routes
- Certain routes require authentication
- Requests are validated via middleware
- Access is denied if token is missing or invalid

---

## 🔁 High-Level Architecture Flow

This is the **mental model you must remember**.

### 🧭 Registration Flow

Client
↓
POST /register
↓
Password is hashed
↓
Database stores hashed password

✔ No token  
✔ No login  
✔ Just secure storage

---

### 🧭 Login Flow

Client
↓
POST /login
↓
Password compared (hash check)
↓
JWT is issued
✔ User identity verified  
✔ Token generated  
✔ Token sent to client

---

### 🧭 Protected Route Flow

Client (with JWT)
↓
Authorization Header
↓
Middleware verifies token
↓
Request allowed or rejected


✔ No token → ❌ Access denied  
✔ Invalid token → ❌ Access denied  
✔ Valid token → ✅ Access granted  

---

## 🔒 Trust Boundaries (Very Important)

Understanding **who you trust** is critical.

| Component       | Trusted? | Why                              |
|-----------------|----------|----------------------------------|
| Frontend        | ❌ No    | Can be modified by users         |
| API Requests    | ❌ No    | Can be forged                    |
| JWT Signature   | ✅ Yes   | Cryptographically verified       |
| Database        | ⚠️ Limited | May be breached               |
| Server Logic    | ✅ Yes   | Source of truth                  |

> **Golden Rule:**  
> Never trust what the client tells you — always verify.

---

## 🧪 What We Will NOT Do (By Design)

- ❌ No client-side authentication logic
- ❌ No role checks on frontend
- ❌ No plaintext credentials
- ❌ No infinite tokens
- ❌ No "just for demo" security shortcuts

This keeps the system **production-aligned**.

---

## 🧠 Success Criteria for This Module

After completing this module, you should be able to:

- Explain the full authentication flow without code
- Draw the system architecture on paper
- Identify where attacks could happen
- Understand why each component exists

---

## ✅ Outcome

✔ You clearly understand **what you are building**  
✔ You know the **end goal before implementation**  
✔ You are ready to move from **design → secure code**

---

## 🔜 Coming Next — Module 3

> **"Now that we know what we're building, let's see how developers usually mess this up."**

In the next module, you will:
- See insecure login systems
- Observe plaintext password storage
- Understand how attackers exploit weak design

➡️ **Proceed to Module 3 — Insecure Authentication (What Not To Do)**
