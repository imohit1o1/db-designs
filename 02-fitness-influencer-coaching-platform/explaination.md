# 🧠 Fitness Coaching Platform – ER Diagram Explanation

## 👤 Users
- Stores all users of the platform.
- A user can be either a **client** or a **trainer**.
- Common details like name, email, password are stored here.

---

## 🔑 Tokens
- Used for authentication and security.
- Stores different types of tokens:
  - refresh token
  - verification token
  - password reset token
- Each token belongs to one user.

---

## 🤝 Trainer–Client Relationship
- `trainer_clients` handles **many-to-many** relation.
- One trainer can have many clients.
- One client can have multiple trainers.
- Tracks when the relationship started and ended.

---

## 📦 Plans
- Represents coaching programs created by trainers.
- Includes:
  - name
  - price
  - duration
- Each plan is created by a trainer.

---

## 🧾 Subscriptions
- Represents when a client **purchases a plan**.
- Links:
  - client
  - trainer
  - plan
- Stores:
  - start and end date
  - current status (active, expired, cancelled)

---

## 📅 Sessions
- Represents scheduled interactions:
  - consultation calls
  - live sessions
- Linked to:
  - client
  - trainer
  - subscription (optional)
- Stores schedule, duration, meeting link, and status.

---

## 💳 Payments
- Stores payment details for subscriptions.
- Includes:
  - amount
  - payment method
  - payment status
- Each payment is linked to a subscription.

---

## 📊 Progress Tracking
- Stores measurable fitness data over time.
- Flexible design using:
  - metric type (weight, BMI, etc.)
  - value
- Can be recorded by trainer or system.

---

## ✅ Check-Ins
- Represents regular updates from clients.
- Includes:
  - date
  - weight
  - notes
- Helps trainers monitor consistency and progress.

---

## 🔗 Relationships Summary

- One **user** → many **tokens**
- Trainers ↔ Clients → many-to-many (`trainer_clients`)
- One **trainer** → many **plans**
- One **client** → many **subscriptions**
- One **subscription** → one **plan**
- One **subscription** → many **sessions**
- One **subscription** → many **payments**
- One **client** → many **check-ins**
- One **client** → many **progress records**

---

## 🧠 Key Design Points

- Separation of concerns:
  - plans ≠ subscriptions ≠ sessions
- Supports:
  - multiple trainers per client
  - multiple plans per client
- Flexible progress tracking system
- Real-world coaching workflow is properly modeled