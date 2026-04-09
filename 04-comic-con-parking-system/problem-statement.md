# 🚗 Comic-Con Parking System

**Web Dev Cohort 2026 – Databases**

---

## ⏱️ Timeline

* **Start:** Apr 9, 2026, 9:30 AM
* **Due:** Apr 10, 2026, 12:30 AM
* **Evaluation Begins:** Apr 10, 2026, 1:00 AM
* **Evaluation Ends:** Apr 10, 2026, 11:59 PM

---

## 📌 Instructions

A large convention venue hosts Comic-Con India, where thousands of visitors arrive across multiple days for anime screenings, cosplay competitions, gaming showcases, creator meetups, merchandise zones, and panel discussions.

During the event, people arrive using bikes, cars, SUVs, cabs, and EV vehicles. The venue has a structured parking facility divided into multiple zones and levels. Some parking areas are reserved for cosplayers with props, exhibitors, creators, VIP guests, staff members, and EV charging vehicles.

Whenever a vehicle enters the parking facility, the system generates a parking ticket and assigns a suitable parking spot depending on vehicle type and availability. When the vehicle exits, the system records exit time and calculates the parking fee.

The venue management wants a system that can track:

* Vehicles entering the parking facility
* Vehicle categories
* Parking spot allocation
* Reserved parking categories
* Entry and exit timestamps
* Parking sessions
* Payment status
* Spot availability across zones and levels

This is a **multi-zone event parking system** where vehicle types, access categories, sessions, tickets, and payments must be modeled properly.

---

## 🎯 What You Have to Do

Your design should be able to answer questions like:

* What vehicles entered the parking facility?
* What type of vehicle entered?
* Which parking spot was assigned?
* Which zone or level does that parking spot belong to?
* Was the parking spot reserved for exhibitors, VIP guests, staff, or EV charging?
* When did the vehicle enter the facility?
* When did the vehicle exit the facility?
* What ticket was issued for the parking session?
* Can one vehicle visit the venue multiple times across different days?
* Can one parking spot be reused across multiple parking sessions?
* How is parking availability tracked?
* How are parking charges calculated?
* How is payment recorded for each parking session?
* Can special access categories (cosplayers with props, exhibitors, VIP guests, staff) be represented?
* Can the system track which vehicles are currently parked inside the venue?

---

## 🧩 What to Make

Design the **ER diagram** for this parking system.

Your ERD should include the important structures needed for:

* Vehicles
* Vehicle categories
* Parking spots
* Parking spot categories
* Parking zones or parking levels
* Parking tickets
* Parking sessions (entry and exit tracking)
* Payment records

---

## 🤔 Things to Think About

* One vehicle can enter multiple times during the event
* One parking spot can serve many vehicles over time
* Parking sessions should store entry and exit timestamps
* Tickets and parking sessions may be separate structures
* Different vehicle types require different parking spot types
* Some parking spots may be reserved
* Parking availability must be trackable
* Zones or levels may contain multiple parking spots
* Payments should be connected to parking sessions
* Avoid putting everything into one single entity

---

## 🚫 What You Do NOT Need

* SQL queries
* Frontend or backend implementation

👉 This task is **only about database design**.

---

## 📤 Submission Instructions

Submit any one of the following:

* An image export of your ER diagram
* A PDF export of your ER diagram
* An Excalidraw / Eraser / Draw.io / FigJam board link
* A GitHub repository link containing the diagram file or exported image

---

## ✅ Submission Expectations

* One single board is preferred
* The diagram must be readable
* Entity names and attribute names should be clearly visible
* Primary Keys (PK) and Foreign Keys (FK) should be clearly marked
* Relationship lines should not look random or confusing
* If you use GitHub, keep the diagram inside the repo properly and include a short README

---

## 📊 Evaluation Parameters

### 🧠 Parking System Understanding (15 marks)

* Did the student understand that this is a multi-zone event parking system, not a simple parking entry-exit tracker?
* Did they capture vehicle types, spot allocation, sessions, tickets, and payments separately?

### 🧱 Entity Quality (20 marks)

* Did they capture vehicle, vehicle category, parking spot, parking zone/level, parking session, ticket, and payment structures properly?
* Did they represent reserved categories such as VIP, exhibitors, staff, or EV charging where needed?

### 🔗 Relationship Modeling (20 marks)

* Are vehicle–session relations designed correctly?
* Are zone–spot relationships structured properly?
* Is spot reuse across multiple parking sessions modeled correctly over time?
* Are many-to-many relations handled properly wherever required?

### 🧾 Attribute and Table Design (15 marks)

* Are important attributes like entry time, exit time, ticket number, vehicle type, spot category, and payment status modeled properly?
* Is information distributed logically instead of being placed inside one large table?

### 🔑 PK/FK and Junction Tables (15 marks)

* Did the student define primary keys for all major entities?
* Are foreign keys placed correctly to support relationships?
* Did they introduce junction tables wherever necessary?

### 🌍 Real-World Practicality (10 marks)

* Does the design support multiple visits by the same vehicle across event days?
* Can parking spots be reused across sessions?
* Can reserved parking categories and EV charging spots be represented realistically?
* Can the system track currently parked vehicles?

### 🧹 Diagram Neatness (5 marks)

* Is the ER diagram clearly structured and readable?
* Are entities, attributes, PKs, and relationships easy to review?

---
