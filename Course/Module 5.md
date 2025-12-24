# Module 5 — JWT Authentication & Secure Login Flow

## 🎯 Goal

Understand how modern authentication works without sessions, and implement a secure login system using JWT the way real fintech backends do it.

By the end of this module, you will clearly know:
- What a JWT really is (and what it is NOT)
- Why JWTs are used in scalable systems
- How token expiry protects users
- How insecure JWT usage leads to critical breaches

---

## 🧠 Why This Module Matters

Many developers:
- Use JWTs without understanding them
- Store sensitive data inside tokens
- Forget expiry
- Trust the client blindly

This module fixes that mindset.
**🔑 JWTs don't make your app secure — correct usage does.**

---

## 📚 What You'll Learn

### 1️⃣ What Is a JWT (Concept First)

A JSON Web Token (JWT) is:
- A signed token
- Used to prove identity
- Stateless (server doesn't store sessions)

A JWT has three parts:
HEADER.PAYLOAD.SIGNATURE



You will understand:
- Why JWTs are readable
- Why JWTs are not encrypted
- Why signing ≠ hiding data

---

### 2️⃣ What Goes Inside a JWT (And What Never Should)

✅ Safe to include:

userId

role

token expiry (exp)

❌ Never include:

passwords

email OTPs

API keys

personal secrets



⚠️ **If it shouldn't be public, it doesn't belong in a JWT.**

---

### 3️⃣ Why JWTs Are Stateless (System Design Insight)

You will understand:
- Why servers don't store tokens
- Why JWTs scale better than sessions
- Why fintech systems prefer stateless auth

This explains:
- How Zerodha-like systems handle millions of users
- Why "logout everywhere" is harder with JWTs
- Why expiry becomes mandatory

---

### 4️⃣ Implementing the /login Route (Hands-On)

You will implement a secure login flow:
**Logical steps (no blind coding):**
1. Accept email + password
2. Check if user exists
3. Compare hashed password (bcrypt)
4. Issue JWT if valid
5. Send token to client

**Key implementation idea:**
jwt.sign(
{ id: user._id, role: user.role },
JWT_SECRET,
{ expiresIn: "15m" }
);



You will understand:
- Why expiry is short-lived
- Why refresh tokens exist (conceptual)
- Why long-lived tokens are dangerous

---

### 5️⃣ Token Expiry — Your First Line of Defense

This section explains:
- What happens when a token expires
- Why infinite tokens are a security bug
- How expiry limits damage after token leaks

**Real-world thinking:**
*"If a token is stolen, how long should the attacker have access?"*

---

### 6️⃣ Live Token Inspection (Security Awareness)

You will:
- Copy a real JWT
- Paste it into jwt.io
- Inspect header & payload
- Observe expiry timestamps

**Key realization:**
🔓 Anyone can read your JWT — but no one can modify it without breaking the signature.



This builds security intuition, not just syntax knowledge.

---

## 🧪 Self-Paced Exercises

### Exercise 1 — Token Inspection
Login and receive a JWT

Decode it using jwt.io

Identify:

userId

role

expiry time



### Exercise 2 — Expiry Experiment
Change expiry from 15m to 5m

Wait for expiry

Try accessing a protected route

Observe the failure


💡 **This teaches why expiry exists, not just how to set it.**

---

## ⚠️ Common Mistakes & Pitfalls (Critical)

❌ Treating JWT as encrypted data
❌ Putting sensitive data in token payload
❌ Forgetting token expiry
❌ Assuming JWT alone means "secure"
❌ Using JWT without HTTPS



You will explicitly avoid these mistakes going forward.

---

## 🧠 Key Concepts Reinforced

- Stateless authentication
- Token-based identity
- Trust boundaries
- Damage control through expiry
- Backend responsibility vs client trust

---

## ✅ Outcome of Module 5

By the end of this module, you will have:
✅ A working /login endpoint  
✅ JWT issuance with proper expiry  
✅ Clear understanding of token internals  
✅ Ability to explain JWTs in interviews  
✅ Security-first thinking around login flows  

**You now own authentication, not just use it.**

---

## 🔜 What's Next (Module 6 Preview)

*"Now that login works… let's protect real routes."*

In Module 6, you will:
- Build authentication middleware
- Protect routes using JWT verification
- See requests fail without tokens
- Understand how backend trust is enforced

**This is where authorization begins 🔐**
