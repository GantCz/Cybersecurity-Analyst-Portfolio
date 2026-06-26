# Project 5: Governance, Risk, and Compliance (GRC) Assessment

## 📜 Executive Summary
In this capstone project, I acted as a GRC Security Analyst to perform a comprehensive gap analysis for "XYZ Company" I evaluated their current operational cybersecurity controls against the 
**NIST Cybersecurity Framework (CSF 2.0)**,mapped critical administrative and technical deficiencies, and authored an Executive Remediation Roadmap to align the business with industry compliance standards.

## 🛠️ Frameworks & Tools Used
* **Framework Standard:** NIST Cybersecurity Framework (CSF 2.0)
* **Core Methodologies:** Gap Analysis, Risk Assessment, Strategy Planning
* **Documentation:** Markdown formatting

---

## 🔬 Gap Analysis & NIST Alignment

I analyzed four major operational areas where the organization fell short of regulatory standards:

### 1. Asset Management (NIST ID.AM)
* **The Gap:** Enterprise hardware assets were being tracked manually via a static Excel spreadsheet.
* **The Risk:** High risk of human error, lack of dynamic visibility, and extreme vulnerability to "rogue devices" entering the corporate network undetected.
*   If an asset is untracked, it cannot be monitored or scanned for vulnerabilities.
* **Remediation:** Transition away from manual tracking and deploy an automated network asset discovery tool to dynamically maintain a real-time inventory.

### 2. Access Control & Identity (NIST PR.AA)
* **The Gap:** Multi-Factor Authentication (MFA) was mandatory for remote users but entirely optional for employees working inside the physical office.
* **The Risk:** Severe violation of **Zero Trust Architecture ("Never Trust, Always Verify")**. If a threat actor breaches the physical security perimeter or compromises an internal office endpoint,
*    they can move laterally across the network without encountering authentication barriers.
* **Remediation:** Enforce a global conditional access policy mandating MFA for all authentication requests, regardless of network origin.

### 3. Vulnerability Management (NIST PR.IP)
* **The Gap:** Server vulnerability scans occurred only once per quarter, with a 30-day remediation window for critical vulnerabilities.
* **The Risk:** Prolonged exploit windows. Threat actors weaponize publicly disclosed vulnerabilities within hours. A 30-day delay allows a clear path for corporate data breaches or backdoor installations.
* **Remediation:** Increase vulnerability scanning cadence to a weekly schedule and implement a strict Service Level Agreement (SLA) requiring critical flaws to be patched within 7 to 14 days.

### 4. Incident Response Planning (NIST RS.RP)
* **The Gap:** The SOC team responded to threats using unwritten "tribal knowledge" and informal verbal arrangements.
* **The Risk:** Severe operational disarray during a crisis (such as a ransomware outbreak). Lack of formalized documentation leads to communication breakdowns,
*    legal/compliance failure, and potential destruction of critical forensic evidence.
* **Remediation:** Formalize, document, and test a comprehensive Incident Response Plan (IRP) with explicit escalation pathways, and secure executive sign-off.

---

## 🏁 Executive Roadmap Summary
By translating these four technical and operational deficiencies into quantifiable business risks, I compiled a formalized remediation timeline for senior leadership. 
This ensure the business balances operational speed with robust defensive security posture as mandated by modern regulatory environments.
