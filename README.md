# -The-RealEstate-Management-System(REMS)
Manage Your Property With Ease



[![Java EE](https://img.shields.io/badge/JavaEE-7.0-blue.svg)](https://javaee.github.io/)
[![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-blue)](https://www.postgresql.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) 

An enterprise-grade software solution designed to streamline real estate operations, manage multi-tenant compliance registers, and automate workflow auditing pipelines. The platform coordinates operations between property managers, owners, maintenance personnel, tenants, administrators, and real estate agents.

---

## 👥 Authors & Contributors

*   **Mabane TS** — 231594760
*   **Mkhatshwa ML** — 224266499
*   **Khomu PN** — 224142218
*   **Aphane IT** — 221062167
*   **Sibambo AB** — 230547335
*   **Dlamini OS** — 224437382

---

## 👁️ System Vision & Objectives

The primary objective of the **Real Estate Management System (REMS)** is to replace legacy spreadsheet-based workflows with a unified collection of secure transactional registers and analytical reporting tools. 

Key functional objectives include:
*   **Property Registry Lifecycle:** Automated property data capture, historical data updates, and media/document correlation.
*   **Tenant Workflow Automation:** Simplified tenant screening, secure admission tracking, lease management, and structured tenant departure verification.
*   **Operational Logs:** Integrated maintenance request tracking, property inspections monitoring, and financial sales logging.
*   **Compliance Analytics:** On-screen data previews paired with multi-format audit report compilation (`.pdf`, `.csv`, `.txt`) matching programmatic South African market requirements.

---

## 👤 System Actors

The platform isolates system interactions into six discrete role-based profiles:
1.  **Administrator:** Monitors system state telemetry, analyzes financial transactions, reviews logs, handles validation exceptions, and issues structural governance documents.
2.  **Property Manager:** Manages listing states, reviews application workflows, and monitors ongoing occupancy balances.
3.  **Property Owner:** Tracks active assets, monitors incoming revenue allocations, and tracks building depreciation data.
4.  **Real Estate Agent:** Captures incoming property assets, updates marketing data, links physical files/images, and logs active sales agreements.
5.  **Tenant:** Searches active listings, submits rental application forms, runs secure payments, and files maintenance tickets.
6.  **Maintenance Staff:** Audits incoming maintenance requests, updates repair pipeline metrics, logs associated expenses, and commits engineering action reports.

---

## ⚡ Functional Requirements Matrix

*   **Authentication Tier:** Secure multi-role user registration and cryptographic user session authentication.
*   **Data Capture Layer:** Form validation structures for property details, ownership metrics, and pricing arrays.
*   **Document Management Storage:** Relational mapping of media attachments, tenancy contracts, and physical inspection documents.
*   **Tenancy Lifecycle Pipelines:** Tracking engines handling onboarding profiles, active lease monitoring, dispute management, and departure slip generation.
*   **Financial Processing Unit:** Safe processing endpoints for tracking rent transfers, deposit escrows, and sales transactions.
*   **Maintenance Workflows:** Dynamic engineering tickets allowing status transformations, photo attachments, and prioritization updates.

---

## 📊 Behavioral Architecture: Event-Table Blueprint

| Event | Trigger Input | Source Actor | Core Use Case | System Response | Destination |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Buyer applies for property** | Submits property application | Buyer | Property Application | Logs application data to database | Database / Admin |
| **Administrator reviews application** | Opens pending applications list | Administrator | Review Application | Compiles application approval/rejection state | Buyer / Admin |
| **Tenant submits rental application** | Submits localized rental form | Tenant | Rental Application | Logs rental contract application row | Database / Admin |
| **Administrator reviews rental app** | Requests active application queue | Administrator | Review Application | Commits lease approval/rejection vector | Tenant / Admin |
| **Property Agent captures property** | Enters building details profile | Property Agent | Capture Property Data | Generates new active property registry row | Database |
| **Agent uploads property photo** | Attaches structural image media | Property Agent | Upload Property Photo | Persists media array to record mapping | Database |
| **Tenant admitted to property** | Assigns tenant profile to unit | Data Clerk | Record Tenant Submission | Transforms target property state mapping | Database |
| **Property sale recorded** | Completes purchasing ledger | Property Agent | Record Property Sale | Commits irreversible financial transaction row | Database / Admin |
| **Tenant submits maintenance request** | Requests utility repair help | Tenant | Record Maintenance Request| Inserts active engineering ticket row | Database / Admin |
| **Administrator generates property report**| Invokes property asset breakdown | Administrator | Print Property Report | Compiles real-time property catalog output | Administrator |
| **Administrator generates tenant report**  | Invokes active lease audit trail | Administrator | Print Tenant Report | Compiles live tenancy summary ledger | Administrator |
| **Administrator generates sales report**   | Invokes structural financial data | Administrator | Print Sales Report | Compiles historical transaction summary | Administrator |
| **Administrator generates maintenance report**| Invokes engineering ticket log | Administrator | Print Maintenance Report | Compiles cost and performance analysis | Administrator |

---

## 📝 Use Case Specifications

### 1. Capture Property Data
*   **Triggering Event:** A Property Manager decides to add a new property listing into the system.
*   **Brief Description:** A real estate agent records complete property information (owner details, property specifications, pricing, and images) into the system so that the property can be listed for sale or rent.
*   **Primary Actor:** Property Manager
*   **Related Use Cases:** `Validate Owner Details`, `Upload Property Images`, `Verify Property Information`
*   **Pre-conditions:**
    *   Property owner has submitted the property for listing.
    *   The agent is authenticated and logged into the system.
    *   The property does not already exist in the system.
    *   Required property documentation is available.
*   **Post-conditions:**
    *   Property record is successfully stored in the system database.
    *   Property becomes available for search and listing.
    *   Confirmation is displayed to the agent.
*   **Flow of Activities:**
