# MODULE 1 — Understanding Authentication & Authorization

## 🎯 Module Goal
To develop a **security-first mindset** by understanding *why authentication is one of the hardest and most critical problems* in software engineering — and why even experienced teams get it wrong.

This module is **conceptual and reflective**, designed to reshape how you think about login systems *before* you write any code.

---

## 📖 Introduction: Why This Module Exists

Most developers treat authentication as a **checklist feature**:

- Login page ✅  
- Password stored ✅  
- JWT added ✅  

But attackers treat authentication as an **entry point**.

If authentication fails:
- Every other feature becomes irrelevant
- User data, money, and trust are at risk
- Recovery is expensive and reputation damage is permanent

This module exists to help you **think like a defender before attackers think like attackers**.

---

## 🔐 Authentication vs Authorization (Foundational Concept)

### 🔑 Authentication — *Who are you?*
Authentication is the process of **proving identity**.

Examples:
- Email + password
- OTP
- OAuth login

If authentication is broken:
> An attacker can become *any user*.

---

### 🛂 Authorization — *What are you allowed to do?*
Authorization determines **permissions after identity is known**.

Examples:
- User vs Admin
- Read-only vs Write access

If authorization is broken:
> A normal user can perform admin actions.

---

### ⚠️ Critical Insight
> **Authentication must always come before authorization.**  
If identity itself is unreliable, permissions don’t matter.

---

## 🚨 Real-World Breaches: What Actually Goes Wrong

### 📌 Case 1: Instagram Credential Leaks
- Password reuse across platforms
- Weak hashing strategies
- Stolen credentials reused at scale

**Lesson:**  
Even if *your* app isn’t breached, **poor password handling makes your users vulnerable everywhere**.

---

### 📌 Case 2: Uber Breach
- Hardcoded credentials
- Over-trusted internal access
- No proper token revocation

**Lesson:**  
Security failures are often **configuration and trust issues**, not complex hacks.

---

### 💡 Reflection
Most breaches don’t happen because attackers are geniuses.  
They happen because **basic security assumptions were wrong**.

---

## 🧠 Why Login Systems Are the First Attack Surface

Attackers target login systems because:

- They are publicly exposed
- They control access to everything else
- They can be automated (bots, scripts)

Common attacker goals:
- Steal credentials
- Escalate privileges
- Maintain long-term access

---

### 🔓 Typical Attack Paths
1. Find weak password storage
2. Exploit missing rate limits
3. Abuse long-lived or permanent tokens
4. Manipulate client-side role data

---

## ❌ Common Startup Mistakes (That Cause Breaches)

### 1️⃣ Plaintext or Weakly Hashed Passwords
Storing passwords as-is or using outdated hashing algorithms.

**Why this fails:**
- Database leaks expose real passwords
- Users reuse passwords across apps

---

### 2️⃣ No Token Expiry
JWTs or session tokens that never expire.

**Why this fails:**
- A stolen token gives permanent access
- No way to force logout after compromise

---

### 3️⃣ Trusting Client-Side Roles
Accepting `role: "admin"` from frontend requests.

**Why this fails:**
- Client-side data is always untrusted
- Attackers can modify requests easily

---

### 4️⃣ Treating Security as “Later”
Delaying security decisions until after features are built.

**Why this fails:**
- Security is architectural
- Retrofitting security is harder and riskier

---

## 🧩 Key Security Concepts Introduced

### 🛡 Threat Modeling
Thinking in advance:
- What can go wrong?
- Who might attack?
- What assets are valuable?

---

### 🧪 Credential Leaks
Passwords or tokens exposed through:
- Database breaches
- Logs
- Misconfigured environments

---

### 🚧 Trust Boundaries
Understanding where **trust ends**:
- Frontend → Backend (never trust)
- External APIs
- User input

---

## 🧠 Mental Model Shift (Important)

> Authentication is not a feature.  
> It is a **risk management system**.

Your job as a backend engineer is not just to:
- Make login work

But to:
- Make abuse difficult
- Make breaches limited
- Make recovery possible

---

## ✅ Module Outcome

By the end of this module, you should be able to confidently say:

- I understand the difference between authentication and authorization
- I know why login systems are targeted first
- I can identify common authentication anti-patterns
- I think about security **before** writing code

---

## 🔜 What’s Next

In **Module 2**, we will:
- Start building a real authentication system
- Intentionally begin with an insecure version
- Prepare to *see* how attackers exploit weak setups

You will move from **security awareness** to **security implementation**.
