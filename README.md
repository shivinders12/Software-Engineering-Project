# 🔋Software-Engineering-Project UCS503

### On-Demand Battery Delivery, Installation & Buyback Platform

Battify is a web-based platform designed to make battery replacement **fast, reliable, and transparent** by integrating battery discovery, inventory management, delivery, installation, and old-battery buyback into a single workflow.

The platform connects **customers, inventory managers, operations administrators, and delivery/installation agents** through one system.

> Developed as a Software Engineering project for **UCS503P – Software Engineering Lab** at Thapar Institute of Engineering and Technology.

---

## 📌 Problem

Battery failure can be time-sensitive. A failed inverter, tractor, or agricultural pump battery can interrupt household activities or farm operations.

The traditional replacement process is fragmented:

* Finding a suitable battery
* Checking whether it is available nearby
* Arranging transportation
* Getting the battery installed
* Disposing of the old battery
* Tracking the overall process

Battify brings these activities together into a **single software platform**.

---

## 💡 Solution

Battify provides an integrated workflow:

```text
Customer
   ↓
Select Battery
   ↓
Enter Vehicle / Application Details
   ↓
Check Inventory
   ↓
Create Order
   ↓
Assign Delivery Agent
   ↓
Deliver & Install
   ↓
Collect Old Battery
   ↓
Calculate Buyback
   ↓
Complete Order
```

This transforms battery replacement from a simple product purchase into an **end-to-end service workflow**.

---

## ✨ Key Features

### 👤 Customer

* User registration and login
* Browse battery catalogue
* Select battery based on application/vehicle
* Enter battery requirements
* Check availability
* Place replacement orders
* Select delivery location and service slot
* Track order status
* View final price after buyback deduction

### 📦 Inventory Management

* Maintain battery inventory
* Track available and reserved stock
* Update inventory
* Identify low-stock products
* Support inventory reservation during order confirmation

### 🚚 Delivery & Installation

* Assign orders to delivery/installation agents
* Track delivery progress
* Record installation completion
* Maintain order status history

### ♻️ Old Battery Buyback

* Record old battery details
* Calculate estimated buyback value
* Deduct buyback credit from the order amount
* Record old-battery collection for recovery/recycling

### 🖥️ Admin / Operations Dashboard

* Monitor orders
* Manage inventory
* Assign delivery agents
* Monitor unresolved jobs
* Track delivery and installation progress

---

## 🔄 Order Lifecycle

Battify uses a controlled order state machine:

```text
Placed
  ↓
Confirmed
  ↓
Assigned
  ↓
Dispatched
  ↓
Delivered
  ↓
Installed
  ↓
Completed
```

### Exceptional States

```text
Cancelled
Out of Stock
Rescheduled
```

This ensures that invalid order transitions can be prevented and tested systematically.

---

## 🏗️ System Architecture

Battify follows a **three-tier architecture with MVC principles**.

```text
┌─────────────────────────────────────┐
│        Presentation Layer           │
│                                     │
│  Customer UI   Admin UI   Agent UI  │
└──────────────────┬──────────────────┘
                   │
                   ▼
┌─────────────────────────────────────┐
│        Application Layer            │
│                                     │
│ REST APIs + Business Logic          │
│                                     │
│ Authentication                      │
│ Order Management                    │
│ Inventory Management                │
│ Dispatch                            │
│ Buyback                             │
└──────────────────┬──────────────────┘
                   │
                   ▼
┌─────────────────────────────────────┐
│            Data Layer               │
│                                     │
│ Relational Database                 │
│                                     │
│ Users                               │
│ Products                            │
│ Inventory                           │
│ Orders                              │
│ Status History                      │
│ Service Records                     │
└─────────────────────────────────────┘
```

The project uses a **modular monolithic architecture** initially to keep implementation manageable while maintaining clear module boundaries.

---

## 🧩 Core Modules

```text
Battify
│
├── Authentication
│
├── Customer Management
│
├── Battery Catalogue
│
├── Compatibility & Requirements
│
├── Inventory Management
│
├── Order Management
│
├── Pricing & Buyback
│
├── Agent Assignment
│
├── Delivery & Installation
│
├── Order Tracking
│
└── Admin Dashboard
```

---

## 👥 System Actors

| Actor             | Responsibilities                                   |
| ----------------- | -------------------------------------------------- |
| Customer          | Browse batteries, place orders, track service      |
| Delivery Agent    | Deliver and install batteries, collect old battery |
| Inventory Manager | Manage stock and reservations                      |
| Operations Admin  | Manage orders and agent assignments                |
| Battery Supplier  | Supply battery inventory                           |
| Recycling Partner | Receive collected old batteries                    |

---

## 🗄️ Main Entities

The proposed relational data model contains entities such as:

```text
User
Customer
Agent
Battery
InventoryItem
Order
OrderStatusHistory
Installation
Buyback
Payment
ServiceRecord
```

Relationships between these entities will be represented through the project's ER and class diagrams.

---

## 📋 Functional Requirements

Some of the core system requirements are:

* Customers shall be able to browse battery products.
* Customers shall be able to submit replacement requests.
* The system shall check inventory before confirming an order.
* The system shall reserve inventory for confirmed orders.
* The system shall assign an eligible service agent.
* The system shall maintain an auditable order-status history.
* The system shall calculate the final amount after buyback credit.
* Administrators shall be able to update inventory.
* Customers shall be able to track their orders.
* The system shall record completed installations and old-battery collection.

---

## ⚙️ Non-Functional Requirements

### Performance

Core customer operations should respond quickly under expected project-scale load.

