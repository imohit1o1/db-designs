# 🏥 Clinic Platform – ER Diagram Explanation

## 👤 Users
- Stores all users of the system.
- A user can be either a **doctor** or a **patient**.
- Common fields like name, email, password are stored here.

---

## 🔑 Tokens
- Used for authentication flows.
- Supports:
  - refresh token
  - verification token
  - password reset token
- Each token belongs to one user.

---

## 🧑‍⚕️ Doctor Profile
- Stores doctor-specific details.
- Linked to:
  - user
  - specialization
- Includes experience and professional info.

---

## 🧑 Patient Profile
- Stores patient-specific details.
- Linked to user.
- Includes:
  - DOB
  - gender
  - address

---

## 🏥 Departments & Specializations
- `departments` → high-level categories (e.g., Cardiology)
- `specializations` → specific expertise (e.g., Heart Surgeon)
- Each specialization belongs to a department.
- Doctors are linked to specializations.

---

## 📅 Appointments
- Represents booking between patient and doctor.
- Stores:
  - scheduled time
  - status (scheduled, completed, cancelled, no_show)

---

## 🩺 Consultation Visits
- Represents the **actual doctor visit**.
- Linked 1:1 with appointment.
- Created only if patient shows up.

---

## 🧪 Diagnostic Tests
- Tests prescribed during consultation.
- One consultation can have multiple tests.
- Tracks test status (prescribed, in_progress, completed).

---

## 📄 Reports
- Generated after diagnostic tests.
- Each report belongs to one test.
- Stores report file and generation status.

---

## 💳 Payments
- Stores payment details.
- Linked to consultation (not appointment).
- Includes:
  - amount
  - method
  - status

---

## 🔗 Relationships Summary

- One **user** → one **doctor profile / patient profile**
- One **department** → many **specializations**
- One **specialization** → many **doctors**
- One **patient** → many **appointments**
- One **doctor** → many **appointments**
- One **appointment** → one **consultation (optional)**
- One **consultation** → many **tests**
- One **test** → one **report**
- One **consultation** → one **payment**

---

## 🧠 Key Design Points

- Clear workflow:
  - appointment → consultation → tests → reports → payment
- Separation of booking and actual visit
- No ambiguous relationships (each entity has one owner)
- Scalable and matches real clinic operations