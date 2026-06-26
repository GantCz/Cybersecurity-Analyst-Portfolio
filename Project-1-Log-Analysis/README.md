# Project 1: Firewall Log Analysis & Brute-Force Attack Mitigation

## 📜 Executive Summary
In this project, I acted as a Security Analyst to investigate a spike in authentication alerts targeting an enterprise Linux server. 
By parsing and analyzing raw firewall and authentication logs (`/var/log/auth.log`), I isolated a distributed SSH brute-force attack vector, 
  identified malicious IP addresses, and implemented active network security controls to block and mitigate the threat in real time.

## 🛠️ Tools & Environments Used
* **Operating System:** Linux (Kali / Ubuntu)
* **Log Types Analyzed:** System Authentication Logs (`auth.log`)
* **Command Line Utilities:** `grep`, `awk`, `uniq`, `sort`, `wc`, `iptables`

---

## 🔬 Step-by-Step Walkthrough

### Phase 1: Identifying the Anomaly
Upon receiving automated alerts indicating high authentication failure rates, I navigated to the system log directory to check for unauthorized access attempts.

1. Checked total failed login attempts to determine the scope of the event:
   ```bash
   grep "Failed password" /var/log/auth.log | wc -l
   ```
(Screenshot here)
   
### Phase 2: Extracting Attacker Infrastructure (IoCs)
To understand who was attacking the system, I utilized Linux text-processing commands to extract, count, and sort the unique IP addresses responsible for the failed attempts.

  ``` bash
  grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}' | sort | uniq -c | sort -nr
```
(Screenshot here)

### Phase 3: Active Ingredient Mitigation
To prevent account takeover, I utilized the built-in Linux host firewall (iptables) to create a rule blocking the primary offending IP address from establishing any future network handshakes.
```bash
sudo iptables -A INPUT -s [Attacker_IP] -j DROP
```
(Screenshot here)

## 📊 Defensive Takeaways & Incident Review
* **Log Retention Strategy:** Manual analysis highlights the importance of Centralized Log Management (SIEM). In an enterprise network, these logs are aggregated to map patterns globally.
* **Control Improvements:** Moving forward, I recommended implementing `Fail2Ban` for automated IP ban triggers, disabling password-based SSH authentication entirely, and enforcing SSH Key authorization.
* 1. Deploy an automated intrusion prevention framework such as 'Fail2Ban' to dynamically jail aggressive IPs.
  2. Modify `/etc/ssh/sshd_config` to disable password-based authentication entirely.
  3. Enforce public-private SSH Key authentication restricted by centralized IAM policies.
