# spring-boot-redis-cache

A backend-focused Spring Boot application demonstrating how to integrate **Redis** as a caching layer using Spring’s `@Cacheable`, `@CachePut`, and `@CacheEvict` annotations — all backed by real integration tests with **Testcontainers**.

---

## ⚙️ How It Works

This project showcases Redis-backed caching for a simple product inventory system. It reduces redundant database hits and improves response time using Spring Boot's caching abstraction.

---

## 🔄 Request Flow

- ✅ `GET /api/product/{id}`  
  - First call → retrieves product from database and caches it  
  - Next calls → served directly from Redis  

- 🆕 `POST /api/product`  
  - Adds new product and populates cache with response  

- ✏️ `PUT /api/product`  
  - Updates the product in DB and **refreshes the cache**  

- ❌ `DELETE /api/product/{id}`  
  - Deletes product from DB and **evicts the cache entry**

---

## 🧰 Tech Stack

| Layer     | Tools / Libraries                                                                 |
|-----------|-----------------------------------------------------------------------------------|
| Backend   | Spring Boot, Spring Web, Spring Data JPA, Spring Cache                            |
| Caching   | Redis (via Lettuce), Spring Cache Abstraction                                     |
| DB        | PostgreSQL (Testcontainers)                                                       |
| Testing   | JUnit 5, MockMvc, Testcontainers, Mockito (`@SpyBean` for DB interaction testing) |
| Build     | Maven                                                                             |
| DevOps    | Docker Compose (optional)                                                         |

