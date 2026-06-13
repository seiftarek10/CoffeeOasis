# ☕ Coffee Oasis — Realtime Multi-Flavor Coffee Shop System

<!-- TECH BADGES -->
<p align="left">
  <img src="https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white" alt="Flutter" />
  <img src="https://img.shields.io/badge/DevOps-Flavors--3--Roles-blueviolet?style=for-the-badge" alt="Flavors" />
  <img src="https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black" alt="Firebase" />
  <img src="https://img.shields.io/badge/BLoC%20%2F%20Cubit-0175C2?style=for-the-badge&logo=dart&logoColor=white" alt="BLoC" />
  <img src="https://img.shields.io/badge/Architecture-Clean-brightgreen?style=for-the-badge" alt="Clean Architecture" />
</p>

> 🚀 Real-time management app for physical Coffee Shops. Built on **Clean Architecture** using native **Product Flavors** (User, Staff, Owner) in a single codebase.

---

### 🏗️ 📐 Presentation & Multi-Flavor DevOps

* **🎭 3 Native Flavors:** Segregated Gradle/Xcode configs to compile independent apps (User, Staff, Owner).
* **🧩 Atomic Widgets:** Generic custom wrappers (Menu Cards, Custom Buttons) to prevent UI duplication.
* **🛵 Hybrid Checkout:** Dynamic fields that instantly toggle layouts for **Home Delivery** or **In-Store Pickup**.

---

### ⚡ 🔮 Core Project Functions

#### 1️⃣ 👑 OWNER FLAVOR: Content Control
* **🧠 Logic:** Absolute admin power over the physical shop's menu and data.
* **⚙️ Steps:** Owner adds **Drinks & Categories** + edits **Shop Info** ➔ Updates Firestore ➔ Triggers instant menu refresh for customers.

#### 2️⃣ 👤 USER FLAVOR: Local-First Custom Cart
* **🧠 Logic:** Zero UI lag during complex drink customization (Size, Milk, Sugar extras).
* **⚙️ Steps:** Intercepts clicks inside **Hive Box** ➔ Computes prices and add-ons in-memory ➔ Commits payload to Firestore at checkout.

#### 3️⃣ 👤 USER FLAVOR: Live Order Tracking
* **🧠 Logic:** Supports Delivery/Pickup modes with zero-polling, real-time updates.
* **⚙️ Steps:** Binds UI to a **Firestore Document Stream** ➔ Updates tracking view instantly when status changes.

#### 4️⃣ 👨‍🍳 STAFF FLAVOR: Live Barista Dashboard
* **🧠 Logic:** Synchronized live preparation queue for baristas.
* **⚙️ Steps:** Streams incoming orders from Firestore ➔ Barista shifts status (`Pending` ➔ `Preparing` ➔ `Ready`) ➔ Signals customer instantly.

---

### 🛠️ 💻 Tech Stack

* **📱 Framework:** Flutter (iOS & Android)
* **📐 Architecture:** Feature-Driven Clean Architecture
* **⚙️ DevOps:** Native Product Flavors (User, Staff, Owner)
* **🔄 State Management:** Flutter BloC / Cubit
* **🔥 Backend:** Firebase Authentication & Cloud Firestore Streams
* **💾 Persistence:** Hive Local Binary DB (Menu & Session Caching)
