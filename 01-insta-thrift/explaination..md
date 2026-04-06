# 📦 Thrift & Handmade Store – ER Diagram

This project presents a database design for a growing Instagram-based store that sells both thrifted (unique) and handmade (multi-unit) products.

## 🧠 Design Overview

The schema is structured to support real-world commerce operations, including:

### User Management
Stores customer details with token-based authentication support.

### Product Modeling
- `products` represent the catalog  
- `productVariant` defines SKU-level variations (size, color, price)  
- `inventory` tracks stock per variant  
  - Supports both **unique thrift items (quantity = 1)**  
  - and **handmade items (quantity > 1)**  

### Order System
- `orders` store high-level order data  
- `orderItems` enable multiple products per order  
- Includes **price snapshot (`orderPrice`)** to preserve historical accuracy  

### Address & Shipping
- `addresses` store reusable user addresses  
- `shippings` stores snapshot delivery details per order  

### Payments
Handles multiple payment methods and tracks transaction status independently.

---

## 🔗 Key Relationships

- One **user → many orders**  
- One **order → many orderItems**  
- One **product → many variants**  
- One **variant → one inventory record**  
- One **order → one payment & shipping record**  

---

## ⚙️ Key Design Decisions

- Separation of **product, variant, and inventory** for scalability  
- Support for **unique vs reusable inventory** using `isUnique`  
- Use of **orderItems** to handle many-to-many relationships  
- Snapshot-based **shipping data** to preserve order history  
- Token system for flexible authentication flows  