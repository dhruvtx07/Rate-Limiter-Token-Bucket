# Rate-Limiter-Token-Bucket
Rate-Limiter-Token-Bucket using spring boot - java


Spring Boot Rate Limiter (Token Bucket + Redis + Docker)

A scalable Rate Limiting system built using Java Spring Boot, implementing the Token Bucket Algorithm, with Redis for distributed storage, and fully containerized using Docker.

📌 Features
⚡ Token Bucket Rate Limiting Algorithm
🔥 Spring Boot REST API backend
🧠 Redis-based distributed rate limiting
🚫 Prevents API abuse & traffic spikes
👤 Per user / IP based rate limiting
⚙️ Configurable capacity & refill rate

🏗️ System Architecture
Client Request
      ↓
Spring Boot API
      ↓
Rate Limiting Filter (Token Bucket)
      ↓
Redis (Stores token state per user/IP)
      ↓
Allow / Block Response (200 / 429)
🧠 Rate Limiting Algorithm (Token Bucket)
Each user/IP has a bucket of tokens
Tokens refill at a fixed rate
Each request consumes 1 token
If no tokens → request is rejected


🛠️ Tech Stack
Java 17+
Spring Boot
Spring Web
Spring Data Redis
Redis
Gradle

⚙️ Configuration
application.properties
server:
  port: 8080

spring:
  redis:
    host: redis
    port: 6379

rate-limiter:
  capacity: 10
  refill-rate: 1   # tokens per second


🚀 How It Works
Request hits Spring Boot API
Filter intercepts request
Redis checks token bucket for user/IP
Token logic applied:
Token available → request allowed
No tokens → request blocked
Response returned
📡 API Example
🔹 Test Endpoint
GET /gateway/rate-limit/status
✅ Success Response -- allowed 200 OK
❌ Rate Limit Exceeded -- not allowed 429 too many request
