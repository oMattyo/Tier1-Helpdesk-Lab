# Naming Standards

This document defines the naming and classification rules used throughout the Tier 1 HelpDesk Lab.  
The goal is consistency, searchability, and alignment with real-world IT service desk practices.

---

## 1. Ticket Type (ITIL Classification)

Every ticket must be classified as one of the four ITIL types at intake:

| Type              | Meaning                                      | When to use                                      | Example                                      |
|-------------------|----------------------------------------------|--------------------------------------------------|----------------------------------------------|
| **Incident**      | Unplanned disruption – restore service       | Something is broken                              | “Cannot print to Lab-Printer-01”             |
| **Service Request** | Routine, pre-approved ask                  | User needs something new or changed              | “Add user to Marketing share”                |
| **Problem**       | Root cause behind one or more incidents      | Investigating why something keeps happening      | “Recurring account lockouts after password change” |
| **Change Request**| Planned modification to a service            | Controlled change (rarely used in this Tier 1 lab) | “Deploy new printer via GPO”                 |

**Rule of thumb**  
- Broken → **Incident**  
- Needed → **Service Request**

---

## 2. Category → Subcategory

Use a simple two-level hierarchy. Keep it consistent across all tickets.

### Common Incident Categories (used in this lab)

| Category     | Sub-Categories                                                 |
|--------------|------------------------------------------------------------------|
| Access       | Password Reset, Account Lockout, Permissions, Group Membership |
| Network      | Connectivity, DNS, IP Configuration, VPN                       |
| Devices      | Printer, Desktop/Laptop, Peripherals                           |
| Software     | Application, OS, Driver                                        |
| File Access  | Share Permissions, NTFS, Mapped Drives                         |
| GPO          | Policy Not Applying, Unexpected Policy, Conflict               |
| Identity     | User Creation, Attribute Change, Account Status                |

### Common Service Request Categories

| Category       | Sub-Categories                                      |
|----------------|-------------------------------------------------------|
| User Services  | Onboarding, Account Management, Group Membership    |
| Access         | File Access, Printer Access, Application Access     |
| Hardware       | Printer Setup, Device Configuration                 |
| Information    | How-to, Policy Clarification                        |

---

## 3. Ticket ID Format

All tickets use a structured ID for easy reference and folder mapping:

| Code | Meaning              | Example          |
|------|----------------------|------------------|
| ACC  | Access / Identity    | T1-ACC-001       |
| DNS  | DNS / Network        | T1-DNS-003       |
| PRN  | Printer              | T1-PRN-004       |
| FIL  | File Access          | T1-FIL-012       |
| GPO  | Group Policy         | T1-GPO-007       |
| NET  | General Network      | T1-NET-015       |
| SFT  | Software             | T1-SFT-009       |

**Full example:**  
`T1-PRN-004` = Tier 1, Printer category, ticket number 004

---

## 4. Subject / Summary Line

Use a short, specific, noun-phrase format: Component - Symptom - Scope


**Good examples**

| Type            | Subject Line                                      |
|-----------------|---------------------------------------------------|
| Incident        | `Printer – Offline – Lab-Printer-01`              |
| Incident        | `Account – Locked – fin-jane.doe`                 |
| Incident        | `DNS – Cannot resolve intranet – Single user`     |
| Service Request | `Access – Add to Marketing share – mkt-emma.wilson` |
| Service Request | `Printer – Deploy Lab-Printer-01 – Marketing OU`  |
| Problem         | `Lockouts – Recurring after password change – Finance` |

**Avoid**
- Vague titles (`General issue`, `Computer problem`)
- Overly long technical strings
- User language only (`My printer doesn’t work`)

---

## 5. Priority

Use a simple 4-level scale (Impact × Urgency):

| Priority | Label     | Typical Use                              |
|----------|-----------|------------------------------------------|
| P1       | Critical  | Multiple users / business-critical service down |
| P2       | High      | Single user blocked from core work       |
| P3       | Medium    | Degraded service or non-urgent issue     |
| P4       | Low       | Request or minor inconvenience           |

---

## 6. Tags (Optional)

Use `snake_case`. Combine a high-level tag with a specific reason when helpful.

Examples:
- `printer_offline`
- `account_lockout`
- `dns_resolution`
- `permission_denied`
- `gpo_not_applying`
- `stale_credentials`

---

## 7. User Account Naming

| Role / Department      | Format                          | Example                |
|------------------------|---------------------------------|------------------------|
| Finance                | `fin-firstname.lastname`        | `fin-jane.doe`         |
| Marketing              | `mkt-firstname.lastname`        | `mkt-emma.wilson`      |
| Help Desk Tier 1       | `hd-firstname.lastname`         | `hd-john.smith`        |
| Help Desk Tier 2       | `hd-firstname.lastname`         | `hd-sarah.lee`         |
| Network Technician     | `net-firstname.lastname`        | `net-mike.chen`        |
| Privileged Admin       | `firstname.lastname.admin`      | `alex.carter.admin`    |
| Contractor             | `contractorXX`                  | `contractor01`         |

---

## 8. Group Naming (AGDLP)

| Type                    | Prefix | Example                        |
|-------------------------|--------|--------------------------------|
| Global Role Group       | `GG-`  | `GG-HelpDesk-T1`               |
|                         |        | `GG-Marketing`                 |
|                         |        | `GG-ITAdmins`                  |
| Domain Local Access Group | `DL-` | `DL-AD-User-Reset`             |
|                         |        | `DL-Marketing-Share-Modify`    |
|                         |        | `DL-Printer-Lab-01-Manage`     |

---

## 9. Printer Naming (Mocked Print Server)

| Element          | Convention                          | Example                  |
|------------------|-------------------------------------|--------------------------|
| Printer Name     | `Lab-Printer-XX`                    | `Lab-Printer-01`         |
| Share Name       | Same as printer name                | `Lab-Printer-01`         |
| Location         | Simple lab description              | `Building A – Floor 1`   |
| Comment          | Always note it is mocked            | `Mocked printer – practice only` |

---

## 10. Screenshot Evidence Naming

Inside each ticket folder under `04-Screenshots-Evidence/T1-XXX-YYY/`:
- 01-initial-error.png
- 02-diagnosis-step.png
- 03-resolution.png
- 04-verification.png


Use zero-padded numbers and short descriptive names so the sequence is obvious.

---

## 11. Quick Reference – Ticket Header Fields

When creating any ticket, fill these fields consistently:

| Field           | Convention / Source                     | Example                              |
|-----------------|------------------------------------------|-------------------------------------|
| **Ticket ID**   | `T1-<CODE>-<NUMBER>`                    | `T1-PRN-004`                         |
| **Type**        | One of the 4 ITIL types                 | `Incident`                           |
| **Category**    | From the taxonomy above                 | `Devices`                            |
| **Subcategory** | Second level                            | `Printer`                            |
| **Subject**     | `Component – Symptom – Scope`           | `Printer – Offline – Lab-Printer-01 `|
| **Priority**    | P1–P4                                   | `P3 – Medium`                        |
| **Tags**        | Optional `snake_case`                   | `printer_offline`                    |

---

**Core principle:**  
Classify the ticket correctly at the moment it is created. Type, Category, and Subcategory drive routing, reporting, and future searchability.

