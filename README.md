# Application-Programming-Interface-API-Notes



## 🔗 API Key vs JWT vs OAuth – System Diagram

> ✔️ GitHub-safe Mermaid (tested style: no emojis in nodes, clean labels)

```mermaid id="clean-flow-1"
flowchart TD

    A[User] --> B[OAuth Provider - Google]
    B --> C[Backend]

    C --> D[JWT Token]
    D --> E[Frontend]

    E --> C

    C --> F[External APIs - OpenAI Stripe]
    C --> G[OAuth Resource APIs - Google Data]
```

---

## 🧠 How It Works

### OAuth (Login)

* User logs in using Google
* OAuth provider returns authorization code
* Backend verifies and continues flow

---

### JWT (Session)

* Backend creates JWT after login
* Frontend stores and sends JWT with requests
* Backend verifies JWT on every request

---

### API Key (External Services)

* Backend uses API keys to access external services like:

  * OpenAI
  * Stripe

---

## 📦 Sequence Diagram (Fixed Version)

```mermaid id="clean-seq-1"
sequenceDiagram
    participant User
    participant Frontend
    participant Backend
    participant OAuthProvider
    participant ExternalAPI

    User->>Frontend: Login request
    Frontend->>OAuthProvider: Redirect for login
    OAuthProvider->>Frontend: Authorization code
    Frontend->>Backend: Send code
    Backend->>OAuthProvider: Exchange code for token
    Backend->>Backend: Create JWT
    Backend->>Frontend: Send JWT

    Frontend->>Backend: API request with JWT
    Backend->>Backend: Verify JWT

    Backend->>ExternalAPI: Request using API key
    ExternalAPI->>Backend: Response
    Backend->>Frontend: Return data
```

---

## ⚡ One-Line Summary

**OAuth = login identity | JWT = user session | API Key = external service access**

---
