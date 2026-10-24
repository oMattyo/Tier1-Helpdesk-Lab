# Ticketing System Guide

This document explains how tickets are handled in the Tier 1 HelpDesk Lab.

---

## 1. Ticket Types (ITIL)

| Type              | When to use                                      |
|-------------------|--------------------------------------------------|
| **Incident**      | Something is broken – restore service            |
| **Service Request** | User needs something (access, setup, etc.)     |
| **Problem**       | Investigating the root cause of recurring issues |
| **Change Request**| Planned modification (rarely used at Tier 1)     |

---

## 2. Priority Levels

| Priority | Label     | Typical Criteria                              |
|----------|-----------|-----------------------------------------------|
| P1       | Critical  | Multiple users or core service fully down     |
| P2       | High      | Single user blocked from primary work         |
| P3       | Medium    | Degraded service or important but not blocking|
| P4       | Low       | Minor issue or routine request                |

---

## 3. Standard Workflow

1. **Intake** – Capture Type, Category, Subcategory, Subject, and Priority
2. **Clarify** – Confirm symptoms and identity
3. **Diagnose** – Gather evidence before making changes
4. **Remediate** – Apply the fix (one change at a time when possible)
5. **Verify** – Confirm the issue is resolved
6. **Document** – Complete the ticket with root cause and resolution
7. **Knowledge** – Update or create a Knowledge Base article when useful
8. **Close** or **Escalate**

---

## 4. Escalation Guidelines

| Situation                                      | Action          |
|------------------------------------------------|-----------------|
| Password reset / unlock within scope           | Resolve at T1   |
| Simple permission or group membership change   | Resolve at T1   |
| Printer offline / basic connectivity           | Resolve at T1   |
| Requires changes to privileged accounts/groups | Escalate        |
| Requires new GPO or structural AD change       | Escalate        |
| Root cause unclear after reasonable effort     | Escalate        |

---

## 5. Documentation Standards

- Every ticket uses the Master Ticket Template
- Root cause must be stated clearly
- Evidence screenshots are stored in `04-Screenshots-Evidence/T1-XXX-YYY/`
- Related Knowledge Base articles are linked when available

---

## 6. Example Ticket Header

Ticket ID:     T1-PRN-004
Type:          Incident
Category:      Devices
Subcategory:   Printer
Priority:      P3 – Medium
Subject:       Printer – Offline – Lab-Printer-01
