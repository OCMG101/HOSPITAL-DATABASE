# 🏥 Hospital ER Database

A normalized relational schema for managing an Emergency Room (ER) database system, with detailed handling of personnel, shifts, patient admissions, medication administration, and bed supervision.

---

## 📘 Overview

This repository contains the design and SQL schema for an ER management system. It covers entities such as doctors, nurses, patients, and administrative staff, as well as their interaction within hospital shifts and treatment processes.

---

## 🧱 Database Tables

### 👤 Person
Represents all individuals in the hospital system.
- `person_ID` (PK)
- `email`
- `phoneNumber`

### 🏠 Address
Represents physical addresses linked to persons.
- `number`, `street`, `state`, `city` (Composite PK)
- `persID` (FK → Person)

### ⏰ Shift
Describes time-based shift segments.
- `startTime`, `endTime`, `sdate` (Composite PK)

### 🧑‍💼 Receptionist
Receptionist-specific details.
- `receptionist_ID` (PK)
- `person_ID` (FK → Person)

### 🥼 Doctor
Doctor-specific data.
- `doctor_ID` (PK)
- `person_ID` (FK → Person)

### ⚕️ TriageDoctor
Identifies triage doctors.
- `tdoctor_ID` (PK)
- `doctor_ID` (FK → Doctor)

### 👩‍⚕️ Nurse
Nurse-specific data.
- `nurse_ID` (PK)
- `person_ID` (FK → Person)

### 🛏 Bed
Beds available in the ER.
- `bed_ID` (PK)
- `nurse_ID` (FK → Nurse)

### 🧑‍🦽 Patient
Admitted or treated patients.
- `patient_ID` (PK)
- `bed_ID` (FK → Bed)
- `person_ID` (FK → Person)
- `outcomeOfVisit`

### 💊 Medication
Medication catalog.
- `name` (PK)

### 🧾 Assigned
Tracks worker shift assignments.
- `person_ID`, `startTime`, `endTime`, `sdate` (Composite PK)
- FKs → `Shift`

### 💉 Administered
Tracks medication administration.
- `medication_name` (PK, FK → Medication)
- `nurse_ID` (FK → Nurse)
- `dosage`, `timesPerDay`, `timeAdministered`

### 🏥 Admitted
Tracks patient ER visits.
- `person_ID`, `receptionist_ID`, `startTime`, `endTime`, `date` (Composite PK)
- `admit_date`, `admit_time`, `discharge_date`, `discharge_time`, `primaryDiagnosis`
- FKs → `Person`, `Shift`, `Receptionist`

### 📋 Prescribed
Tracks medication prescriptions.
- `doctor_ID`, `patient_ID`, `medication_name` (Composite PK)
- FKs → `Doctor`, `Patient`, `Medication`

---

## 🛠 Technologies

- SQL for schema creation
- ER modeling principles
- (Optional) PostgreSQL or MySQL for implementation


---

## 🚀 Getting Started
1. Clone this repo.
2. Run the SQL file in a database of your choice.
3. Use or expand the schema with real data or front-end/backend integration.

---

## 🤝 Contributing
Feel free to fork the repo, propose changes, or suggest enhancements via pull requests or issues.

---
