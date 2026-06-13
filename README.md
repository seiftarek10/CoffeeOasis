# ☕ Coffee Oasis — Realtime Multi-Flavor Coffee Shop System

<!-- TECH BADGES -->
<p align="left">
  <img src="https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white" alt="Flutter" />
  <img src="https://img.shields.io/badge/DevOps-Flavors--3--Roles-blueviolet?style=for-the-badge" alt="Flavors" />
  <img src="https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black" alt="Firebase" />
  <img src="https://img.shields.io/badge/BLoC%20%2F%20Cubit-0175C2?style=for-the-badge&logo=dart&logoColor=white" alt="BLoC" />
  <img src="https://img.shields.io/badge/Architecture-Clean-brightgreen?style=for-the-badge" alt="Clean Architecture" />
</p>

> 🚀 A high-performance management ecosystem tailored for physical Coffee Shops. Built on **Clean Architecture** and isolated via native **Product Flavors** to power Customers, Baristas, and Owners from a single codebase.

---

### 🏗️ 📐 Presentation & Multi-Flavor DevOps

* **🎭 Production-Grade Flavors (User ➔ Staff ➔ Owner):** Natively segregated Gradle and Xcode build configurations to compile completely independent apps from one clean codebase.
* **🧩 Atomic Widget Library:** Generic UI wrappers (Menu Cards, Option Toggles, Order Cards) engineered to strictly isolate the **Presentation Layer**.
* **🛵 Hybrid Checkout UI:** Adaptive ordering fields that instantly toggle layout based on customer choice: **Home Delivery** configuration or **In-Store Pickup**.

---

### ⚡ 🔮 Core Project Functions & Role Workflows

#### 1️⃣ 👑 OWNER FLAVOR: Content Control & Shop Context (`manageShopContext`)
* **🧠 Logic:** Absolute administrative power to update the physical shop's digital twin instantly.
* **⚙️ Steps:** Owner injects new **Coffee Drinks & Categories** ➔ Edits **Shop Info** (Location, Hours) ➔ Writes directly to Firestore, forcing an instant menu refresh across all Customer apps.

#### 2️⃣ 👤 USER FLAVOR: Local-First Custom Cart (`syncAndCalculateCart`)
* **🧠 Logic:** Zero UI lag during real-time drink customization (Size, Milk choices, Sugar extras).
* **⚙️ Steps:** Intercepts customization clicks inside **Hive Box** ➔ Computes prices and add-on modifiers instantly in-memory ➔ Commits final transaction to Firestore at checkout.

#### 3️⃣ 👤 USER FLAVOR: Dynamic Fulfillment & Live Tracking (`streamOrderTrackingStatus`)
* **🧠 Logic:** Supports dual fulfillment types (**Delivery / Pickup**) with zero-polling, native live status updates.
* **⚙️ Steps:** Customer selects checkout mode ➔ Binds UI to a **Firestore Document Stream** ➔ Updates tracking view instantly the exact millisecond the barista changes the status.

#### 4️⃣ 👨‍🍳 STAFF FLAVOR: Live Barista Dashboard (`streamStaffActiveOrders`)
* **🧠 Logic:** Instant, synchronized preparation queue for baristas and kitchen staff.
* **⚙️ Steps:** Listens to active Firestore streams filtering incoming shop orders ➔ Barista updates document state (from `Pending` ➔ `Preparing` ➔ `Ready for Delivery/Pickup`) ➔ Signals customers instantly.

---

### 🛠️ 💻 Tech Stack

* **📱 Framework:** Flutter (Cross-Platform iOS & Android)
* **📐 Architecture:** Feature-Based Clean Architecture & SOLID
* **⚙️ DevOps:** Native Product Flavors (User, Staff, Owner)
* **🔄 State Management:** Flutter BloC / Cubit (Unidirectional Flow)
* **🔥 Backend:** Firebase Authentication & Cloud Firestore Streams
* **💾 Persistence:** Hive Local Binary DB (Menu Caching & Session Management)
