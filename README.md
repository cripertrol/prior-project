# 🍦 Bonrecreme

A modern **full-stack** restaurant management application for ordering, kitchen tracking, billing, and reporting—powered.

---

## 📋 Table of Contents

- [🍦 Bonrecreme](#-bonrecreme)
  - [📋 Table of Contents](#-table-of-contents)
  - [✨ Features](#-features)
  - [🛠️ Tech Stack Overview](#️-tech-stack-overview)
    - [🎨 Frontend](#-frontend)
    - [⚙️ Backend](#️-backend)
    - [🚀 DevOps](#-devops)
  - [🚀 Getting Started](#-getting-started)
    - [⚡ Prerequisites](#-prerequisites)
    - [📦 Installation](#-installation)
  - [🔗 Access](#-access)
  - [🍽️ App Usage Guide](#️-app-usage-guide)
    - [🚀 1. Initial Setup (Before Open a restaurant)](#-1-initial-setup-before-open-a-restaurant)
    - [👤 2. Manager Setup](#-2-manager-setup)
    - [📊 3. Real-time Reports](#-3-real-time-reports)
    - [🍽️ 4. Customer Ordering](#️-4-customer-ordering)
    - [👨‍🍳 5. Kitchen Station](#-5-kitchen-station)
    - [🧑‍🍽️ 6. Waitstaff Station](#️-6-waitstaff-station)
    - [💳 7. Checkout](#-7-checkout)
    - [🧾 8. Reports \& Export](#-8-reports--export)
  - [🖥️ API Endpoints](#️-api-endpoints)
  - [🤝 Contributing](#-contributing)
  - [⚖️ License](#️-license)

---

## ✨ Features

* 📃 **Menu Management**: CRUD operations for menu items
* 🍽️ **Table Management**: Create, update, and delete restaurant tables
* 🧾 **Checkout & Billing**: Generate bills (PDF/CSV) and process payments
* 🥘 **Order Flow**:

  * **Customer** places orders
  * **Kitchen** updates cooking status
  * **Waitstaff** serves ready orders
* 📈 **Reporting**: Monthly reports exported as PDF or Excel
* 🔒 **JWT Authentication** for manager APIs

---

## 🛠️ Tech Stack Overview

### 🎨 Frontend

| Technology                | Role                                                                                                                     |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| **Vite**                  | A next-gen frontend build tool offering fast startup, HMR, and optimized builds ([vitejs.dev](https://vitejs.dev))       |
| **HTML, CSS, JavaScript** | Core web technologies for structure, styling, and interactivity ([developer.mozilla.org](https://developer.mozilla.org)) |
| **Node.js**               | JavaScript runtime environment for server-side tooling ([nodejs.org](https://nodejs.org))                                |

### ⚙️ Backend

| Technology       | Role                                                                                                                                      |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| **Spring Boot**  | Java framework for building robust backends and microservices with embedded servers ([spring.io](https://spring.io/projects/spring-boot)) |
| **PostgreSQL**   | Open-source relational database system for transactional data ([postgresql.org](https://www.postgresql.org))                              |
| **Redis**        | In-memory data store used for caching and fast data access ([redis.io](https://redis.io))                                                 |
| **Apache Kafka** | Distributed event streaming platform ([kafka.apache.org](https://kafka.apache.org))                                                       |

### 🚀 DevOps

| Technology         | Role                                                                                                                   |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| **Docker**         | Platform to build, share, and run containerized apps ([docker.com](https://www.docker.com))                            |
| **Docker Compose** | Tool for defining and running multi-container Docker apps ([docs.docker.com/compose](https://docs.docker.com/compose)) |

---

## 🚀 Getting Started

### ⚡ Prerequisites

* **Git** ≥ 2.30
* **Docker** & **Docker Compose**
* (Optional) **Postman** or **Hoppscotch** for testing APIs

### 📦 Installation

```bash
git clone https://github.com/LUX14Zx/pior-test.git
cd pior-test

git submodule update --init --recursive

docker-compose build
docker-compose up
```

---

## 🔗 Access

* **Frontend UI**: [http://localhost:4173](http://localhost:4173)
* **Backend API**: [http://localhost:8080/api/v1](http://localhost:8080/api/v1)

---

## 🍽️ App Usage Guide

### 🚀 1. Initial Setup (Before Open a restaurant)

Open the following these pages **in separate tabs**:

* Customer
* Kitchen
* Waitstaff
* Cashier
* Manager

> Open All of them insperate tabs:

### 👤 2. Manager Setup

* Register and login as manager
* Create **menu items** and **tables** first IMPORTANT ⚠️

### 📊 3. Real-time Reports

* View real-time billing under **Manager > Reports** (uses SSE) (⚠️ but you need to open report page don't change a page to another page bill ticket information (from SSE) will be lost 💀)

### 🍽️ 4. Customer Ordering

* Select a table
* Place orders (multiple times possible)

### 👨‍🍳 5. Kitchen Station

* View orders
* Update cooking status

### 🧑‍🍽️ 6. Waitstaff Station

* Serve orders marked as **Ready**

### 💳 7. Checkout

* Cashier generates bill for table
* Customer makes payment

### 🧾 8. Reports & Export

* Payment reflected in real-time
* Export monthly sales as **PDF** or **CSV**

---

## 🖥️ API Endpoints

| Service     | Method | Endpoint                                       | Description                     |
| ----------- | ------ | ---------------------------------------------- | ------------------------------- |
| **Auth**    | POST   | `/auth/register`                               | Manager registration            |
|             | POST   | `/auth/login`                                  | Manager login → returns JWT     |
| **Menu**    | GET    | `/customer/menu`                               | List all menu items (public)    |
|             | POST   | `/manager/menu-items`                          | Create a new menu item          |
|             | PUT    | `/manager/menu-items/{id}`                     | Update menu item                |
|             | DELETE | `/manager/menu-items/{id}`                     | Remove menu item                |
| **Table**   | POST   | `/manager/tables`                              | Create new table                |
|             | PUT    | `/manager/tables/{id}`                         | Update table status/capacity    |
|             | DELETE | `/manager/tables/{id}`                         | Delete a table                  |
| **Order**   | POST   | `/customer/order`                              | Place a new order               |
|             | PUT    | `/kitchen/order/update/{orderId}`              | Update cooking status           |
|             | PUT    | `/waitstaff/order/serve/{orderId}`             | Serve order to customer         |
| **Billing** | POST   | `/cashier/checkout-bill/table/{tableId}`       | Generate bill                   |
|             | GET    | `/cashier/checkout-bill/image/table/{tableId}` | Retrieve bill image             |
|             | POST   | `/cashier/pay/bill/{billId}`                   | Process payment                 |
| **Reports** | GET    | `/manager/reports/excel?year={y}&month={m}`    | Download monthly report (Excel) |
|             | GET    | `/manager/reports/pdf?year={y}&month={m}`      | Download monthly report (PDF)   |

---

## 🤝 Contributing

1. Fork the project
2. Create a new branch (`git checkout -b feature/YourFeature`)
3. Commit your changes (`git commit -m "Add awesome feature"`)
4. Push to the branch (`git push origin feature/YourFeature`)
5. Open a Pull Request

Follow the [Contributor Covenant](https://www.contributor-covenant.org/) in all contributions.

---

## ⚖️ License

This project is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.

---
