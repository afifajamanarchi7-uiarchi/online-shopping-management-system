# 🛒 Online Shopping Management System

<div align="center">

![Project Status](https://img.shields.io/badge/Status-In%20Development-blue?style=for-the-badge)
![Duration](https://img.shields.io/badge/Duration-11%20Weeks-orange?style=for-the-badge)
![Type](https://img.shields.io/badge/Type-Academic%20Project-green?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-purple?style=for-the-badge)

A full-stack web application for managing online shopping — products, cart, orders, and payments — with a dedicated admin dashboard.

</div>

---

## 📋 Table of Contents

- [Project Overview](#-project-overview)
- [Features](#-features)
- [System Architecture](#-system-architecture)
- [Database Design](#-database-design)
- [Tech Stack](#-tech-stack)
- [Project Roadmap](#-project-roadmap-11-weeks)
- [Installation & Setup](#-installation--setup)
- [Folder Structure](#-folder-structure)
- [API / Module Overview](#-module-overview)
- [Testing](#-testing)
- [Deliverables](#-deliverables)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🌐 Project Overview

The **Online Shopping Management System** is a complete e-commerce platform developed as an 11-week academic project. It provides two distinct user experiences:

- **Customers** — Register, browse products by category, search and filter, manage a shopping cart, place orders, and track payment status.
- **Administrators** — Manage users, products, categories, orders, and generate sales reports from a dedicated dashboard.

> **Problem Statement:** Manual retail management is error-prone, slow, and not scalable. This system automates the complete shopping lifecycle — from product discovery to order fulfillment — in a secure, maintainable web application.

---

## ✨ Features

| Module | Features |
|---|---|
| 🔐 **Authentication** | Registration, Login, bcrypt password hashing, Session management, Role-based access |
| 📦 **Products** | Add / Edit / Delete products, Image upload, Stock tracking, Pagination |
| 🗂️ **Categories** | Hierarchical categories, Category browse, Parent-child relationships |
| 🔍 **Search & Filter** | Full-text search, Filter by price/rating/category, Sort options |
| 🛒 **Shopping Cart** | Add/Remove/Update items, Stock validation, Persistent cart, Order summary |
| 📋 **Orders** | Checkout flow, Order history, Status tracking (Pending → Delivered), Stock deduction |
| 💳 **Payments** | Cash on Delivery, Payment records, Receipt/invoice generation |
| 🖥️ **Admin Dashboard** | User management, Product management, Order management, Sales reports |

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────┐
│                    CLIENT LAYER                      │
│          Browser (HTML + CSS + JavaScript)           │
└────────────────────┬────────────────────────────────┘
                     │  HTTP Requests
┌────────────────────▼────────────────────────────────┐
│                  WEB SERVER (Apache / Nginx)         │
│                                                      │
│  ┌─────────────────────────────────────────────┐    │
│  │           APPLICATION LAYER (MVC)           │    │
│  │  ┌──────────┐ ┌──────────┐ ┌─────────────┐ │    │
│  │  │Controllers│ │  Models  │ │    Views    │ │    │
│  │  └──────────┘ └──────────┘ └─────────────┘ │    │
│  └─────────────────────────────────────────────┘    │
└────────────────────┬────────────────────────────────┘
                     │  SQL Queries
┌────────────────────▼────────────────────────────────┐
│              DATABASE LAYER (MySQL)                  │
│   Users │ Products │ Orders │ Payments │ Cart ...    │
└─────────────────────────────────────────────────────┘
```

---

## 🗄️ Database Design

The system uses **8 relational tables** normalized to **3NF**:

```
USERS ──────────────────────────────────────────┐
  │ 1                                            │ 1
  │ M                                            │ M
ORDERS ──── 1 ──── ORDER_ITEMS ──── M ──── PRODUCTS ──── M ──── CATEGORIES
  │ 1                                            │ 1
  │ 1                                            │ M
PAYMENTS                                        CART

USERS ──── 1:M ──── SESSIONS
```

### Key Tables

| Table | Primary Key | Foreign Keys |
|---|---|---|
| `users` | `user_id` | — |
| `categories` | `category_id` | `parent_category_id → categories` |
| `products` | `product_id` | `category_id → categories` |
| `cart` | `cart_id` | `user_id → users`, `product_id → products` |
| `orders` | `order_id` | `user_id → users` |
| `order_items` | `item_id` | `order_id → orders`, `product_id → products` |
| `payments` | `payment_id` | `order_id → orders` |
| `sessions` | `session_id` | `user_id → users` |

> 📄 Full ER Diagram: see `docs/er_diagram.tex` (compile with LaTeX) or `docs/er_diagram.pdf`

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | HTML5, CSS3, Bootstrap 5, JavaScript |
| **Backend** | PHP 8.x / Python (Flask) |
| **Database** | MySQL 8.x |
| **Server** | Apache / XAMPP (local), Nginx (production) |
| **Version Control** | Git + GitHub |
| **Documentation** | LaTeX (ER Diagram, Roadmap), Markdown |

---

## 📅 Project Roadmap (11 Weeks)

```
Week  1  ████░░░░░░░░░░░░░░░░░░░░░░░░  Planning & Requirements
Week  2  ████████░░░░░░░░░░░░░░░░░░░░  System Design
Week  3  ████████████░░░░░░░░░░░░░░░░  Database Development
Week  4  ████████████████░░░░░░░░░░░░  User Authentication
Week  5  ████████████████████░░░░░░░░  Product Management
Week  6  ████████████████████████░░░░  Category & Search
Week  7  ██████████████████████████░░  Shopping Cart
Week  8  █████████████████████████████ Order Management
Week  9  █████████████████████████████ Payment Module
Week 10  █████████████████████████████ Admin Dashboard
Week 11  █████████████████████████████ Testing & Documentation
```

### Weekly Deliverables Summary

| Week | Phase | Key Deliverable |
|---|---|---|
| 1 | Planning | Project Proposal, Use Case Diagram |
| 2 | Design | ER Diagram, Wireframes, Architecture |
| 3 | Database | SQL Scripts, Seed Data |
| 4 | Auth | Registration & Login System |
| 5 | Products | Product CRUD Interface |
| 6 | Search | Search & Filter Features |
| 7 | Cart | Shopping Cart System |
| 8 | Orders | Order Processing System |
| 9 | Payments | Payment Management System |
| 10 | Admin | Admin Panel & Reports |
| 11 | QA | Final Report, Slides, Submission |

---

## ⚙️ Installation & Setup

### Prerequisites

- PHP 8.x or Python 3.10+
- MySQL 8.x
- XAMPP / WAMP (local development) or Docker
- Composer (for PHP) / pip (for Python)
- Git

### 1. Clone the Repository

```bash
git clone https://github.com/<your-username>/online-shopping-management.git
cd online-shopping-management
```

### 2. Database Setup

```bash
# Open MySQL CLI or use phpMyAdmin
mysql -u root -p

# Inside MySQL:
CREATE DATABASE online_shopping_db;
USE online_shopping_db;

# Import the schema and seed data
SOURCE database/schema.sql;
SOURCE database/seed_data.sql;
```

### 3. Configure Environment

```bash
# Copy example config
cp config/config.example.php config/config.php

# Edit database credentials
nano config/config.php
```

```php
<?php
define('DB_HOST', 'localhost');
define('DB_NAME', 'online_shopping_db');
define('DB_USER', 'root');
define('DB_PASS', 'your_password');
define('BASE_URL', 'http://localhost/online-shopping-management');
define('SECRET_KEY', 'your_secret_key_here');
?>
```

### 4. Start the Server

```bash
# Using PHP built-in server
php -S localhost:8000

# Or place in XAMPP htdocs/ and access:
# http://localhost/online-shopping-management
```

### 5. Default Admin Credentials

```
URL:      http://localhost:8000/admin
Email:    admin@shop.com
Password: Admin@1234
```

> ⚠️ **Change the default password immediately after first login.**

---

## 📁 Folder Structure

```
online-shopping-management/
│
├── 📁 config/
│   ├── config.php              # Database & app configuration
│   └── config.example.php      # Template (commit this, not config.php)
│
├── 📁 database/
│   ├── schema.sql              # DDL: CREATE TABLE statements
│   ├── seed_data.sql           # DML: Sample/test data
│   └── migrations/             # Future schema changes
│
├── 📁 modules/
│   ├── auth/                   # Registration, Login, Sessions
│   ├── products/               # Product CRUD
│   ├── categories/             # Category management
│   ├── cart/                   # Cart operations
│   ├── orders/                 # Order processing
│   ├── payments/               # Payment handling
│   └── admin/                  # Admin dashboard
│
├── 📁 public/
│   ├── index.php               # Entry point
│   ├── css/                    # Stylesheets
│   ├── js/                     # JavaScript files
│   └── uploads/                # Uploaded product images
│
├── 📁 views/
│   ├── layouts/                # Base templates (header, footer)
│   ├── auth/                   # Login, register pages
│   ├── products/               # Product listing, detail
│   ├── cart/                   # Cart page
│   ├── orders/                 # Order history, tracking
│   ├── payments/               # Checkout, receipt
│   └── admin/                  # Admin pages
│
├── 📁 includes/
│   ├── db.php                  # Database connection
│   ├── auth_middleware.php     # Session / access control
│   └── helpers.php             # Utility functions
│
├── 📁 docs/
│   ├── er_diagram.tex          # LaTeX ER Diagram source
│   ├── project_roadmap.tex     # LaTeX Roadmap source
│   ├── er_diagram.pdf          # Compiled ER Diagram
│   ├── wireframes/             # UI wireframe images
│   └── use_case_diagram.png    # UML Use Case Diagram
│
├── 📁 tests/
│   ├── unit/                   # Unit tests
│   ├── integration/            # Integration tests
│   └── test_cases.xlsx         # Manual test case document
│
├── .gitignore
├── README.md                   # This file
└── LICENSE
```

---

## 📦 Module Overview

### 🔐 Authentication Module

```
POST /auth/register    → Register new user
POST /auth/login       → Authenticate & create session
GET  /auth/logout      → Destroy session
POST /auth/reset       → Password reset request
```

### 📦 Product Module

```
GET    /products           → List all products (paginated)
GET    /products/{id}      → Product detail page
POST   /admin/products     → Create product (admin)
PUT    /admin/products/{id}→ Update product (admin)
DELETE /admin/products/{id}→ Soft delete (admin)
```

### 🛒 Cart Module

```
GET    /cart              → View cart
POST   /cart/add          → Add item to cart
PUT    /cart/update/{id}  → Update quantity
DELETE /cart/remove/{id}  → Remove item
```

### 📋 Order Module

```
POST /orders/checkout     → Place order from cart
GET  /orders              → User's order history
GET  /orders/{id}         → Order detail & tracking
```

---

## 🧪 Testing

### Run Tests

```bash
# Unit tests (PHPUnit)
./vendor/bin/phpunit tests/unit/

# Integration tests
./vendor/bin/phpunit tests/integration/

# All tests with coverage
./vendor/bin/phpunit --coverage-html reports/coverage
```

### Test Coverage Targets

| Module | Target Coverage |
|---|---|
| Authentication | ≥ 90% |
| Cart Logic | ≥ 85% |
| Order Processing | ≥ 85% |
| Payment Records | ≥ 80% |
| Admin Reports | ≥ 75% |

---

## 📚 Deliverables

- [x] Project Proposal
- [x] Requirement Specification Document
- [x] Use Case Diagram
- [x] ER Diagram (`docs/er_diagram.tex`)
- [x] Database Schema (`database/schema.sql`)
- [x] Project Roadmap (`docs/project_roadmap.tex`)
- [ ] User Authentication Module
- [ ] Product Management Module
- [ ] Category & Search Module
- [ ] Shopping Cart Module
- [ ] Order Management Module
- [ ] Payment Module
- [ ] Admin Dashboard
- [ ] Final Report
- [ ] Presentation Slides
- [ ] Test Case Document

---

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/cart-module`
3. Commit your changes: `git commit -m "Add cart quantity update feature"`
4. Push to the branch: `git push origin feature/cart-module`
5. Open a Pull Request

### Commit Convention

```
feat:     New feature
fix:      Bug fix
docs:     Documentation changes
db:       Database schema changes
test:     Adding or updating tests
refactor: Code restructuring (no feature change)
```

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Online Shopping Management System** · 11-Week Academic Project · Version 1.0

Made with ❤️ for learning full-stack web development

</div>
