# Application-Programming-Interface-API-Notes


## 🔗 API Key vs JWT vs OAuth – Mermaid Diagram

> ✅ Clean version (GitHub-safe, no parsing errors)

```mermaid
flowchart TD

    A[User] -->|Login or Consent| B[OAuth Provider - Google]

    B -->|Authorization Code| C[Backend]

    C -->|Generate JWT| D[JWT Token]
    D -->|Send to Frontend| E[Frontend]

    E -->|API Request with JWT| C

    C -->|Verify JWT| C

    C -->|Use API Key| F[External APIs - OpenAI or Stripe]

    C -->|Use Access Token| G[OAuth Resource APIs - Google Data]

```

---

## 🧠 How to Read This Diagram

### 🔐 OAuth (Login)

* User logs in via Google
* Backend receives authorization code and exchanges it for tokens

---

### 🔑 JWT (Session)

* Backend creates JWT
* Frontend uses JWT for authenticated requests

---

### 🔗 API Key (External Services)

* Backend uses API keys to call external services:

  * OpenAI
  * Stripe

---

## 📦 Sequence Diagram (Also Fixed)

```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant Backend
    participant OAuthProvider
    participant ExternalAPI

    User->>Frontend: Click Login with Google
    Frontend->>OAuthProvider: Redirect to login
    OAuthProvider->>Frontend: Return authorization code
    Frontend->>Backend: Send code
    Backend->>OAuthProvider: Exchange code for access token
    Backend->>Backend: Create JWT
    Backend->>Frontend: Send JWT

    Frontend->>Backend: API request with JWT
    Backend->>Backend: Verify JWT

    Backend->>ExternalAPI: Request using API key
    ExternalAPI->>Backend: Response
    Backend->>Frontend: Send data
```

---

## ⚡ One-Line Summary

**OAuth = login → JWT = session → API key = external API access**

---




