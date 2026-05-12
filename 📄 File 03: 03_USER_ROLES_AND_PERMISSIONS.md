# User Roles and Permissions Matrix - Dental Clinic System

## 1. Introduction
This document defines the Access Control Levels (ACL) for the Dental Clinic Appointment Management System. The system uses Role-Based Access Control (RBAC) to ensure data security and operational integrity.

## 2. Role Definitions
* **Admin:** The system owner with unrestricted access to all modules, including financial data and system configurations.
* **Doctor:** Medical professional focused on patient treatment, clinical records, and their personal schedule.
* **Receptionist:** Operational staff responsible for patient flow, front-desk tasks, and billing.
* **Patient:** External user with limited access to personal records and booking features.

## 3. Permissions Matrix
| Feature / Module | Admin | Doctor | Receptionist | Patient |
| :--- | :---: | :---: | :---: | :---: |
| **Dashboard (Financial Stats)** | Full | No | No | No |
| **Dashboard (Daily Appointments)** | Full | Personal | Full | No |
| **User Management (Create/Edit)** | Full | No | No | No |
| **Patient Registration** | Yes | No | Yes | No |
| **EHR & Visual Dental Chart** | View | Full | No | View Only |
| **Medical Prescriptions/Notes** | View | Full | No | View Only |
| **Manage Appointments (Book/Reschedule)** | Yes | Yes | Yes | Personal |
| **Cancel Appointments** | Yes | Yes | Yes (Manual) | Personal (24h rule) |
| **Services & Pricing Setup** | Full | No | No | No |
| **Invoicing & Payments** | Full | No | Yes | View Own |
| **Financial Reports (Income/Debt)** | Full | No | No | No |
| **Inventory & Stock Management** | Full | View | Yes | No |
| **Feedback Management** | Full | View | No | Create |

## 4. Specific Access Rules
### A. Appointment Cancellation
* **Automated (Patient):** Allowed if `CurrentDateTime` < `AppointmentDateTime - 24 Hours`.
* **Manual (Receptionist/Admin):** Can override the 24-hour rule to cancel at any time.

### B. Medical Data Privacy
* **Receptionists** can view patient contact information but are strictly blocked from accessing the **Visual Dental Chart** or **Medical History**.
* **Doctors** cannot see the **Total Clinic Revenue** or other doctors' productivity reports.

### C. Inventory Alerts
* Both **Admin** and **Receptionist** receive notifications when stock levels fall below the defined threshold.

## 5. UI Customization (Arabic Interface)
* The Sidebar/Navigation menu will dynamically show/hide links based on the logged-in user's role to maintain a clean Arabic UI experience.
