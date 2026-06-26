---

### 📂 Project 2 Template: Endpoint Threat Detection & IR

# Project 2: Endpoint Compromise Investigation & Threat Eradication

## 📜 Executive Summary
This project simulates an Endpoint Detection and Response (EDR) investigation following a high-severity alert indicating a potential malicious binary execution on a corporate workplace asset. I conducted live system forensics to locate unauthorized persistent files, isolated Indicators of Compromise (IoCs), and followed standard eradication procedures to cleanly remove the threat from the environment.

## 🛠️ Tools & Environments Used
* **Operating System:** Tart Linux Environment
* **Forensic Tooling:** System Process Monitors, File Hashes (MD5/SHA256)
* **Concepts:** Indicators of Compromise (IoCs), Process Hiding, Malicious Persistence

---

## 🔬 Step-by-Step Walkthrough

### Phase 1: Triaging the Live System
I initiated system triage by tracking running processes to find anomalies (such as processes running from temporary directories or utilizing unusual system ports).

1. Generated active background processing trees:
   ```bash
   ps auxf
   ```
   (Screenshot here)

2. Analyze active network connections linked to unknown processes to identify potential Command and Control (C2) communication:
  ```bash
netstat -tulnp
```
(Screenshot here)

### Phase 2: Isolating and Hashing the Artifact
After tracking down the unauthorized binary running out of a user's hidden directory, I isolated the file to create a cryptographic footprint (hash) to pivot into global security threat intelligence feeds.
```bash
sha256sum /poath/to/suspect_binary
```

### Phase 3: Eradication and Cleanup
Following identification, I executed containment steps to prevent the binary from continuing to execute code or communicate outwards.

1. Terminated the active malicious process tree:
```bash
sudo kill -9 [Process_ID]
```
(Screenshot here)

2. Removed the local persistence file and cleared temporary system runtime directories.

## 📊 Defensive Takeaways
* **Defense-in-Depth:** An attacker should never be able to execute an unsigned binary inside a standard corporate environment. This lab underscores the necessity of AppLocker or Application Whitelisting policies.
* **Incident Response Playbook:** This investigation followed standard containment and eradication lifecycles to minimize enterprise disruption.
  
