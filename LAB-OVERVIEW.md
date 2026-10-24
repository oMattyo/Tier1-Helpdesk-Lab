# Lab Overview – Tier 1 HelpDesk Environment

This document describes the complete Active Directory lab environment used in this portfolio.

---

## 1. Environment Summary

| Item                    | Value                          |
|-------------------------|--------------------------------|
| Domain Name             | `adlab.test`                   |
| Domain Controller       | DC01 (Windows Server 2025)     |
| Client Operating System | Windows 11 Pro                 |
| Functional Level        | Windows Server 2025            |
| Identity Model          | AGDLP                          |
| Help Desk Model         | Tier 1 + Tier 2                |
| Print Services          | Mocked Print Server on DC01    |

---

## 2. High-Level Architecture

The lab is built around these core layers:

- **Identity Layer** – Users, computers, and service accounts organized in a clear OU structure
- **Access Control Layer** – Global Role Groups + Domain Local Access Groups (AGDLP)
- **Resource Layer** – File shares and a mocked Print Server
- **Policy Layer** – Group Policy Objects linked to the correct OUs
- **Client Layer** – Domain-joined Windows 11 workstations

---

## 3. OU Structure
```
adlab.test
  ├── AD-Users
  │   ├── Employees
  │   │   ├── Finance
  │   │   └── Marketing
  │   ├── Contractors
  │   └── IT
  │       ├── HelpDesk
  │       └── NetworkTechnicians
  ├── AD-PrivilegedUsers
  │   └── ITAdmins
  ├── AD-Computers
  │   ├── Workstations
  │   └── Servers
  ├── AD-ServiceAccounts
  └── AD-Groups
      ├── RoleGroups
      │   ├── StandardRoles
      │   ├── ITRoles
      │   └── PrivilegedRoles
      └── AccessGroups
          ├── Delegation
          └── ResourceAccess
```

**Design notes**
- Privileged accounts are deliberately separated from normal users.
- Role groups and access groups are kept in different OUs for clear delegation boundaries.
- Domain Controllers remain in the built-in Domain Controllers OU.

---

## 4. Security Model (AGDLP)

Every permission follows this chain:
Account -> Global Role Group (GG-) -> Domain Local Access Group (DL-) -> Permission -> Resource (OU, Share, or Printer)

**Examples**
- `hd-john.smith` → `GG-HelpDesk-T1` → `DL-AD-User-Reset` → Password reset rights on Employees + Contractors OUs
- `mkt-emma.wilson` → `GG-Marketing` → `DL-Marketing-Share-Modify` → Modify rights on the Marketing share

---

## 5. Key Role Groups

| Group                | Purpose                              |
|----------------------|--------------------------------------|
| GG-Employees         | All standard employees               |
| GG-Finance           | Finance department                   |
| GG-Marketing         | Marketing department                 |
| GG-Contractors       | Contractor accounts                  |
| GG-HelpDesk-T1       | Tier 1 Help Desk technicians         |
| GG-HelpDesk-T2       | Tier 2 Help Desk technicians         |
| GG-NetworkTechnicians| Network support staff                |
| GG-ITAdmins          | Highly privileged administrators     |

---

## 6. Key Access Groups (Delegation)

| Group                | Rights Granted                              | Scope                     |
|----------------------|---------------------------------------------|---------------------------|
| DL-AD-User-Reset     | Reset password, unlock account              | Employees + Contractors   |
| DL-AD-User-Status    | Enable / disable accounts                   | Employees                 |
| DL-AD-User-Modify    | Modify ordinary attributes                  | Employees                 |
| DL-AD-User-Create    | Create user accounts                        | Selected OUs              |
| DL-AD-User-Delete    | Delete user accounts                        | Selected OUs              |

---

## 7. File Shares

Example departmental shares hosted on DC01:

- `\\DC01\Marketing`
- `\\DC01\Finance`
- `\\DC01\HelpDesk`

Permissions are applied using Domain Local groups (never individual users).

---

## 8. Print Server (Mocked)

A non-functional Print Server is installed on DC01 for realistic practice.

| Item              | Value                              |
|-------------------|------------------------------------|
| Role              | Print and Document Services        |
| Shared Printer    | `Lab-Printer-01`                   |
| Purpose           | Practice sharing, GPO deployment, permissions, and troubleshooting |
| Status            | Intentionally non-functional       |

---

## 9. Group Policy

GPOs are linked according to OU boundaries. Examples:

- Employee baseline settings → linked to `AD-Users\Employees`
- Contractor restrictions → linked to `AD-Users\Contractors`
- Workstation settings → linked to `AD-Computers\Workstations`
- Printer deployment (optional) → targeted to specific OUs or groups

---

## 10. Canonical Test Accounts

| Account              | Role / Purpose                     |
|----------------------|------------------------------------|
| `hd-john.smith`      | Tier 1 Help Desk                   |
| `hd-sarah.lee`       | Tier 2 Help Desk                   |
| `fin-jane.doe`       | Finance employee                   |
| `mkt-emma.wilson`    | Marketing employee                 |
| `contractor01`       | Contractor                         |
| `net-mike.chen`      | Network technician                 |
| `alex.carter.admin`  | Privileged administrator           |

---

## 11. Design Principles

1. OUs define organization, policy, and delegation boundaries — not permissions.
2. All access follows the AGDLP model.
3. Privileged accounts and groups are isolated.
4. Least privilege is applied to Help Desk roles.
5. The Print Server exists only for skill practice and is non-functional by design.
6. Every change is documented so the environment remains auditable and teachable.
