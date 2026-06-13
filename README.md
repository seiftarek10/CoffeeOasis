# ☕ Coffee Oasis — Full-Cycle Realtime Retail & Order Management System

<!-- TECH BADGES -->
<p align="left">
  <img src="https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white" alt="Flutter" />
  <img src="https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black" alt="Firebase" />
  <img src="https://img.shields.io/badge/BLoC%20%2F%20Cubit-0175C2?style=for-the-badge&logo=dart&logoColor=white" alt="BLoC" />
  <img src="https://img.shields.io/badge/Hive%20DB-🔍-green?style=for-the-badge" alt="Hive" />
  <img src="https://img.shields.io/badge/Architecture-Clean-brightgreen?style=for-the-badge" alt="Clean Architecture" />
</p>

> 🚀 A production-ready retail platform focused on high-velocity transaction handling, built using **Clean Architecture** with a deep emphasis on **Reusable Custom Widgets** and native **Firebase Reactive Architecture**.

---

### 🏗️ 📐 Presentation Layer & Reusable Widgets

* **🧩 Atomic Widget Library:** Built a dedicated, encapsulated library of **Custom Form Fields, Adaptive Action Buttons, and State-aware Item Cards**. Every UI component is engineered as a Stateless/Stateful wrapper that accepts generic data models, ensuring the **Presentation Layer** remains pure and strictly decoupled from business logic (**DRY Principle**).
* **🎭 Dynamic Role-Based UI (User ➔ Staff ➔ Owner):** Developed intelligent, reusable order-card widgets that adapt their presentation layout, border styles, and action triggers dynamically based on the active session role.
* **🎨 Centralized Theme Injector:** Enforced complete design consistency across all screens by wrapping reusable components inside a dynamic dark/light theme management system.

---

### ⚡ 🔮 Realtime Core Functions & Multi-Role Sync

#### 1️⃣ 👤 USER FLOW: Local-First Cart Logic (`syncAndCalculateCart`)
* **🧠 The Logic:** Runs a **local-first reduction algorithm** within a fast `Hive Box` to ensure zero UI lag during real-time cart modifications.
* **⚙️ How it works:** Recalculates base price, item extras, and taxes entirely in-memory. It updates the reusable cart widgets instantly, caching the state locally before committing final transaction payloads to **Cloud Firestore** at checkout.

#### 2️⃣ 👤 USER FLOW: Customer Reactive Order Tracking (`streamOrderTrackingStatus`)
* **🧠 The Logic:** Eliminates continuous, resource-heavy HTTP polling requests from the customer side by binding the UI directly to the live database state.
* **⚙️ How it works:** Subscribes the customer directly to a **Firestore Document Stream** of their specific order ID. It maps incoming reactive snapshots into domain-specific `OrderEntities`, updating the UI instantly the exact millisecond the status changes.

---

#### 3️⃣ 👨‍🍳 STAFF FLOW: Live Order Dashboard (`streamStaffActiveOrders`)
* **🧠 The Logic:** Creates an instantaneous, synchronized control panel for restaurant staff to manage incoming queues seamlessly.
* **⚙️ How it works:** 
  1. The function opens a native **Firestore Collection Stream** filtering orders where status equals `pending` or `preparing`.
  2. It updates the Staff UI instantly using **Cubit state emissions** when a new customer completes checkout.
  3. Staff can trigger state updates that modify the Firestore document directly, advancing the order lifecycle dynamically.

---

#### 4️⃣ 👑 OWNER FLOW: Live Operations & Management Sync
* **🧠 The Logic:** Provides top-level state monitoring over all active staff queues and historical transaction snapshots without layout or data leaks.
* **⚙️ How it works:** Aggregates real-time Firestore collections to present business analytics summaries, financial reports, and track active user-to-staff response loops dynamically.

---

### 🛠️ 💻 Tech Stack & Production Patterns

* **📱 Framework:** Flutter (Cross-Platform iOS & Android)
* **📐 Architecture:** Feature-Based Clean Architecture & SOLID Principles
* **🔄 State Management:** Flutter BloC / Cubit (Predictable State Flow)
* **🔥 Backend Ecosystem:** Firebase Authentication & Cloud Firestore Streams
* **💾 Data Persistence:** Hive Local Binary DB (Optimized Cart & Session Caching)
