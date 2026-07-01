# Project 1b : Windows AD Authentication Auditing & Lockout Policy

## 🔬 Lab Environment

* **Target System:** Windows Server 2022 (Domain Controller)
* **Role:** Domain Controller / Identity Infrastructure
* **Tools Used:** Windows Event Viewer, PowerShell, Local Security Policy Editor
* **Security Context:** Hardening identity services against brute-force attacks.

## 📜 Executive Summary

In this project, I investigated the visibility of authentication attempts on a Windows Domain Controller. By analyzing Windows Security Event Logs, I identified failed login attempts and subsequently configured Group Policy Objects (GPOs) to implement an account lockout threshold, effectively mitigating automated brute-force vectors.

## 🛠️ Step-by-Step Walkthrough
### Phase 1: Identifying the Anomaly (Event ID 4625)
Unlike Linux /var/log/auth.log, Windows tracks authentication in the Security Event Log.
1. Generate Test Data: Use an incorrect password to attempt a login to a domain-joined machine.
2. Locate the Logs: Open Event Viewer $\rightarrow$ Windows Logs $\rightarrow$ Security.
3. **Filter for Failures:** Filter the log for Event ID 4625 (An account failed to log on).
  Note: This is the Windows equivalent of the Linux "Failed password" grep.
(Screenshot: Show the Event Viewer filtered for 4625)

### Phase 2: Analyzing Attempt Patterns (PowerShell)
To act like a professional analyst, use PowerShell to parse these logs instead of clicking through the GUI.
1. Run this command as Administrator to find the total count of failed attempts:
```powershell
Get-WinEvent -FilterHashtable @{LogName='Security'; ID=4625} | Measure-Object | Select-Object -ExpandProperty Count
```


2. Extract the IP addresses from the events to see where the "attack" is originating.
(Screenshot: Show the output of the PowerShell command)

### Phase 3: Mitigation (Account Lockout Policy)
To stop brute force, we don't just "block" the IP (like we did with iptables in Linux); we enforce a Lockout Policy so the account becomes useless to the attacker.
1. Open Group Policy Management (gpmc.msc).
2. Navigate to Default Domain Policy $\rightarrow$ Computer Configuration $\rightarrow$ Policies $\rightarrow$ Windows Settings $\rightarrow$ Security Settings $\rightarrow$ Account Policies $\rightarrow$ Account Lockout Policy.
3. Set the Account lockout threshold to 5 invalid attempts.

## 📊 Defensive Takeaways & Incident Review
* **Linux vs. Windows:** In Linux, mitigation is often network-based (blocking IPs via iptables). In Windows AD, mitigation is identity-based (locking accounts via GPO).
* **Visibility:** Real-world SOC analysts rely on Event ID 4625. Understanding this ID is a core competency for any Windows security role.
* **Future Improvement:** Implement Account Lockout Duration settings to ensure that after a brute-force attempt, the account is locked long enough to allow an analyst to investigate the alert.

