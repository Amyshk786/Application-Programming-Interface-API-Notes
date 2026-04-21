## 📘 JWT (JSON Web Token) – Quick Reference Notes

### 🔐 What is JWT?

A **JWT (JSON Web Token)** is a compact, secure way to **send information between two parties** (usually client ↔ server) as a JSON object.

It is commonly used for:

* **Authentication** (login sessions)
* **Authorization** (access control)

---

### ⚙️ Structure of a JWT

A JWT has **3 parts**, separated by dots:

```
HEADER.PAYLOAD.SIGNATURE
```

Example:

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9
.
eyJ1c2VySWQiOjEyMywiZW1haWwiOiJ0ZXN0QGV4YW1wbGUuY29tIn0
.
SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

---

### 🧩 Breakdown

#### 1. Header

Contains metadata:

```json id="a8f9x1"
{
  "alg": "HS256",
  "typ": "JWT"
}
```

---

#### 2. Payload

Contains actual data (called **claims**):

```json id="b1k7pz"
{
  "userId": 123,
  "email": "user@example.com"
}
```

⚠️ This is **NOT encrypted**, only encoded → don’t store sensitive data

---

#### 3. Signature

Used to verify token integrity:

```id="c0k9lm"
HMACSHA256(
  base64UrlEncode(header) + "." + base64UrlEncode(payload),
  secret_key
)
```

If payload is changed → signature becomes invalid ❌

---

### 🔄 How JWT Works (Login Flow)

1. User logs in
2. Server verifies credentials
3. Server creates a JWT and signs it
4. Client stores the token (usually in localStorage/cookies)
5. Client sends JWT with every request

Example request:

```id="d4v2ty"
Authorization: Bearer YOUR_JWT_TOKEN
```

Server:

* Verifies signature
* Extracts user info
* Grants/denies access

---

### 🧠 Why JWT is Used

* **Stateless authentication** (no session stored on server)
* **Fast & scalable**
* Works across different services (microservices)

---

### ❌ What NOT to Do

* Don’t store sensitive info (passwords, secrets) in payload
* Don’t use weak secret keys
* Don’t trust JWT without verifying signature

---

### ✅ Best Practices

#### 1. Use Strong Secret Key

```id="e8l1os"
MY_SECRET=super_long_random_string
```

#### 2. Set Expiry Time

```json id="f7k2qp"
{
  "exp": 1712345678
}
```

#### 3. Use HTTPS

Always send JWT over secure connection

#### 4. Store Safely

* Prefer **HTTP-only cookies** (safer)
* Avoid exposing in frontend JS if possible

---

### 📦 Example (Node.js)

Using jsonwebtoken:

```bash id="g3m9zx"
npm install jsonwebtoken
```

Create token:

```js id="h2r8vy"
const jwt = require("jsonwebtoken");

const token = jwt.sign(
  { userId: 123 },
  process.env.SECRET,
  { expiresIn: "1h" }
);
```

Verify token:

```js id="i6t4nd"
jwt.verify(token, process.env.SECRET);
```

---

### 🔐 JWT vs API Key (Quick Difference)

| Feature        | API Key 🔑   | JWT 🔐               |
| -------------- | ------------ | -------------------- |
| Purpose        | Identify app | Identify user        |
| Data inside    | No           | Yes (payload)        |
| Expiry         | Usually none | Has expiration       |
| Security level | Basic        | More secure (signed) |

---

### 🧩 Analogy

JWT = Digital ID Card 🪪

* Header = Card type
* Payload = Your details
* Signature = Official stamp

If someone edits details → stamp becomes invalid

---

### ⚡ One-Line Summary

**JWT = a signed token that securely carries user information for authentication and authorization.**

---
