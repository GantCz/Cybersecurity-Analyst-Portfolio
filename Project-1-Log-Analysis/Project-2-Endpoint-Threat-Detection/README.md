
# Project 2: Endpoint Compromise Investigation & Threat Eradication

## 📜 Executive Summary
This project simulates an Endpoint Detection and Response (EDR) triage scenario following a high-severity alert indicating suspicious background process behavior on a critical enterprise endpoint. Operating as an Incident Responder, I conducted live system forensics to locate unauthorized persistent files, isolated Indicators of Compromise (IoCs), and followed standard containment and eradication procedures to cleanly remove the threat from the environment.

## 🛠️ Tools & Environments Used
* **Operating System:** Kali Linux Environment
* **Forensic Focus Areas:** Active Process Trees, Socket Configurations, Cryptographic File Hashes
* **Command Line Utilities:** `ps`, `netstat`, `sha256sum`, `kill`, `rm`

---

## 🔬 Step-by-Step Walkthrough

### Phase 1: Triaging the Live System
Upon receiving a simulated endpoint compromise alert, I initiated live system triage forensics to identify running processes hiding in the volatile memory space or executing from unusual temporary paths.


1. Generated a comprehensive active background processing tree to look for binary execution anomalies:
   ```bash
   ps auxf
   ```
   (Screenshot here)

2. Analyze active network connections linked to unknown running processes to detect unauthorized outbound Command and Control (C2) communication:
  ```bash
netstat -tulnp
```
(Screenshot here)

### Phase 2: Isolating and Hashing the Artifact (IoC)
After tracking down the unauthorized binary running out of a user's hidden workspace directory, I isolated to compute its unique cryptographic footprint (hash), establishing an actionable Indicator of Compromise (IoC).
```bash
sha256sum /poath/to/suspect_binary
```

### Phase 3: Containment, Eradication, and Cleanup
Following identification, I executed containment steps to prevent the binary from continuing to execute code or communicate outwards.

1. Forcibly killed the active malicious process tree by its specific Process ID (PID):
```bash
sudo kill -9 [Process_ID]
```
(Screenshot here)

2. Removed the local persistence file from the directory structure and cleared temporary cache runtimes to complete eradication.
```bash
sudo rm /path/to/suspect_binary
```

## 📊 Defensive Takeaways
* **Defense-in-Depth Configuration:** An unprivileged user or external entity should never be allowed to execute unsigned binaries within a standard corporate workspace environment. This lab emphasizes the critical necessity of endpoint enforcement rules, such as AppLocker or Windows Defender Application Control (WDAC).
* **Incident Response Alignmemt:** This playbook execution mapped precisely to the NIST SP 800-61 r2 lifecycle (Containment, Eradication, and Recovery), minimizing overall enterprise risk exposure and ensuring zero persistence.
  
