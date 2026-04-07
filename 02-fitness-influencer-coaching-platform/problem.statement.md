# 🛍️ Thrift & Handmade Store – ER Diagram Assignment

## 📌 Instructions

A small creator has started an Instagram-based store where they sell thrifted fashion items and handmade products. Initially, the business is very small and receives orders through Instagram DMs and WhatsApp.

As the business grows, the owner now wants a system to:
- manage products
- track available stock
- handle customer orders properly
- maintain basic information about delivery and payments

---

## 🧠 Business Context

- Some products are **thrifted** and only have **one piece available**
- Some products are **handmade** and can have **multiple units**
- Some items may have attributes like:
  - size
  - color
  - condition

The owner also wants to:
- store customer details
- track order history
- track payment status
- track shipping status

---

## 🎯 Your Task

Design an **ER diagram** for this business.

This is not just a basic “shop” problem. You must carefully model:
- differences between thrift and handmade products
- inventory behavior
- order structure

---

## ❓ Your Design Should Answer

- What products are being sold?
- Are they thrifted or handmade?
- How many pieces are available?
- Which customer placed which order?
- What items are included in each order?
- Was the order paid?
- Has the order been shipped or delivered?
- Can one customer place multiple orders?
- Can one order contain multiple products?
- How are product details like size, category, color, condition stored?

---

## 🧩 What to Include

Your ER diagram must include:

- All important **entities**
- Attributes for each entity
- Primary key (PK) for each main entity
- Foreign keys (FK) where relationships exist
- Proper relationships between entities
- Cardinality (1:1, 1:M, M:N)
- Junction tables for many-to-many relationships

---

## ⚠️ Design Considerations

- A customer can place multiple orders
- One order can contain multiple products
- Some products are **unique (thrift)**
- Some products have **multiple inventory units (handmade)**
- Consider whether **product condition** should be stored
- Model **payment and shipping** properly
- Avoid mixing unrelated data in one entity
- Keep the design **normalized and clean**
- Use **meaningful naming conventions**

---

## 🚫 What You Don’t Need To Do

- No SQL queries required
- No frontend or backend implementation required
- Only focus on **database design (ER diagram)**

---

## 📤 Submission

Submit any one of the following:
- Image export (PNG/JPG)
- PDF export
- Excalidraw / Draw.io / FigJam link
- GitHub repo containing the diagram

---

## ✅ Expectations

- Single, clean, readable diagram
- Clearly visible entity and attribute names
- PK and FK properly marked
- Relationships clearly drawn (not messy)
- Proper structure and clarity