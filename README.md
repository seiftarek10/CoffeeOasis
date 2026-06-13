# ☕ Coffee Oasis — Realtime Coffee Shop & Order Management System

<!-- TECH BADGES -->
<p align="left">
  <img src="https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white" alt="Flutter" />
  <img src="https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black" alt="Firebase" />
  <img src="https://img.shields.io/badge/BLoC%20%2F%20Cubit-0175C2?style=for-the-badge&logo=dart&logoColor=white" alt="BLoC" />
  <img src="https://img.shields.io/badge/Architecture-Clean-brightgreen?style=for-the-badge" alt="Clean Architecture" />
</p>

> 🚀 A specialized, real-time management ecosystem tailored for a physical Coffee Shop. Built on **Clean Architecture** to power a dynamic 3-way operational loop (Customer, Staff, and Owner).

---

### 🏗️ 📐 Presentation & Reusable Widgets

* **🧩 Atomic Widget Library:** Custom generic wrappers (Item Cards, Option Toggles, Status Badges) engineered to strictly isolate the **Presentation Layer**.
* **🎭 3-Way Dynamic UI (User ➔ Staff ➔ Owner):** Intelligent UI screens that dynamically switch layouts and management features based on the active role's permissions.
* **🛵 Dynamic Checkout Layouts:** Adaptive order forms that instantly toggle UI fields based on user choice: **Home Delivery** tracking or **In-Store Pickup**.

---

### ⚡ 🔮 Realtime Core Functions & Business Logic

#### 1️⃣ 👑 OWNER: Shop Management & Content Control (`manageShopContext`)
* **🧠 Logic:** Gives the owner full administrative power to update the physical shop's digital twin instantly.
* **⚙️ Steps:** Owner adds/updates **Coffee Drinks & Categories** ➔ Edits **Shop Info** (Location, Working Hours) ➔ Writes directly to Firestore, forcing an instant menu refresh across all Customer apps.

#### 2️⃣ 👤 USER: Local-First Custom Cart (`syncAndCalculateCart`)
* **🧠 Logic:** Guarantees zero UI lag during real-time drink customization (Size, Milk choices, Sugar extras).
* **⚙️ Steps:** Intercepts customization toggles inside **Hive Box** ➔ Computes base prices and add-on modifiers in-memory ➔ Commits final payload to **Cloud Firestore** at checkout.

#### 3️⃣ 👤 USER: Hybrid Fulfillment & Tracking (`streamOrderTrackingStatus`)
* **🧠 Logic:** Supports dual fulfillment types (**Delivery / Pickup**) with zero-polling live status updates.
* **⚙️ Steps:** Customer selects checkout mode ➔ Binds UI to a **Firestore Document Stream** ➔ Updates tracking view instantly when the order moves from cooking to dispatched/ready.

---

#### 4️⃣ 👨‍🍳 STAFF: Live Kitchen Dashboard (`streamStaffActiveOrders`)
* **🧠 Logic:** Instant, synchronized preparation queue for baristas and kitchen staff.
* **⚙️ Steps:** Listens to active Firestore streams filtering incoming orders ➔ Staff advances order status (e.g., from `Pending` to `Preparing` ➔ `Ready`) ➔ Signals both customers and delivery drivers instantly.

---

### 🛠️ 💻 Tech Stack

* **📱 Framework:** Flutter (iOS & Android)
* **📐 Architecture:** Feature-Based Clean Architecture & SOLID
* **🔄 State Management:** Flutter BloC / Cubit (Unidirectional Flow)
* **🔥 Backend:** Firebase Authentication & Cloud Firestore Streams
* **💾 Persistence:** Hive Local Binary DB (Menu Caching & Session Management)
