# Defender Setup Summary

This document provides a summary of the defender environment setup, including objectives, environment status, and readiness for Phase 2 activities.

---

## Objective Statement

The purpose of this setup is to create a controlled lab environment that simulates a real-world network with the following goals:

1. Deploy a **Victim Server** with common services (SSH, Apache2, DNS) for monitoring and testing.
2. Configure an **IDS Sensor (Suricata)** to monitor traffic on the same network as the victim.
3. Enable logging and analysis capabilities for studying attacks, traffic patterns, and defensive measures.
4. Prepare the environment for **Phase 2**, which will focus on active reconnaisance, active simulation, and traffic analysis.

This phase focused exclusively on defender-side preparation and validation. No attacker activity was analyzed or correlated at this stage.


---

## Environment Status

| Component          | Status               | Notes                                                                 |
|-------------------|--------------------|----------------------------------------------------------------------|
| Victim Server      | Configured & Running | Services enabled: SSH, Apache2, DNS; static IP: 192.168.8.100        |
| IDS Sensor (Suricata) | Configured & Running | Monitors subnet 192.168.8.0/24; ET Open rules loaded; logs enabled   |
| Network            | Operational         | Bridged adapter; subnet 192.168.8.0/24; default gateway 192.168.8.1   |
| Logging            | Verified            | SSH, Apache, and Suricata logs configured and accessible             |
| Snapshots          | Created             | Base snapshot saved for rollback before Phase 2               |

(Attacker system intentionally excluded from this phase)

---

## Victim Server Status

### Services Enabled
- DNS (Port 53)
- SSH (Port 22)
- HTTP (Port 80 – Apache)

These services were intentionally left minimally hardened to simulate a realistic enterprise exposure surface.

### Logging
The following logs were verified and confirmed active:
- `/var/log/auth.log` – Authentication events
- `/var/log/apache2/access.log` - Web access events
- `/var/log/apache2/error.log` -  Server errors, crashes, and misconfigurations.

---

## IDS Sensor Status

### IDS Platform
- Tool: Suricata
- Mode: IDS (passive monitoring)

### Configuration
- Monitoring interface connected to the Internal Network
- Emerging Threats Open ruleset enabled via `suricata-update`

### Validation
Suricata configuration was validated using:
```bash
suricata -T -c /etc/suricata/suricata.yaml
````
The IDS service was confirmed running successfully.

## Evidence Collected
The following artifacts were captured during this phase:
- VirtualBox network configuration screenshots
- Victim server service status screenshots
- IDS installation and configuration validation screenshots
- Confirmation of Suricata log generation (eve.json)
All screenshots are stored in the screenshots/ directory.

---

## Snapshot 

A snapshot of the fully configured lab environment has been taken to ensure reproducibility and quick restoration. This snapshot represents the frozen baseline environment prior to attacker execution.

- Snapshot Name: `pre-attack-clean-state`
- Date: 2026-02-09
- Components included: Victim Server, IDS Sensor, network configuration

---

## Transition to Phase 2

With the environment fully configured, validated, and backed-up (snapshot taken):

- Phase 2 can begin with confidence.
- Activities in Phase 2 will include:
  - Simulated attack traffic generation
  - Advanced network traffic analysis
  - IOC extraction
  - Reporting
  
The lab is now ready for hands-on testing and monitoring.

---