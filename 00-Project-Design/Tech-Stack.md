# Technology Stack

| Layer              | Technology                          | Purpose                                             |
|--------------------|-------------------------------------|--------------------------------------------------------|
| Domain Controller  | Windows Server 2025                 | AD DS, DNS, Group Policy, File Server, **Print Server** |
| Client OS          | Windows 11 Pro                      | Domain-joined end-user simulation                   |
| Directory          | Active Directory Domain Services    | Identity & access                                   |
| Name Resolution    | DNS (AD-integrated)                 | Hostname resolution                                 |
| Policy             | Group Policy                        | User & computer configuration + printer deployment  |
| File Services      | SMB File Shares + NTFS              | Departmental data access                            |
| Print Services     | Print and Document Services role    | **Mocked / non-functional** Print Server for practice   |
| Security Model     | AGDLP                               | Role → Access → Permission                          |
| Documentation      | Markdown + GitHub                   | Portfolio & knowledge base                          |

## Print Server Notes
- Role: Print and Document Services (Print Server only)
- Location: DC01
- Status: Mocked / non-functional (no real print hardware)
- Purpose: Practice sharing printers, deploying via GPO, managing permissions, and troubleshooting common Help Desk printer tickets
