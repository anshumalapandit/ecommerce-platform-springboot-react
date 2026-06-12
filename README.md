# 🛒 E-Commerce Platform

<div align="center">
  
  [![Spring Boot](https://img.shields.io/badge/Spring%20Boot-4.0.6-brightgreen?style=flat-square&logo=springboot)](https://spring.io/projects/spring-boot)
  [![React](https://img.shields.io/badge/React-19.2.6-blue?style=flat-square&logo=react)](https://react.dev)
  [![Java](https://img.shields.io/badge/Java-17-orange?style=flat-square&logo=java)](https://www.oracle.com/java/)
  [![PostgreSQL](https://img.shields.io/badge/PostgreSQL-13+-336791?style=flat-square&logo=postgresql)](https://www.postgresql.org/)
  [![Stripe](https://img.shields.io/badge/Payment%20Gateway-Stripe-1F425F?style=flat-square&logo=stripe)](https://stripe.com)
  [![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

  <h3>Full-Stack E-Commerce Platform with Multi-Role Architecture</h3>
  <p>
    <strong>Spring Boot 4.0.6 | React 19.2.6 | PostgreSQL | JWT Authentication</strong><br>
    RBAC • Secure Payments • RESTful APIs • Microservices-Ready
  </p>

  [🎯 Features](#-features) • [🏗️ Architecture](#-system-architecture) • [⚙️ Setup](#-installation--setup) • [📚 API](#-api-endpoints) • [🔐 Security](#-security-features)

</div>

---

## 📋 Quick Navigation

- [Overview](#overview)
- [✨ Features](#-features)
- [🏗️ System Architecture](#-system-architecture)
- [⚙️ Installation & Setup](#-installation--setup)
- [📚 API Endpoints](#-api-endpoints)
- [🔐 Security Features](#-security-features)
- [🌐 Running the Application](#-running-the-application)
- [🚀 Deployment](#-deployment)
- [📄 License](#-license)
- [👤 Author](#-author)

---

## Overview

A production-ready e-commerce platform built with **Spring Boot 4.0.6** backend and **React 19.2.6** frontend. Implements enterprise patterns: JWT authentication, RBAC, RESTful APIs, and Stripe payment integration.

### Key Capabilities
- **Multi-Role System**: Customer, Seller, and Admin with distinct workflows
- **Secure Architecture**: JWT-based authentication with role-based access control
- **Payment Integration**: Stripe payment gateway with order reconciliation
- **Scalable Design**: Service-oriented architecture ready for microservices
- **Database**: PostgreSQL (production), H2 (development/testing)

---

## ✨ Features

### Core Functionality
- **User Management**: Registration, authentication, profile management
- **Product Catalog**: Browse, search, filter by category and price
- **Shopping Cart**: Add/remove items, quantity management, persistence
- **Checkout Flow**: Multi-step checkout with address management
- **Order Management**: Order placement, status tracking, order history
- **Payment Processing**: Stripe integration for secure transactions
- **Admin Dashboard**: Analytics, user/seller/product management
- **Seller Portal**: Product management, inventory, sales analytics

### Technical Features
- **JWT Authentication**: Stateless, token-based security
- **RBAC**: Three roles (Customer, Seller, Admin)
- **RESTful APIs**: Standardized endpoints with proper HTTP methods
- **Input Validation**: Server-side validation on all requests
- **Error Handling**: Centralized exception handling with proper responses
- **CORS Security**: Configured for secure cross-origin requests

---

## 🏗️ System Architecture

### Architecture Layers

```
Frontend (React 19.2.6)
    ↓ (REST API via Axios)
Spring Security Filter Chain
    ↓
REST Controllers (7 modules)
    ↓
Service Layer (Business Logic)
    ↓
Data Access Layer (JPA Repositories)
    ↓
PostgreSQL Database
```

### Core Modules
| Module | Responsibility |
|--------|-----------------|
| **AuthController** | User registration, login, JWT token management |
| **ProductController** | Product CRUD, search, filtering, image uploads |
| **CartController** | Shopping cart operations (add, remove, update) |
| **OrderController** | Order creation, status updates, tracking |
| **CategoryController** | Category management and classification |
| **AddressController** | User address management for checkout |
| **AnalyticsController** | Dashboard metrics and business analytics |

### Technology Stack
- **Backend**: Java 17, Spring Boot 4.0.6, Spring Security, JPA/Hibernate
- **Frontend**: React 19.2.6, Redux, React Router, TailwindCSS, Material-UI
- **Database**: PostgreSQL (prod), H2 (dev)
- **Authentication**: JWT (JJWT library)
- **Payments**: Stripe API
- **Build**: Maven (backend), Vite (frontend)

---

## ⚙️ Installation & Setup

### Prerequisites

#### Backend Requirements
- Java Development Kit (JDK) 17+
- Maven 3.6.0+
- PostgreSQL 13+ (production)
- Git

#### Frontend Requirements
- Node.js 18.0.0+
- npm 9.0.0+ or yarn
- Git

### Quick Start

#### 1. Clone Repository
```bash
git clone https://github.com/yourusername/ecom-platform.git
cd ecom-platform
```

#### 2. Backend Setup
```bash
cd my-cart

# Install dependencies
mvn clean install

# Build project
mvn clean package -DskipTests
```

#### 3. Frontend Setup
```bash
cd ../ecom-frontend

# Install dependencies
npm install
```

#### 4. Configure Environment

**Backend** - Create `application.properties`:
```properties
server.port=8080
server.servlet.context-path=/api

# Database
spring.datasource.url=jdbc:postgresql://localhost:5432/ecommerce_db
spring.datasource.username=postgres
spring.datasource.password=your_password
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect

# JWT Configuration
app.jwtSecret=your_secret_key_minimum_32_characters_required
app.jwtExpirationInMs=3600000

# CORS
app.cors.allowedOrigins=http://localhost:5173,http://localhost:3000
```

**Frontend** - Create `.env`:
```env
VITE_BACK_END_URL=http://localhost:8080
VITE_API_TIMEOUT=30000
```

---

## 📚 API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/auth/register` | POST | User registration |
| `/api/auth/login` | POST | User authentication |
| `/api/auth/logout` | POST | User logout |
| `/api/products` | GET | Get all products (paginated) |
| `/api/products/{id}` | GET | Get product details |
| `/api/products` | POST | Create product (SELLER/ADMIN) |
| `/api/products/{id}` | PUT | Update product (SELLER/ADMIN) |
| `/api/products/{id}` | DELETE | Delete product (SELLER/ADMIN) |
| `/api/cart` | GET | Get user's cart |
| `/api/cart/add` | POST | Add item to cart |
| `/api/cart/remove/{itemId}` | DELETE | Remove item from cart |
| `/api/cart/clear` | DELETE | Clear cart |
| `/api/orders` | POST | Create order |
| `/api/orders` | GET | Get user's orders |
| `/api/orders/{id}` | GET | Get order details |
| `/api/orders/{id}/status` | PUT | Update order status (ADMIN) |
| `/api/categories` | GET | Get all categories |
| `/api/categories` | POST | Create category (ADMIN) |
| `/api/addresses` | GET | Get user's addresses |
| `/api/addresses` | POST | Add new address |
| `/api/analytics/dashboard` | GET | Dashboard analytics (ADMIN) |

**Query Parameters Example:**
```
/api/products?page=0&pageSize=10&sortBy=price&sortOrder=asc&category=1
```

---

## 🔐 Security Features

### Authentication & Authorization
| Feature | Details |
|---------|---------|
| **JWT Authentication** | Stateless token-based authentication using JJWT |
| **Password Encryption** | BCryptPasswordEncoder with strength 12 |
| **RBAC** | Three roles: CUSTOMER, SELLER, ADMIN |
| **Token Expiration** | 1 hour access token, 7 days refresh token |
| **CORS Configuration** | Restricted cross-origin requests from whitelisted origins |
| **Request Validation** | Server-side validation on all endpoints |
| **Input Sanitization** | Protection against XSS and injection attacks |
| **Global Exception Handling** | Centralized error handling with appropriate HTTP status codes |

### Security Implementation
```java
@Configuration
public class SecurityConfig {
    @Bean
    public PasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder(12);
    }
}

@PreAuthorize("hasRole('ADMIN')")
@PostMapping("/categories")
public ResponseEntity<?> createCategory(...) {
    // Only admins can access
}

@PreAuthorize("isAuthenticated()")
@PostMapping("/cart/add")
public ResponseEntity<?> addToCart(...) {
    // Authenticated users only
}
```

---

## 🌐 Running the Application

### Development Mode

#### Backend
```bash
cd my-cart
mvn spring-boot:run
# Available at: http://localhost:8080/api
```

#### Frontend
```bash
cd ecom-frontend
npm run dev
# Available at: http://localhost:5173
```

### Production Build

#### Backend
```bash
cd my-cart
mvn clean package -DskipTests
java -jar target/my-cart-0.0.1-SNAPSHOT.jar
```

#### Frontend
```bash
cd ecom-frontend
npm run build
npm run preview
```

---

## 🚀 Deployment

### AWS Elastic Beanstalk

#### 1. Prepare Backend
```bash
cd my-cart
mvn clean package -DskipTests
```

#### 2. Configure EB
```bash
pip install awsebcli
eb init -p "Java 17 running on 64bit Amazon Linux 2" my-cart-app
eb create production-env
```

#### 3. Set Environment Variables
```bash
eb setenv \
  DB_URL=jdbc:postgresql://your-rds-endpoint:5432/ecommerce \
  DB_USERNAME=postgres \
  JWT_SECRET=your_production_secret
```

#### 4. Deploy
```bash
eb deploy
eb logs -f
```

### Amazon RDS Setup
```bash
aws rds create-db-instance \
  --db-instance-identifier ecommerce-db \
  --db-instance-class db.t3.micro \
  --engine postgres \
  --master-username postgres \
  --allocated-storage 20
```

### CloudFront + S3 (Frontend)
```bash
cd ecom-frontend
npm run build

aws s3 mb s3://ecom-platform-frontend
aws s3 sync dist/ s3://ecom-platform-frontend --delete

# Create CloudFront distribution with S3 origin
# Set index.html as default root object
```

---

## 🤝 Contributing

We welcome contributions from the community! Here's how you can help:

### Steps
1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/amazing-feature`
3. **Commit** changes: `git commit -m "Add feature"`
4. **Push** to fork: `git push origin feature/amazing-feature`
5. **Open** a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** - see [LICENSE](LICENSE) file for details.

**Permissions:**
- ✅ Commercial use
- ✅ Modification
- ✅ Distribution
- ✅ Private use

---

## 👤 Author

### Anshumala

**Full Stack Developer | Spring Boot | React.js | AWS**

- 💼 [LinkedIn](https://linkedin.com/in/anshumala)
- 🐙 [GitHub](https://github.com/anshumalapandit)
- 📧 Email: anshumalapandit@gmail.com

---

## 🙏 Acknowledgments

- **Spring Boot Team** for the excellent framework
- **React Community** for amazing libraries and tools
- **Stripe** for secure payment processing
- **PostgreSQL** for reliable database
- **AWS** for cloud infrastructure

---

<div align="center">

### 🌟 If you found this project helpful, please consider giving it a star!

[⭐ Star this Repository](https://github.com/yourusername/ecom-platform)

---

<p>Made with ❤️ by <a href="https://github.com/anshumala">Anshumala</a></p>

<p>
  <sub>
    <strong>Version:</strong> 1.0.0 | <strong>Status:</strong> Active Development
  </sub>
</p>

</div>
