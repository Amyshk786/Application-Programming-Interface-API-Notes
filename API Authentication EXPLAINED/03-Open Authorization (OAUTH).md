## 📘 OAuth (Open Authorization) – Quick Reference Notes

### 🔐 What is OAuth?

**OAuth** is a protocol that allows a user to **give one application limited access to their data on another service** — **without sharing their password**.

Common example:

> “Login with Google” or “Continue with Facebook”

---

### 🧠 Core Idea

Instead of giving your password to an app:

* You **authorize** it via a trusted provider
* The app gets a **token**, not your credentials

---

### ⚙️ Key Roles in OAuth

1. **Resource Owner** → User (you)
2. **Client** → App requesting access
3. **Authorization Server** → Handles login (e.g., Google)
4. **Resource Server** → API holding your data

---

### 🔄 How OAuth Works (Simplified Flow)

1. User clicks “Login with Google”
2. App redirects user to Google login page
3. User logs in & gives permission
4. Google sends back an **Authorization Code**
5. App exchanges code for an **Access Token**
6. App uses token to access user data

---

### 🎟️ Tokens in OAuth

#### 1. Access Token

* Used to access APIs
* Short-lived

Example:

```id="aa2m5p"
Authorization: Bearer ACCESS_TOKEN
```

---

#### 2. Refresh Token

* Used to get a new access token
* Long-lived

---

### 🔑 Why OAuth is Used

* No need to share passwords
* Safer and more secure
* Fine-grained permissions (scopes)
* Widely supported (SSO – Single Sign-On)

---

### 🧾 Scopes (Permissions)

Scopes define what the app can access:

Examples:

* `email` → access email
* `profile` → basic profile info

User can allow or deny specific permissions

---

### ❌ What NOT to Do

* Don’t store tokens insecurely
* Don’t request unnecessary permissions
* Don’t skip token validation

---

### ✅ Best Practices

#### 1. Use HTTPS Always

Tokens must be transmitted securely

#### 2. Validate Tokens

Check expiry and issuer

#### 3. Use Minimal Scopes

Request only what you need

#### 4. Store Tokens Safely

* Backend storage preferred
* Use HTTP-only cookies if possible

---

### 🔐 OAuth vs JWT vs API Key

| Feature       | API Key 🔑   | JWT 🔐        | OAuth 🚀                     |
| ------------- | ------------ | ------------- | ---------------------------- |
| Purpose       | App identity | User identity | Delegated access             |
| Data inside   | No           | Yes           | Token-based                  |
| Expiry        | Rare         | Yes           | Yes                          |
| Password used | No           | No            | No (user logs in separately) |

---

### 🧩 Analogy

OAuth = Hotel Key Card 🏨

* You (user) check in at reception
* You get a **limited-access card**
* Card works only for your room & time
* You never share your master password

---

### ⚡ One-Line Summary

**OAuth = a secure way to let apps access your data from another service without sharing your password.**

---
