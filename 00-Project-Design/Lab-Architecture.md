# Lab Architecture

## Domain
- Name: `adlab.test`
- Domain Controller: DC01 (Windows Server 2025)
- Functional level: Windows Server 2025

## Core Design Goals
1. Clear separation of identity types (normal users vs privileged)
2. Strict AGDLP model for every permission
3. Tiered Help Desk rights with least privilege
4. Group Policy boundaries that match OU structure
5. File shares that demonstrate Share + NTFS interaction
6. Mocked Print Server for realistic printer-related Help Desk practice

## High-Level Components
- Identity layer (Users + Groups)
- Access control layer (Domain Local groups + Delegation)
- Resource layer (File shares + shared printers)
- Policy layer (Group Policy – including printer deployment)
- Client layer (Windows 11 domain-joined workstations)
- Print layer (mocked Print Server on DC01)

## Print Server Design
- Installed on DC01 using the Print and Document Services role
- One or more shared printers created (e.g., `Lab-Printer-01`)
- Printers are **non-functional** (no physical device or real print queue required)
- Used for:
  - Sharing printers
  - Deploying printers via Group Policy
  - Setting printer permissions
  - Simulating common Tier-1 printer tickets (offline, access denied, driver issues, etc.)

## Why this design?
- Attempt to Mirror real MSP / small-to-medium-sized company AD environments
- Prevents classic beginner mistakes
- Makes troubleshooting logical (follow the AGDLP chain)
- Gives realistic practice with printers without needing hardware
