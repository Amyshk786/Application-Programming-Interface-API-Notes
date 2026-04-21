## 📘 API Key – Quick Reference Notes

### 🔑 What is an API Key?

An **API key** is a unique secret string used to authenticate your application when it interacts with an external service (API).
It tells the server:

* Who is making the request
* What they’re allowed to do
* How much they can use

---

### ⚙️ How It Works

1. You sign up for a service (e.g., OpenAI, Google, Stripe)
2. You get an API key
3. You include it in your API request

Example:

```
GET /data
Authorization: Bearer YOUR_API_KEY
```

Server checks → Valid or not → Responds accordingly

---

### 🧠 Why API Keys Are Used

* **Authentication** → Identify your app
* **Authorization** → Control access
* **Rate Limiting** → Prevent abuse
* **Usage Tracking** → Billing & analytics

---

### ❌ What NOT to Do

* Never hardcode API keys in your code
* Never upload API keys to GitHub
* Never share keys publicly

Bad example:

```js
const apiKey = "my_secret_key";
```

---

### ✅ Best Practices

#### 1. Use Environment Variables

```js
const apiKey = process.env.API_KEY;
```

#### 2. Store in `.env` file

```
API_KEY=your_secret_key
```

#### 3. Add `.env` to `.gitignore`

```
.env
```

---

### 📦 Example (Node.js)

Install:

```
npm install dotenv
```

Use:

```js
require("dotenv").config();

const apiKey = process.env.API_KEY;
console.log(apiKey);
```

---

### 🔐 Security Tips

* Rotate keys regularly
* Use restricted permissions
* Use separate keys for dev & production
* Monitor usage to detect misuse

---

### 🧩 Analogy

API = Restaurant 🍽️
API Key = Secret pass 🎟️
Without it → No service
If leaked → Anyone can use your account

---

### ⚡ One-Line Summary

**API key = a secret token that lets your app securely access an external service.**

---
