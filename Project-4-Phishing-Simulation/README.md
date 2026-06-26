# Project 4: Phishing Simulation & Security Awareness Blueprint

## 📜 Executive Summary
In this project, I stepped into the role of a Security Awareness Program Lead to address a critical risk vector: social engineering.
I engineered three realistic phishing simulation pretexts (IT Urgent Update, HR Policy Change, and Cloud Document Sharing) targeting standard corporate workflows, 
deployed a local web server infrastructure to safely simulate credential harvesting, and constructed a definitive Security Operations Center (SOC) incident response triage playbook.

## 🛠️ Tools & Environments Used
* **Operating System:** Tart Kali Linux VM
* **Web Server Architecture:** Apache2
* **Languages & Configurations:** HTML5, CSS3, Linux File Permissions (`chmod`)
* **Concepts:** Pretexting, Social Engineering Metrics, Indicator Deception

---

## 🔬 Step-by-Step Walkthrough

### Phase 1: Pretext Engineering & Indicator Design
I designed three distinct corporate attack scenarios to test user susceptibility, embedding specific "Deception Indicators" into each vector:
1. **IT Urgent Password Reset:** Built a false sense of urgency utilizing a lookalike domain suffix (`services@company-support-security.com`).
2. **HR Policy Sign-Off:** Exploited organizational administrative authority regarding a mock remote work policy amendment.
3. **Cloud Document Share:** Mimicked standard cloud notification user interfaces to exploit daily business workflow habits.

### Phase 2: Deploying the Harvesting Infrastructure
To safely test the mechanics of a landing page without exposing data to the public internet, I configured and hosted the single sign-on (SSO) prompt locally using Apache.

1. Developed the portal front-ends inside `/var/www/html/login.html`.
2. Restructured the web directory access parameters (`chmod 644`) to guarantee the server daemon could cleanly process the inputs.
3. Initialized the system handler:
   ```bash
   sudo systemctl start apache2
   ```
   (Screenshot here)

### Phase 3: Campaign Testing & Verification
I verified the landing page infrastructure by navigating to the address http://127.0.0.1/login.html via a local Firefox browser instance. 
I interacted with the prompt by inputting mock test credentials (cloud_test@company.com) to simulate a campaign interaction and successfully validate the landing mechanics.

(Screenshot of active IT, HR, and Cloud login Page)

## )

📊 Defensive Takeaways & SOC Incident Playbook
To ensure simulation analytics drive actual defensive capability, I authored a triage playbook mapping out the SOC response when an end-user reports a suspicious lure:

Scope Identification: Querying corporate mail tenants to isolate all internal recipients of the lookalike sender domain.

Eradication: Executing administrative search-and-purge actions to instantly drop the email from all active mailboxes globally.

Infrastructure Controls: Sinkholing the target URL at the upstream DNS and proxy layer while revoking active user OAuth session tokens.
