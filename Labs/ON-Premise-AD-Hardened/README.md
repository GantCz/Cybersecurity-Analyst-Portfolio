# Foundational Lab: On-Premises AD & Identity Security 

## 📁 Executive Summary
This project serves as the foundational infrastructure for my Security Operations Center (SOC) simulation suite. By virtualizing a hardened Windows Server 2022 instance, I have created a controlled environment to practice Active Directory Domain Services (AD DS) administration, identity monitoring, and incident response within a simulated on-premises enterprise network.

## Architecture & Design
* **Hypervisor:** VMWare Workstation (Deployed on physical host)
* **Operating System:** Windows Server 2022 Standard (Desktop Experience)
* **Connectivity:** Tailscale (WireGuard-based mesh VPN) for secure, zero-trust remote management
* **Network Flow:** Remote MacBook <-> Tailscale Mesh <-> Window Server VM

## 🔒 Security Implementation (Hardening)
* **Zero-Trust Access:** Eliminated public-facing port forwarding: Utilized Tailscale for encrypted, authenticated access
* **Surface Hardening:** Minimized attack surface by disabling unnecessary services and features within the Server OS.
* **Access Control:** Configured RDP access restrictions and implemented strict local user policy management.

## 🚀 Skills Demonstrated
* **AD DS Management:** Domain Controller provisioning and OU/User Management
* **Infrastructure as Code (IaC) Mindset:** Documentation of manual build processes to ensure reproducibility
* **Secure Remote Access:** Implementation of VPN/Mesh networking for secure lab management
* **Virtualization:** Configuration of host-guest network interfaces and resource allocation.
 
## 🧪 Lab Roadmap (Future Integration)
Planned integrations include:
 1. SIEM log ingestion for centralized monitoring
 2. simulated credential harvesting for incident response testing
 3. automated vulnerability scanning of the AD domain
  
