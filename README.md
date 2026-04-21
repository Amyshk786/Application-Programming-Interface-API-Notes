# Application-Programming-Interface-API-Notes


##  API Key vs JWT vs OAuth – Mermaid Diagram 



```mermaid
flowchart TD

    A[ User] -->|Login / Consent| B[ OAuth Provider (Google)]

    B -->|Authorization Code| C[ Your Backend]

    C -->|Generate| D[ JWT Token]
    D -->|Send to| E[ Frontend]

    E -->|API Requests with JWT| C

    C -->|Verify JWT| C

    C -->|Use API Key| F[ External APIs (OpenAI, Stripe)]

    C -->|Use Access Token| G[ OAuth Resource APIs (Google Data)]

```

---

##  How to Read This Diagram

###  OAuth (Login)

* User logs in via Google
* Your backend receives authorization and tokens

---

### 🔑 JWT (Session)

* Backend creates JWT
* Frontend uses it for authenticated requests

---

### 🔗 API Key (External Services)

* Backend uses API keys to talk to services like:

  * OpenAI
  * Stripe

---

## 📦 Optional: Sequence Diagram Version

```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant Backend
    participant OAuthProvider as OAuth (Google)
    participant ExternalAPI as External APIs

    User->>Frontend: Click "Login with Google"
    Frontend->>OAuthProvider: Redirect to login
    OAuthProvider->>Frontend: Authorization Code
    Frontend->>Backend: Send Code
    Backend->>OAuthProvider: Exchange for Access Token
    Backend->>Backend: Create JWT
    Backend->>Frontend: Send JWT

    Frontend->>Backend: API Request (JWT)
    Backend->>Backend: Verify JWT

    Backend->>ExternalAPI: Request (API Key)
    ExternalAPI->>Backend: Response
    Backend->>Frontend: Send Data
```

---

## ⚡ One-Line Summary

**OAuth = login → JWT = session → API Key = external API access**

---


