# 🛒 E-Commerce Microservices Platform (ECMS)

A backend **E-Commerce Microservices Platform** built using **Spring Boot**, **Spring Cloud**, and **MySQL**, following a clean microservices architecture.
This project is designed for learning, scalability, and real-world backend development.

---

## 📌 Project Overview

This platform is divided into independent microservices that communicate via an **API Gateway**.
Each service has its own responsibility, database configuration, and lifecycle.

### Current Microservices

* **Auth Service** – Authentication & Authorization (JWT based)
* **Product Service** – Product management
* **API Gateway** – Central entry point for all requests

> 🚧 More services (Order, User, Payment, etc.) can be added later.

---

## 🧱 Tech Stack

* **Java 17**
* **Spring Boot**
* **Spring Cloud Gateway**
* **Spring Security + JWT**
* **Spring Data JPA**
* **MySQL**
* **Maven**
* **IntelliJ IDEA**
* **Git & GitHub**

---

## 📂 Project Structure

```
E-Commerce Microservices Platform (ECMS)
│
├── api-gateway
│   ├── src/main/java
│   ├── src/main/resources
│   │   └── application.properties
│   └── pom.xml
│
├── auth-service
│   ├── src/main/java
│   ├── src/main/resources
│   │   └── application.properties
│   └── pom.xml
│
├── product-service
│   ├── src/main/java
│   ├── src/main/resources
│   │   └── application.properties
│   └── pom.xml
│
├── .gitignore
├── README.md
```

---

## 🔐 Auth Service

### Responsibilities

* User login
* JWT token generation
* Authentication validation

### Sample Login API

```
POST /auth/login
```

**Request Body**

```json
{
  "username": "admin",
  "password": "admin123"
}
```

**Response**

```json
{
  "token": "jwt-token-value"
}
```

---

## 📦 Product Service

### Responsibilities

* Product CRUD operations
* Product catalog management

### Example Endpoint

```
GET /products
```

---

## 🌐 API Gateway

### Responsibilities

* Single entry point for clients
* Route requests to microservices
* Centralized configuration

### Example Routes

```properties
spring.cloud.gateway.routes[0].id=auth-service
spring.cloud.gateway.routes[0].uri=http://localhost:8081
spring.cloud.gateway.routes[0].predicates[0]=Path=/auth/**

spring.cloud.gateway.routes[1].id=product-service
spring.cloud.gateway.routes[1].uri=http://localhost:8082
spring.cloud.gateway.routes[1].predicates[0]=Path=/products/**
```

---

## 🗄️ Database Configuration (MySQL)

Each microservice uses its **own database**.

Example (`application.properties`):

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/auth_db
spring.datasource.username=root
spring.datasource.password=your_password

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

---

## ▶️ How to Run the Project

### 1️⃣ Start MySQL

Make sure MySQL is running and databases are created.

### 2️⃣ Start Services (order matters)

```bash
1. auth-service
2. product-service
3. api-gateway
```

Run each service using:

```bash
mvn spring-boot:run
```

or directly from IntelliJ.

---

## 🧪 Testing APIs

* Use **Postman**
* Access APIs via **API Gateway**

Example:

```
http://localhost:8080/auth/login
http://localhost:8080/products
```

---

## 🚀 How to Push Project to GitHub

```bash
git init
git add .
git commit -m "Initial commit - E-Commerce Microservices Platform"
git branch -M main
git remote add origin https://github.com/jatin815645/ecommerce-microservice-platform.git
git push -u origin main
```

---

## 🛑 .gitignore Highlights

* `target/`
* `.idea/`
* `*.iml`
* `*.log`
* Environment-specific config files

---

## 📈 Future Enhancements

* Order Service
* User Service
* Role-based authorization
* Docker & Docker Compose
* Service discovery (Eureka)
* Centralized config server
* CI/CD pipeline

---

## 👨‍💻 Author

**Jitendra Patil**
Junior Android & Backend Developer
Learning Spring Boot Microservices 🚀
