# 🚦 API Rate Limiter - Spring Boot Project

🚀 A scalable **API Rate Limiting system** built using **Java, Spring Boot, and Redis** to control the number of API requests a client can make within a specified time window.

This project demonstrates important **backend infrastructure concepts**, including:

- API protection mechanisms  
- Request throttling  
- Distributed caching with Redis  
- Middleware request filtering  
- Scalable backend architecture  

---

# 📌 Problem Statement

Public APIs can be abused if there is **no restriction on the number of requests**.

Example scenario:

```
Without Rate Limiting

User → 10,000 requests/sec → Server overload
```

A **Rate Limiter** ensures fair usage by limiting the number of requests.

Example:

```
Limit: 5 requests per minute

Request 1 → Allowed
Request 2 → Allowed
Request 3 → Allowed
Request 4 → Allowed
Request 5 → Allowed
Request 6 → ❌ Blocked (Rate limit exceeded)
```

---

# ✨ Features

✅ Limits API requests per user  
✅ Prevents server overload  
✅ Redis-based request counter  
✅ Configurable rate limits  
✅ Middleware-style request filtering  
✅ HTTP 429 response when limit exceeded  
✅ Scalable backend architecture  

---

# 🛠 Tech Stack

| Technology | Purpose |
|------------|--------|
| **Java** | Core programming language |
| **Spring Boot** | Backend framework |
| **Spring Web** | REST API development |
| **Redis** | In-memory request counter |
| **Maven** | Dependency management |
| **Git & GitHub** | Version control |

---

# 🏗 System Architecture

```text
        User
         |
         v
   Frontend / Postman
         |
         v
   Spring Boot Controller
         |
         v
   Rate Limiter Filter
         |
         v
     Service Layer
  (Business Logic)
         |
         v
       Redis Cache
  (Request Counter Store)
         |
         v
        Response
```

---

# ⚙️ How the System Works

## Step 1: Client sends API request

Example request:

```
GET /api/test
```

---

## Step 2: Rate limiter checks request count

Redis stores the number of requests per user.

Example:

```
User123 → 3 requests
```

---

## Step 3: If request limit not exceeded

```
Limit = 5
Current Requests = 3

→ Request Allowed
```

---

## Step 4: If request limit exceeded

```
Limit = 5
Current Requests = 6

→ Request Blocked
```

Server response:

```
HTTP 429 Too Many Requests
```

---

# 🔄 Request Flow

```text
Client Request
      |
      v
Check Request Count in Redis
      |
      +---- Within Limit → Process Request
      |
      +---- Limit Exceeded → Return 429 Error
```

---

# 🧩 High-Level Architecture Diagram

```text
           +-------------+
           |   User      |
           +-------------+
                  |
                  v
          +----------------+
          |   REST API     |
          |  Spring Boot   |
          +----------------+
                  |
                  v
          +----------------+
          | Rate Limiter   |
          |    Filter      |
          +----------------+
                  |
                  v
           +-------------+
           |   Redis     |
           | Request     |
           | Counter     |
           +-------------+
                  |
                  v
             API Response
```

---

# 📂 Project Structure

```text
api-rate-limiter
│
├── controller
│   ApiController.java
│
├── filter
│   RateLimitFilter.java
│
├── service
│   RateLimiterService.java
│
├── config
│   RedisConfig.java
│
├── util
│   RateLimitAlgorithm.java
│
└── ApiRateLimiterApplication.java
```

---

# 🔌 API Endpoints

## 1️⃣ Test API

```
GET /api/test
```

Response:

```
Request Successful
```

---

## 2️⃣ Rate Limit Exceeded

Response:

```
HTTP 429 Too Many Requests
```

Message:

```
Rate limit exceeded. Try again later.
```

---

# 🚀 How to Run the Project

### 1️⃣ Clone the repository

```
git clone https://github.com/yourusername/api-rate-limiter.git
```

### 2️⃣ Navigate to project directory

```
cd api-rate-limiter
```

### 3️⃣ Start Redis server

```
redis-server
```

### 4️⃣ Configure Redis

Update `application.properties`

```
spring.redis.host=localhost
spring.redis.port=6379
```

### 5️⃣ Run the application

```
mvn spring-boot:run
```

Server runs at:

```
http://localhost:8080
```

---

# 📈 Future Improvements

🔹 Sliding Window Rate Limiting  
🔹 Distributed rate limiting  
🔹 API key based rate limiting  
🔹 Monitoring dashboard  
🔹 Request analytics  
🔹 Dynamic configuration  

---

# 🎯 Learning Outcomes

This project helped me understand:

- API protection mechanisms
- Backend scalability
- Redis caching
- Middleware request filtering
- Real-world system design concepts

---

# 👩‍💻 Author

**Swathi Mittapalli**

📧 Email: mittapalliswathi57@gmail.com  
💻 GitHub: https://github.com/swathi-57  

---

⭐ If you like this project, consider **giving it a star on GitHub!**