### Usability

The customer workflow should require minimal steps and work effectively on mobile devices.

### Reliability

Order and inventory state changes should remain consistent and recoverable.

### Security

Authentication and role-based authorization should protect administrative functionality.

### Maintainability

Backend modules should have clear interfaces and separation of responsibilities.

### Energy Efficiency

The system should avoid unnecessary animations, excessive polling, large payloads, and unnecessary resource consumption.

---

## 🧪 Testing

Testing is planned throughout development rather than only at the end.

### Unit Testing

Examples:

* Buyback-credit calculation
* Total-price calculation
* Inventory availability
* Inventory reservation
* Order-state transitions
* Agent eligibility

### Integration Testing

Examples:

```text
Customer Order
      ↓
Inventory Reservation
      ↓
Agent Assignment
      ↓
Delivery
      ↓
Installation
      ↓
Inventory Update
```

### System Testing

A complete customer journey will be tested:

```text
Battery Selection
       ↓
Order Confirmation
       ↓
Delivery
       ↓
Installation
       ↓
Buyback
       ↓
Order Completion
```

---

## 🌱 Green Software Engineering

Battify incorporates energy-aware software engineering practices such as:

* Lightweight pages
* Optimized images
* Reduced animations
* Pagination
* Indexed database queries
* Caching relatively static catalogue data
* Efficient API payloads
* Event-driven updates where practical
* Reduced unnecessary polling
* Dark-mode support
* Monitoring CPU, memory, and network consumption

These practices will be evaluated as **engineering trade-offs**, rather than being treated only as UI features.

---

## 🚀 Development Roadmap

### Sprint 1 — Requirements & Design

* Stakeholder analysis
* Requirements gathering
* SRS
* UI sketches
* UML modelling

### Sprint 2 — Authentication & Catalogue

* Authentication
* Customer module
* Battery catalogue
* Battery selection

### Sprint 3 — Orders & Inventory

* Order creation
* Inventory management
* Inventory reservation
* Pricing
* Buyback calculation

### Sprint 4 — Delivery & Installation

* Agent management
* Agent assignment
* Delivery workflow
* Installation workflow
* Order tracking

### Sprint 5 — Operations

* Buyback module
* Admin dashboard
* Notifications
* Operational monitoring

### Sprint 6 — Testing & Deployment

* Unit testing
* Integration testing
* System testing
* Debugging
* Green software optimization
* Deployment

---

## 📊 Evaluation Metrics

The system can be evaluated using:

* Successful order submission rate
* API response time
* Inventory consistency during concurrent orders
* Test-case pass percentage
* Order completion rate
* Number of steps required to place an order
* Reduction in unnecessary network requests
* Usability feedback from pilot users

---

## 🔮 Future Enhancements

Potential future extensions include:

* 📱 Dedicated mobile application
* 💬 WhatsApp-based order intake
* 🗺️ Route optimization
* 📈 Seasonal agricultural battery demand forecasting
* 🤖 Automated battery compatibility recommendations
* 🔗 Supplier inventory integration
* 🔔 Predictive battery replacement reminders
* 🌍 Multi-city expansion

These features are outside the initial MVP scope.

---

## 🎯 MVP Scope

The initial implementation focuses on:

```text
✓ Customer Registration / Login
✓ Battery Catalogue
✓ Compatibility & Requirement Form
✓ Inventory Database
✓ Order Creation
✓ Buyback Calculation
✓ Admin Dashboard
✓ Delivery-Agent Assignment
✓ Order Status Timeline
✓ Installation Completion
✓ Unit & Integration Testing
```

Advanced logistics, forecasting, supplier integration, and mobile applications will be considered future extensions.

---

## 📁 Project Structure

A possible repository structure:

```text
Battify/
│
├── frontend/
│   ├── components/
│   ├── pages/
│   ├── services/
│   └── assets/
│
├── backend/
│   ├── controllers/
│   ├── services/
│   ├── models/
│   ├── repositories/
│   ├── routes/
│   └── middleware/
│
├── database/
│   ├── schema/
│   └── migrations/
│
├── tests/
│   ├── unit/
│   ├── integration/
│   └── system/
│
├── docs/
│   ├── SRS/
│   ├── UML/
│   ├── architecture/
│   └── testing/
│
└── README.md
```

> The exact folder structure may change based on the selected technology stack.

---

## 👨‍💻 Team

**Battify Team — CSED**

* Vyomesh Joshi
* Sarika Garg
* Shivinder Singh
* Yatish Goyal

**Course:** UCS503P – Software Engineering Lab
**Institution:** Thapar Institute of Engineering and Technology
**Year:** 2026

---

## 📚 Software Engineering Focus

Battify is designed to demonstrate the complete Software Engineering lifecycle:

```text
Requirements Engineering
        ↓
Stakeholder Analysis
        ↓
SRS
        ↓
UML & System Modelling
        ↓
Architecture & Design
        ↓
Agile Development
        ↓
Implementation
        ↓
Testing & Verification
        ↓
Green Software Optimization
        ↓
Deployment & Evaluation
```

The project aims to demonstrate that Battify is not simply an e-commerce application, but a **multi-actor service management system involving inventory, workflow orchestration, field service, and reverse logistics**.

---

## 📄 Project Proposal

The complete project proposal is available in the repository under:

```text
docs/Project-Proposal.pdf
```

---

## ⭐ Project Status

**Status:** 🚧 In Development

The repository will be updated progressively as each development sprint is completed.

---

## 📜 License

This project is developed for academic purposes as part of the **UCS503P – Software Engineering Lab**.
