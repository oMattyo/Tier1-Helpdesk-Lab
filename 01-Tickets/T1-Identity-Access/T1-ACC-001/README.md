**Ticket ID:** T1-ACC-001  
**Type:** Incident  
**Category / Subcategory:** Access / Password Reset  
**Subject:** Account – Locked – fin-jane.doe  
**Priority:** P3 – Medium  
**Reported by:** fin-jane.doe  
**Date:** [11/04/26]  
**Technician:** hd-john.smith (Tier 1)

### Description
User reported inability to log on. Message indicated the account was locked.

**Evidence related to this section:**
- '01-initial-error-locked-out-screen.png'
- '01-initial-error-powershell.png'

### Initial Diagnosis
- Logged on as hd-john.smith (Tier 1 Help Desk).
- Confirmed via Active Directory Users and Computers that the account fin-jane.doe was locked.
- Confirmed with PowerShell: 
  - Get-ADUser -Identity "fin-jane.doe" -Properties LockedOut, Enabled, lockoutTime | Select-Object Name, LockedOut, Enabled, lockoutTime
- Confirmed in Event Viewer (Security log) with Event ID 4740 (account lockout)

**Evidence related to this section:**
- '02-diagnosis-account-locked-aduc.png'
- '02-diagnosis-account-locked-powershell.png'
- '02-diagnosis-eventviewer-lockout.png'

### Steps Taken
1. Logged on as hd-john.smith (Tier 1).
2. Confirmed account lockout via GUI, PowerShell, and Event Viewer (ID 4740)
3. Reset password and forced change at next login.
4. Unlocked the account.
5. Confirmed unlock and password reset events in Event Viewer (Event IDs 4767 and 4724).

**Evidence related to this section:**
- '03-resolution-password-reset-aduc.png'
- '03-resolution-eventviewer-account-unlock.png'
- '03-resolution-eventviewer-password-reset.png'

### Root Cause
Account lockout was caused by multiple failed logon attempts.

### Resolution
- Account Unlocked
- Password reset to temporary value.
- User required to change password at next logon.

### Verification
- User successfully logged on and changed password.
- Negative test confirmed: hd-john.smith cannot reset passwords for other Help Desk accounts or privileged user accounts.

**Evidence related to this section:**
- '04-verification-password-reset-prompt.png'
- '04-verification-password-reset-succeeded.png'
- '04-verification-negative-test-privileged.png'
- '04-verification-negative-test-helpdesk.png'

### Knowledge Base
Will link to: [02-Knowledge-Base/Identity-Access/Password-Reset-and-Unlock.md](../../../02-Knowledge-Base/Identity-Access/Password-Reset-and-Unlock.md)

### Evidence
All screenshots for this ticket are stored in:  
[04-Screenshots-Evidence/T1-ACC-001/](../../../04-Screenshots-Evidence/T1-ACC-001/)

