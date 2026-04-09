# 🚗 Comic-Con Parking System – ER Diagram Explanation

## 🚙 Vehicle Categories

* Defines different types of vehicles entering the parking facility.
* Examples: **bike, car, SUV, EV, cab**.
* Used to determine:

  * parking compatibility
  * pricing rules

---

## 🚗 Vehicles

* Stores all vehicles entering the system.
* Each vehicle:

  * has a unique **vehicle number**
  * belongs to one **vehicle category**
* Owner details (name, phone) are stored for identification.

---

## 🗺️ Parking Zones

* Represents high-level divisions of the parking facility.
* Example:

  * Zone A, Zone B
* Helps in organizing large-scale parking areas.

---

## 🏢 Parking Levels

* Each zone can have multiple levels (floors).
* Example:

  * Basement 1, Basement 2
* Provides hierarchical structure:

  * **Zone → Level → Spot**

---

## 🏷️ Spot Categories

* Defines reserved types of parking spots.
* Examples:

  * general
  * VIP
  * staff
  * exhibitor
  * cosplayer
  * EV charging
* Used to enforce access control and allocation rules.

---

## 🅿️ Parking Spots

* Represents individual parking spaces.
* Each spot:

  * belongs to a **level**
  * has a **spot category** (reservation type)
  * supports a specific **vehicle category**
* `isActive` indicates if the spot is usable.

---

## ⏱️ Parking Sessions

* Core entity representing a vehicle’s parking lifecycle.
* Each session stores:

  * entry time
  * exit time
  * status (active, completed, cancelled)
* Links:

  * one **vehicle**
  * one **parking spot**
* Enables:

  * multiple visits by the same vehicle
  * reuse of parking spots over time

---

## 🎫 Tickets

* Generated when a vehicle enters the parking facility.
* Each ticket:

  * is linked to one **parking session**
  * has a unique **ticket number**
* Acts as a reference for the parking session.

---

## 💳 Payments

* Stores payment details for each parking session.
* Includes:

  * amount
  * payment method (cash, UPI, card)
  * payment status (pending, paid, failed)
* Linked directly to **parking sessions**

---

## ⚙️ Pricing Rules

* Defines pricing configuration.
* Based on:

  * vehicle category
  * spot category
* Enables flexible pricing:

  * e.g., EV charging spots cost more
  * VIP spots have premium pricing

---

## 🔗 Relationships Summary

* One **vehicle category** → many **vehicles**
* One **vehicle** → many **parking sessions**
* One **parking zone** → many **parking levels**
* One **parking level** → many **parking spots**
* One **spot category** → many **parking spots**
* One **vehicle category** → many **parking spots**
* One **parking spot** → many **parking sessions (over time)**
* One **parking session** → one **ticket**
* One **parking session** → one **payment**
* One **vehicle category + spot category** → one **pricing rule**

---

## 🧠 Key Design Points

### ✅ Multi-Visit Support

* A vehicle can have multiple parking sessions across different days.

### ✅ Spot Reusability

* Parking spots are reused across sessions using time-based tracking.

### ✅ Real-Time Tracking

* Vehicles currently inside:

  * sessions where `exitTime IS NULL` and `status = 'active'`

### ✅ Reserved Parking Support

* Spot categories handle VIP, staff, exhibitor, cosplayer, and EV reservations.

### ✅ Structured Parking Hierarchy

* Clear hierarchy:

  * Zone → Level → Spot

### ✅ Pricing Flexibility

* Pricing rules are separated from sessions.
* Allows dynamic pricing based on vehicle and spot type.

### ✅ Availability Tracking

* Availability is derived:

  * spots not assigned in active sessions are considered available

### ✅ Clean Separation of Concerns

* Session, ticket, and payment are modeled separately.
* Avoids overloading a single table.

---

## 🚀 Overall Design Strength

* Scalable for large multi-day events
* Supports real-world parking operations
* Proper normalization and relationship modeling
* Easily extendable for production systems

---
