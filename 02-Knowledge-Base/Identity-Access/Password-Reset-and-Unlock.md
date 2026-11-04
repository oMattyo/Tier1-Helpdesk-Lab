# Password Reset and Account Unlock (Tier 1)

## When to use
User cannot log on and reports account locked or forgotten password.

## Prerequisites
- Technician must be a member of GG-HelpDesk-T1 (or T2)
- Target account must be in AD-Users\Employees or AD-Users\Contractors

## Procedure (GUI)
1. Open Active Directory Users and Computers.
2. Locate the user.
3. Right-click → Reset Password.
4. Set temporary password.
5. Check “User must change password at next logon”.
6. Unlock the account if necessary.

## Procedure (PowerShell)
```powershell:
Unlock-ADAccount -Identity "username"

Set-ADAccountPassword -Identity "username" -Reset -NewPassword (ConvertTo-SecureString "TempPass123!" -AsPlainText -Force)

Set-ADUser -Identity "username" -ChangePasswordAtLogon $true
