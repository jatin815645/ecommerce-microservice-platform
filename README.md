# 🛒 E-Commerce Microservices Platform

A backend **E-Commerce Microservices Platform** built using **Spring Boot**, **Spring Cloud Gateway**, **JWT-based authentication**, and **MySQL**, following **industry-standard microservice architecture**.

---

## 📌 Architecture Overview

This project consists of **3 independent microservices**:

```
Client (Postman / Android App)
        |
        v
   API Gateway (8080)
        |
        |-- Auth Service (8081)
        |-- Product Service (8082)
```

Each service runs independently and communicates via **HTTP REST APIs**.

---

## 🧩 Microservices

### 🔐 Auth Service

* User Registration
* User Login
* JWT Token Generation
* Role-based access support (`USER`, `ADMIN`)

**Port:** `8081`

---

### 📦 Product Service

* Create Product (ADMIN)
* Update Product (ADMIN)
* Delete Product (ADMIN)
* View Products (USER / ADMIN)
* Pagination support

**Port:** `8082`

---

### 🌐 API Gateway

* Central entry point for all requests
* Routes requests to appropriate microservices
* JWT validation at gateway level
* Secures all routes except `/auth/**`

**Port:** `8080`

---

## 🔐 Security

* **JWT Authentication**
* Token contains:

  * `username`
  * `role`
* Role-Based Access Control (RBAC) enforced in Product Service
* Stateless authentication (no sessions)

---

## 🛠 Tech Stack

* **Java 17**
* **Spring Boot 3.x**
* **Spring Security**
* **Spring Cloud Gateway (WebFlux)**
* **JWT (io.jsonwebtoken)**
* **MySQL**
* **Maven**
* **IntelliJ IDEA**

---

## 🗂 Project Structure

```
E-Commerce-Microservices-Platform/
│
├── api-gateway/
│
├── auth-service/
│
├── product-service/
│
├── .gitignore
├── README.md
```

Each microservice is a **separate Spring Boot project**.

---

## ⚙️ Configuration

Each service uses `application.properties`.

Example (Auth Service):

```properties
server.port=8081
spring.datasource.url=jdbc:mysql://localhost:3306/auth_db
spring.datasource.username=root
spring.datasource.password=your_password

jwt.secret=my-strong-secret-key
jwt.expiration=86400000
```

---

## 🚀 How to Run Locally

### 1️⃣ Start MySQL

Create required databases:

```sql
CREATE DATABASE auth_db;
CREATE DATABASE product_db;
```

---

### 2️⃣ Run Services (in order)

```bash
# Auth Service
cd auth-service
mvn spring-boot:run

# Product Service
cd product-service
mvn spring-boot:run

# API Gateway
cd api-gateway
mvn spring-boot:run
```

---

## 🔍 API Testing (Postman)

### 🔑 Register User

```
POST http://localhost:8080/auth/register
```

### 🔑 Login

```
POST http://localhost:8080/auth/login
```

➡️ Copy the JWT token from response.

---

### 📦 Product APIs (via Gateway)

```
GET    /products
POST   /products        (ADMIN only)
PUT    /products/{id}   (ADMIN only)
DELETE /products/{id}   (ADMIN only)
```

Add header:

```
Authorization: Bearer <JWT_TOKEN>
```

---

## 🧠 Future Enhancements

* Android App (Jetpack Compose)
* Docker & Docker Compose
* Service Discovery (Eureka)
* Centralized Config Server
* Refresh Tokens
* CI/CD pipeline

---

## 👨‍💻 Author

**Jitendra Patil**
Backend & Android Developer
