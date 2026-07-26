# 🛡️ Red and Blue Team Lab: Network Intrusion and Detection Project

## 📌 Overview

This project demonstrates a full defensive security workflow:

- Attacker simulation
- IDS monitoring (Suricata)
- Host log analysis
- Event correlation
- Detection effectiveness reporting

The goal was to simulate real-world attack activity and perform structured SOC-style analysis using network and host telemetry.

---

# 🎯 Project Objectives

- Deploy and configure Suricata IDS
- Simulate realistic attacker activity
- Capture alerts in `fast.log`
- Correlate IDS alerts with host logs
- Produce professional SOC-style reports
- Evaluate detection coverage and effectiveness

---

# 🧪 Lab Environment

## Components

| Role | Technology |
|------|------------|
| Attacker | Kali Linux |
| Victim | Ubuntu Server |
| IDS | Suricata |
| Web Server | Apache2 |
| Log Sources | `fast.log`, `/var/log/auth.log`, `/var/log/apache2/access.log` |

---

## Tools Used
- VirtualBox
- Nmap
- Hydra
- Suricata

---

# 🚩 Phase 1 – Lab Setup

- Installed and configured Suricata on a dedicated Ubuntu server
- Enabled rule sets (Emerging Threats)
- Enabled promiscous mode on the network adapter to provide traffic visibility
- Verified logging to `fast.log`
- Deployed SSH and Apache services
- Validated network connectivity between attacker and victim

Artifacts:
- `defender/` defender artifacts
- `defender/ids/` Suricata setup

---

# 🔥 Phase 2 – Attack Simulation

Simulated real-world attacker behavior from Kali:

### Activities Performed

- ICMP reconnaissance
- Nmap SYN scan and service detection
- SSH brute-force using Hydra
- Web directory enumeration

Generated:
- Suricata alerts in `fast.log`
- SSH authentication failures in `/var/log/auth.log`
- Apache 404 logs in `/var/log/apache2/access.log`

Artifacts:
- `attacker/`

---

# 🧠 Phase 3 – Defender Analysis & Correlation

Performed structured SOC analysis using:

- Suricata `fast.log`
- SSH authentication logs (auth.log)
- Apache access logs (access.log)

### Analysis Completed

- Extracted IDS alerts
- Identified priority levels
- Correlated attacker IP across data sources
- Built unified attack timeline
- Evaluated detection coverage
- Produced incident summary report

Generated reports:

defender/analysis/<br>
├── alerts/<br>
│ ├── attacker-alerts.log<br>
│ ├── fast-original.log<br>
│ ├── recon-alerts.log<br>
│ └── ssh-alerts.log<br>
├── correlation/<br>
│ └── shared-timeline.md<br>
├── Logs/<br>
│ ├── auth-failures.log<br>
│ └── web-404.log<br>
└── findings/<br>
 ├── detection-effectiveness.md<br>
 └── incident-summary.md


---

# 📊 Key Findings

- SSH brute-force attempts successfully detected by both IDS and host logs
- Nmap reconnaissance detected by Suricata signatures
- Web enumeration confirmed via Apache logs
- No successful compromise occurred
- Layered detection provided high-confidence visibility

---

# 🧩 Skills Demonstrated

- Network Security Monitoring (NSM)
- IDS configuration and analysis (Suricata)
- Log correlation methodology
- Timeline reconstruction
- SOC reporting & documentation
- Threat detection validation

---

# 📈 Detection Coverage Assessment

| Attack Type | IDS | Host Logs | Confidence |
|-------------|-----|-----------|------------|
| Reconnaissance | ✅ | N/A | High |
| SSH Brute Force | ✅ | ✅ | Very High |
| Web Enumeration | ✅ | ✅ | High |

---

# 🗂 Project Structure

├── architecture<br>
│ └── ip-addressing.md<br>
├── attacker/<br>
│ ├── attacks/<br>
│ ├── findings/<br>
│ ├── pcaps/<br>
│ ├── reconnaissance/<br>
│ ├── scope/<br>
│ └── README.md<br>
├── defender/<br>
│ ├── analysis/<br>
│ ├── ids/<br>
│ └── victim-server/<br>
├── correlation/<br>
│ └── shared-timeline.md/<br>
└── README.md

---

# 🧠 What This Project Demonstrates

This lab simulates the full lifecycle of a detection-focused investigation:

1. Attack simulation
2. Alert generation
3. Log analysis
4. Correlation
5. Reporting
6. Detection validation

It showcases practical SOC workflow execution using open-source tooling.

---

# 📬 Author

👩‍💻 **Chukwu PraiseGod**  
Follow my journey: [X](https://x.com/chukwupg) | [LinkedIn](https://linkedin.com/in/chukwupg)  

---
