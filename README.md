# E-commerce Product Management and Order Processing System

## Overview
This project is a full-stack system for product management and order processing using Django, Node.js, PostgreSQL, and Docker. It includes authentication, notifications, and a complete Docker setup for easy deployment.

---

## Features

### 1. Product Management (Django)
- **Endpoints:**
  -  `POST /api/token/` — Generate Token
  - `POST /api/products/` — Add a new product
  - `GET /api/products/` — List all products
  - `GET /api/products/:id/` — Get a specific product
  - `PUT /api/products/:id/` — Update product details
  - `DELETE /api/products/:id/` — Delete a product
- **Fields:**
  - `id`, `name`, `description`, `price`, `stock_quantity`, `created_at`, `updated_at`
- **Database:** PostgreSQL
- **Authentication:** JWT (JSON Web Token)

### 2. Order Processing (Node.js)
- **Endpoints:**
  - `POST /api/orders/` — Create a new order
  - `GET /api/orders/` — List all orders
  - `GET /api/orders/:id/` — Get a specific order
- **Order Fields:**
  - `id`, `product_id`, `quantity`, `total_price`, `status` (Pending, Shipped, Delivered), `created_at`
- **Stock Check:** Ensure product stock availability before creating an order
- **Database:** PostgreSQL

### 3. Notifications
- **Trigger:** On successful order placement
- **Methods:** Email

### 4. Docker Setup
- **Docker Containers:**
  - Django backend
  - Node.js backend
  - PostgreSQL database
- **docker-compose.yml** provided for easy setup and deployment

---

## Setup Guide

### Prerequisites
Ensure you have the following installed:
- Docker & Docker Compose
- Python 3.10+
- Node.js 18+
- PostgreSQL 14+

### 1. Clone the Repository
```bash
$ git clone <repository_url>
$ cd project_directory
```

### 2. Environment Variables
Create `.env` files for both Django and Node.js services.

#### Django Backend (.env)
```
SECRET_KEY=your_django_secret_key
DATABASE_NAME=your_db_name
DATABASE_USER=your_db_user
DATABASE_PASSWORD=your_db_password
JWT_SECRET=your_jwt_secret
```

#### Node.js Backend (.env)
```
PORT=5000
PRODUCTS_API_URL=http://django_backend:8000/api/products
DATABASE_NAME=your_db_name
DATABASE_USER=your_db_user
DATABASE_PASSWORD=your_db_password
```

### 3. Docker Setup
Build and run containers:
```bash
$ docker-compose up --build
```

### 4. API Access
Access the APIs:
- Django Backend: `http://localhost:8000/api/products`
- Node.js Backend: `http://localhost:5000/api/orders`

### 5. Test JWT Authentication
For Django API, obtain a token:
```bash
$ curl -X POST -d "username=user&password=pass" http://localhost:8000/api/token/
```
Use the token in the `Authorization` header:
```
Authorization: Bearer <your_token>
```

---

## Contributors
- **Developer:** Prince Sachdeva
- **Backend:** Django & Node.js
- **Database:** PostgreSQL
- **Containerization:** Docker

