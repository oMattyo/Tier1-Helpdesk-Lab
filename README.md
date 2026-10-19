# Tier 1 Help Desk Lab - Active Directory Service Desk Portfolio

A complete, production-style Active Directory lab that simulates a real Tier 1 / Tier 2 Help Desk environment.

This repository documents a fully built Windows Server 2025 domain ('adlab.test') with a proper OU design, AGDLP security model, delegated administration, Group Policy, file shares, a mocked print server, and a structured ticketing + knowledge-base system.

The goal is to demonstrate **how a professional IT service desk works** - not just that I can reset a password.

---

## Lab Overview

| Component          | Details                                                             |
|---------------------|-----------------------------------------------------------------------|
| Domain             | 'adlab.test'                                                        |
| Domain Controller  | DC01 (Windows Server 2025)                                          |
| Client             | Windows 11 Pro (domain-joined)                                      |
| Identity Model     | AGDLP (Account->Global->Domain Local->Permission)                   |
| Help Desk Tiers    | T1 (password reset / unlock) T2 (status + modify)                   |
| Key Technologies   | Active Directory, DNS, DHCP, Group Policy, NTFS + Share permissions |

---

## Repository structure
Tier1-Helpdesk-Lab/
├── README.md                          ← You are here
├── LAB-OVERVIEW.md                    ← Full environment design
├── Ticketing-System-Guide.md          ← How tickets are handled
│
├── 00-Project-Design/                 ← Architecture & standards
│   ├── Network-Diagram.png
│   ├── Lab-Architecture.md
│   ├── Tech-Stack.md
│   └── Naming-Standards.md
│
├── 01-Tickets/                        ← Simulated work history
│   ├── T1-Identity-Access/
│   ├── T1-File-Access-Permissions/
│   ├── T1-Network-DNS-IP/
│   ├── T1-Devices-Printers-OS/
│   ├── T1-Software-Applications/
│   ├── T1-System-Diagnostics/
│   └── T1-GPO-Policies/
│
├── 02-Knowledge-Base/                 ← Reusable procedures
│   ├── Identity-Access/
│   ├── File-Access/
│   ├── Network/
│   ├── Devices/
│   ├── Software/
│   ├── Diagnostics/
│   └── GPO/
│
├── 03-Mini-Shifts/                    ← Multi-ticket workload simulation
├── 04-Screenshots-Evidence/           ← Audit-style proof per ticket
├── 05-Templates/                      ← Standardized forms
└── 06-Reports-Analytics/              ← Volume & trend analysis


---

## What This Lab Demonstrates

- **Proper Active Directory design**  
  Clean OU structure that separates Users, Privileged accounts, Computers, Service Accounts, and Groups.

- **Enterprise security model (AGDLP)**  
  Global Role Groups → Domain Local Access Groups → Permissions. No direct user permissions on resources.

- **Delegated administration**  
  Tier 1 can reset passwords and unlock accounts only in the correct OUs.  
  Tier 2 can enable/disable and modify attributes.  
  Privileged accounts and IT accounts are protected.

- **Real Help Desk workflow**  
  Structured tickets with diagnosis → root cause → resolution → verification → escalation decisions.

- **Knowledge management**  
  Every resolved issue produces a reusable Knowledge Base article.

- **Operational thinking**  
  Mini-shifts, ticket volume analysis, and SLA-style reporting.

---

## Key Design Principles

1. **OUs are for organization, policy, and delegation — not permissions.**
2. **Permissions always follow AGDLP.**
3. **Privileged accounts live in a separate OU and are never managed by Help Desk.**
4. **Every ticket is documented with evidence and root cause.**
5. **Knowledge Base articles are written so another technician can follow them.**

---

## How to Navigate

| Want to see…                    | Go to                                 |
|----------------------------------|----------------------------------------|
| Overall lab design              | `LAB-OVERVIEW.md`                       |
| Naming rules & ticket format    | `00-Project-Design/Naming-Standards.md` |
| Actual tickets I resolved       | `01-Tickets/`                           |
| Step-by-step fix procedures     | `02-Knowledge-Base/`                    |
| Screenshots that prove the work | `04-Screenshots-Evidence/`              |
| Templates I used                | `05-Templates/`                         | 

---

## Skills Demonstrated

- Active Directory administration & design
- AGDLP security model
- Delegation of Control
- Group Policy scoping and troubleshooting
- File share + NTFS permission design
- Structured troubleshooting methodology
- Professional documentation & knowledge management
- ITIL-aligned Incident / Request / Access / Problem thinking

---

## License

This is a personal portfolio project. Feel free to use the structure and templates for your own learning.
