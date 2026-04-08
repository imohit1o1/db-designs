# 🏥 Clinic Appointment and Diagnostics Platform – Problem Statement

## 📌 Overview
A modern clinic wants to digitize its operations. The system should manage doctors, patients, appointments, consultations, diagnostic tests, reports, and payments in a clean and structured way.

Patients should be able to:
- book appointments with doctors
- visit the clinic for consultation
- undergo diagnostic tests if prescribed
- receive reports later

---

## ⚙️ System Context
- The clinic has multiple doctors.
- Each doctor belongs to a department or specialization.
- A patient can visit the clinic multiple times.
- During a consultation, doctors may prescribe tests.
- Reports are generated after tests and linked back to the visit.

---

## ❓ Key Questions the System Should Answer

- Who are the doctors and what are their specialties?
- Which patient booked which appointment?
- What is the status of an appointment?
- Did the appointment result in a consultation?
- Were any diagnostic tests prescribed?
- What reports were generated?
- Can one patient have multiple visits?
- Can one doctor attend many patients?
- Can one consultation lead to multiple tests?
- How are payments linked to appointments or consultations?

---

## 🧠 Design Considerations

- Difference between:
  - appointment (booking)
  - consultation (actual visit)
- One appointment may or may not result in a consultation
- Diagnostic tests should be linked to the correct stage (consultation)
- Reports should be clearly associated with tests
- Decide whether:
  - doctor specialization is separate or an attribute
  - multiple tests can belong to one consultation
- Payments should be connected to the correct entity (appointment or consultation)

---

## 🎯 Objective

Design an **ER diagram** that models:
- patients
- doctors
- appointments
- consultations / visits
- diagnostic tests
- reports
- payments

The design should:
- reflect real clinic workflow
- maintain clear relationships
- avoid ambiguity
- be simple yet scalable