# 🍦 Bonrecreme

A modern **full-stack** restaurant management application for ordering, kitchen tracking, billing, and reporting—powered by microservices and real-time messaging.

---

## 📋 Table of Contents

- [🍦 Bonrecreme](#-bonrecreme)
   - [📋 Table of Contents](#-table-of-contents)
   - [✨ Features](#-features)
   - [🛠️ Tech Stack Overview](#️-tech-stack-overview)
      - [🎨 Frontend](#-frontend)
      - [⚙️ Backend](#️-backend)
      - [🚀 DevOps (Containerization)](#-devops-containerization)

   - [🚀 Getting Started](#-getting-started)
      - [Prerequisites](#prerequisites)
      - [Installation](#installation)

   - [🔗 Access](#-access)
   - [🖥️ API Endpoints](#️-api-endpoints)
   - [🤝 Contributing](#-contributing)
   - [⚖️ License](#️-license)

---

## ✨ Features

- 📃 **Menu Management**: CRUD operations for menu items
- 🍽️ **Table Management**: Create, update, and delete restaurant tables
- 🧾 **Checkout & Billing**: Generate bills (PDF/CSV) and process payments
- 🥘 **Order Flow**:

   - **Customer** places orders
   - **Kitchen** updates cooking status
   - **Waitstaff** serves ready orders

- 📈 **Reporting**: Monthly reports exported as PDF or Excel
- 🔒 **JWT Authentication** for manager APIs

---

## 🛠️ Tech Stack Overview

### 🎨 Frontend

| Technology                | Role                                                                                                                                               |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Vite**                  | A next-gen frontend build tool offering fast startup, HMR (Hot Module Replacement), and optimized builds ([vitejs.dev](https://vitejs.dev))        |
| **HTML, CSS, JavaScript** | Core web technologies for structure (HTML), styling (CSS), and interactivity (JavaScript) ([developer.mozilla.org](https://developer.mozilla.org)) |
| **Node.js**               | JavaScript runtime environment for server-side and tooling support ([nodejs.org](https://nodejs.org))                                              |

### ⚙️ Backend

| Technology       | Role                                                                                                                                         |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| **Spring Boot**  | Java framework for building robust backends and microservices with embedded servers ([spring.io](https://spring.io/projects/spring-boot))    |
| **PostgreSQL**   | Open-source relational database system for transactional data and complex queries ([postgresql.org](https://www.postgresql.org))             |
| **Redis**        | In-memory data store used for caching and fast data access ([redis.io](https://redis.io))                                                    |
| **Apache Kafka** | Distributed event streaming platform for building real-time data pipelines and streaming apps ([kafka.apache.org](https://kafka.apache.org)) |

### 🚀 DevOps (Containerization)

| Technology         | Role                                                                                                                                            |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Docker**         | Platform to build, share, and run containerized applications ([docker.com](https://www.docker.com))                                             |
| **Docker Compose** | Tool for defining and running multi-container Docker applications with YAML config ([docs.docker.com/compose](https://docs.docker.com/compose)) |
|

---

## 🚀 Getting Started

### Prerequisites

- **Git** ≥ 2.30
- **Docker** & **Docker Compose**
- (Optional) **Postman** or **Hoppscotch** for testing APIs

### Installation

1. **Clone the repo**

```bash
git clone https://github.com/LUX14Zx/pior-test.git
cd pior-test


```

2. **Initialize submodules**

```bash
git submodule update --init --recursive

```

3. **Build & start containers**

```bash
docker compose build
docker compose up

```

---

## 🔗 Access

* **Frontend UI**
   Open your browser at:

   - [http://localhost:4173](http://localhost:4173)

* **Backend API**
   Base URL:

   - [http://localhost:8080/api/v1](http://localhost:8080/api/v1)

---

## 🖥️ API Endpoints

Below is a quick summary of core endpoints:

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

Please follow the [Contributor Covenant](https://www.contributor-covenant.org/) in all contributions.

---

## ⚖️ License

This project is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.

---