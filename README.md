# 🏠 RentNow — Business Closure Tracking & Rental Listing System

> **SYSARCH32 Midterm Project** | KALUY-E TEAM | UCLM

![RentNow Banner](https://img.shields.io/badge/RentNow-Business%20Tracker-2d6a4f?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-In%20Development-f4a261?style=for-the-badge)
![SDG](https://img.shields.io/badge/SDG-8%20Decent%20Work%20%26%20Economic%20Growth-blue?style=for-the-badge)

---

## 📌 About the Project

**RentNow** is a web-based system designed to address the lack of a centralized platform for tracking business closures and vacant commercial spaces in local barangay communities.

It connects **property owners**, **local entrepreneurs**, and **LGU administrators** in one platform — making it easier to discover, list, and manage commercial rental spaces.

### 🎯 Problem It Solves
- No centralized system to track business closures in barangays
- Vacant commercial spaces remain unused for long periods
- LGUs lack accurate data on business sustainability
- Entrepreneurs have difficulty finding available rental spaces

---

## 👥 Team Members — KALUY-E TEAM

| Name | Role |
|------|------|
| Marvin Calvez | Team Lead / Project Manager (PM) |
| Kylar Covy Bihag | Solution Architect / Integrator |
| Junnel Montellano | Business Analyst / Research Lead |
| Keir P. Gom-os | Documentation & Pitch |

---

## 🚀 Features (MVP)

- ✅ **Business Registration Module** — Register and track local shops
- ✅ **Closure Tracking Module** — Mark shops as open/closed with reason
- ✅ **Vacancy Listing System** — Property owners can post available rental spaces
- ✅ **Search & Filter Function** — Filter by location, price, and size
- ✅ **Admin Dashboard** — View active vs. closed businesses with reports
- ✅ **User Account Management (CRUD)** — Create, update, delete shop and rental records
- ✅ **Role-based Access** — Admin, Property Owner, Entrepreneur portals

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | HTML5, CSS3, JavaScript (Vanilla) |
| Backend | PHP / Laravel |
| Database | MySQL |
| Version Control | Git & GitHub |

---

## 📁 Project Structure

```
SYSARCH32-MIDTERM-PROJECT/
├── index.html                  # Landing Page / Login
├── src/
│   ├── pages/
│   │   ├── listings.html       # Browse Available Spaces
│   │   ├── admin-dashboard.html    # Admin Panel
│   │   └── owner-dashboard.html    # Property Owner Panel
│   ├── css/
│   └── js/
├── backend/
│   ├── routes/
│   ├── controllers/
│   ├── models/
│   └── migrations/
├── docs/
│   ├── system-diagram.png
│   └── ERD.png
└── README.md
```

---

## 🗄️ Database Schema

```sql
-- Users Table
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    role ENUM('admin', 'owner', 'entrepreneur') DEFAULT 'entrepreneur',
    barangay VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Shops / Businesses Table
CREATE TABLE shops (
    id INT PRIMARY KEY AUTO_INCREMENT,
    owner_id INT REFERENCES users(id),
    name VARCHAR(150) NOT NULL,
    address TEXT,
    business_type VARCHAR(100),
    status ENUM('active', 'closed') DEFAULT 'active',
    closure_reason TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Rental Listings Table
CREATE TABLE listings (
    id INT PRIMARY KEY AUTO_INCREMENT,
    shop_id INT REFERENCES shops(id),
    price DECIMAL(10,2),
    size_sqm INT,
    description TEXT,
    is_available BOOLEAN DEFAULT TRUE,
    contact_number VARCHAR(20),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## ⚙️ Setup Instructions

### Prerequisites
- PHP >= 8.0
- Composer
- MySQL
- Node.js (optional, for assets)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/Nemless13/SYSARCH32---MIDTERM-PROJECT.git
cd SYSARCH32---MIDTERM-PROJECT

# 2. Install Laravel dependencies
composer install

# 3. Copy environment file
cp .env.example .env

# 4. Set your DB credentials in .env
DB_DATABASE=rentnow
DB_USERNAME=root
DB_PASSWORD=

# 5. Generate app key
php artisan key:generate

# 6. Run migrations
php artisan migrate

# 7. Seed test data (optional)
php artisan db:seed

# 8. Serve the application
php artisan serve
```

### 🌐 Open in Browser
```
http://localhost:8000
```

---

## 🔑 Test Credentials

| Role | Email | Password |
|------|-------|----------|
| Admin | admin@rentnow.com | @dminp@ssword |
| Property Owner | maria@rentnow.com | owner1234 |
| Entrepreneur | ana@rentnow.com | user1234 |

---

## 📡 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/listings` | Get all available listings |
| POST | `/api/listings` | Create a new listing |
| GET | `/api/listings/{id}` | Get a specific listing |
| PUT | `/api/listings/{id}` | Update a listing |
| DELETE | `/api/listings/{id}` | Delete a listing |
| GET | `/api/shops` | Get all registered businesses |
| POST | `/api/shops` | Register a new business |
| PATCH | `/api/shops/{id}/status` | Update shop open/closed status |
| POST | `/api/auth/login` | User login |
| POST | `/api/auth/register` | User registration |

---

## 🚫 Out of Scope (for this sprint)

- Online rent payment processing
- AI-based financial forecasting
- Integration with national government tax systems
- Mobile app version

---

## 🌱 SDG Alignment

This project supports **SDG 8 — Decent Work and Economic Growth** by:
- Empowering local entrepreneurs to find commercial spaces
- Helping LGUs monitor business sustainability in their barangays
- Reducing economic disruption caused by untracked business closures

---

## 📸 Screenshots

> Landing Page
![landing page](https://github.com/user-attachments/assets/b5cb5a57-a032-4f94-9b06-6a64e1d19808)
![log in](https://github.com/user-attachments/assets/fe712971-55f0-4fdd-98c2-27e83ee89c14)
![admindashboard](https://github.com/user-attachments/assets/19c1f966-54ce-4dc6-a3f1-2f2509b38148)
![ownerdashboard](https://github.com/user-attachments/assets/d455a920-828d-4ffe-b674-bdb37aa6c27b)
![userdashboard](https://github.com/user-attachments/assets/9cf56094-4035-4e51-8848-a9505b17a986)




---

## 📄 License

This project is for academic purposes only — SYSARCH32 Midterm, 2025.

---
## 👨‍💻 Team Contributions

<!-- Marvin Calvez - Team Lead / PM - Frontend & Full Stack -->
<!-- Kylar Covy Bihag - Solution Architect / Integrator -->
<!-- Junnel R. Montellano - Business Analyst / Research Lead -->
<!-- Kier P. Gom-os - Documentation & Pitch Lead -->

*Built with ❤️ by KALUY-E TEAM — UCLM*
