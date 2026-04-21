## 🔗 API Key vs JWT vs OAuth – Combined Flow Diagram

```
                    ┌──────────────────────────┐
                    │        👤 USER           │
                    └────────────┬─────────────┘
                                 │
                                 │ Login / अनुमति
                                 ▼
                    ┌──────────────────────────┐
                    │   🔐 OAuth Provider      │
                    │   (e.g., Google)        │
                    └────────────┬─────────────┘
                                 │
                 Authorization Code / Consent
                                 │
                                 ▼
                    ┌──────────────────────────┐
                    │       🌐 YOUR APP        │
                    │   (Frontend + Backend)   │
                    └────────────┬─────────────┘
                                 │
              ┌──────────────────┼──────────────────┐
              │                  │                  │
              ▼                  ▼                  ▼

     ┌──────────────┐   ┌────────────────┐   ┌──────────────────┐
     │  🔑 API KEY   │   │   🔐 JWT TOKEN │   │ 🎟️ ACCESS TOKEN  │
     └──────┬───────┘   └────────┬───────┘   └────────┬─────────┘
            │                    │                    │
            │                    │                    │
            ▼                    ▼                    ▼

 ┌────────────────┐   ┌──────────────────┐   ┌────────────────────┐
 │ External APIs  │   │ Your Backend     │   │ OAuth Resource API │
 │ (Weather, AI)  │   │ (Auth System)    │   │ (Google Data)      │
 └────────────────┘   └──────────────────┘   └────────────────────┘
```

---

## 🧠 How They Work Together (Real Flow)

### 1️⃣ OAuth (Login Step)

* User clicks **“Login with Google”**
* OAuth provider (like Google) authenticates user
* Your app receives an **Access Token**

---

### 2️⃣ JWT (Session Management)

* Your backend creates a **JWT**
* JWT is sent to frontend
* Used for:

  * keeping user logged in
  * verifying identity on each request

Example:

```id="jwtflow1"
Authorization: Bearer JWT_TOKEN
```

---

### 3️⃣ API Key (Service Access)

* Your backend calls external services using an API key
* Example services:

  * OpenAI (AI APIs)
  * Stripe (payments)

```id="apikeyflow1"
Authorization: Bearer API_KEY
```

---

## 🔄 Full Real-World Flow

1. User logs in via OAuth (Google)
2. Your backend:

   * verifies OAuth token
   * creates a JWT
3. Frontend stores JWT
4. User makes requests → sends JWT
5. Backend verifies JWT
6. Backend calls external APIs using API key

---

## 🔐 Responsibility Breakdown

| Component | Responsibility                |
| --------- | ----------------------------- |
| OAuth     | Secure login without password |
| JWT       | Maintain user session         |
| API Key   | Access external services      |

---

## 🧩 Simple Analogy

* OAuth → Security guard verifying your identity 👮
* JWT → Wristband proving you're inside 🎫
* API Key → Staff pass to use internal tools 🔑

---

## ⚡ One-Line Summary

**OAuth logs users in → JWT keeps them logged in → API keys let your app talk to other services.**

---

## 📌 Tip for GitHub README

You can paste this section directly into your `README.md` under:

```id="readmehint"
## Authentication & API Flow
```

---
