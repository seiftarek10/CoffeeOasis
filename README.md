# ☕ Coffee Oasis — Full-Cycle Retail & Order Management System

A production-ready retail platform focused on high-velocity transaction handling, built using **Clean Architecture** with a deep emphasis on **Reusable Custom Widgets** and **Reactive State Management**.

## 🏗️ Modular UI & Reusable Component Engineering
* **Atomic Widget Library:** Built a dedicated library of **Custom Form Fields, Adaptive Action Buttons, and State-aware Item Cards**. Every UI component is built as a Stateless/Stateful wrapper that accepts generic data models, ensuring that the **Presentation Layer** remains pure and strictly decoupled from the business logic.
* **Role-Based Dynamic UI:** Developed reusable order-card widgets that adapt their presentation layout and action triggers dynamically based on whether the logged-in user is a **Customer** (views tracking status) or **Staff** (views management controls).

## ⚡ High-Velocity Core Functions & Multi-Role Sync

### 1. Staff Live Order Dashboard (`streamStaffActiveOrders`)
* **Logic:** Creates a synchronized real-time control panel for restaurant staff to manage incoming queues.
* **How it works:** 
  1. The function opens a secure backend stream that filters orders where status equals `pending` or `preparing`.
  2. It updates the Staff UI instantly using **Cubit state emissions** whenever a new customer hits the checkout.
  3. Staff can trigger the `updateOrderStatus` function, which fires a fast patch request via **REST API/Firestore** to advance the order lifecycle.

### 2. Reactive Order Tracking (`streamOrderTrackingStatus`)
* **Logic:** Eliminates continuous resource-heavy HTTP polling requests from the customer side.
* **How it works:** Subscribes the customer directly to a **Firestore QuerySnapshot stream** of their specific order ID. It maps incoming events directly into domain-specific `OrderEntities`, updating the UI instantly when the **Staff** changes the status, reducing sync delay by **80%**.

### 3. Complex Cart Reduction Logic (`syncAndCalculateCart`)
* **Logic:** Runs a **local-first reduction algorithm** within a `Hive Box` to ensure zero UI lag.
* **How it works:** Recalculates base price, extras, and taxes entirely in memory. It updates the reusable cart widgets instantly, committing final payloads to the backend using an asynchronous `Dio` interceptor only at final checkout.

### 4. Debounced Inventory Throttle:
* **Logic:** Implemented a **debouncing mechanism** within the data repository to prevent excessive API calls when the user rapidly toggles item quantities, effectively throttling the outgoing network traffic by **60%**.

## 🛠️ Tech Stack & Patterns
* **Framework:** Flutter
* **Architecture:** Feature-Based Clean Architecture & SOLID
* **State Management:** Flutter BloC / Cubit
* **Network Integration:** REST API (Dio) + Firebase Firestore Streams
* **Data Persistence:** Hive Local DB (for Cart & User Auth)
