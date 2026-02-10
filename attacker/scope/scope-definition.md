# Phase 2 – Engagement Scope

This document defines the scope of activities permitted during Phase 2 of the lab, which focuses on attack simulation, and defensive analysis.

---

## Target

- **Primary Target IP**: `192.168.8.100`
- Represents the victim system under monitoring by the IDS sensor.

---

## In-Scope Ports

Only the following service ports are authorized for testing and traffic generation:

| Port | Service | Description                     |
|------|---------|---------------------------------|
| 22   | SSH     | Remote access service           |
| 80   | HTTP    | Web service (Apache)            |

---

## Out-of-Scope Activities

The following actions are explicitly prohibited:

- Denial of Service (DoS) or traffic flooding attacks  
- Exploitation of vulnerabilities  
- Privilege escalation attempts  
- Password brute-force attacks  
- Any activity that alters system integrity  

These restrictions ensure the focus remains on **detection and monitoring**, not compromise.

---

## Assumptions

- **No credentials** are provided or available.
- Engagement is conducted in **black-box mode**:
  - No internal knowledge of services or configurations.
  - All observations are based solely on network traffic and responses.
- Target system is assumed to be operational and reachable.

---

## Purpose

This scope is designed to:
- Generate realistic but controlled traffic
- Validate IDS detection capabilities
- Support log analysis and alert tuning
- Maintain ethical and technical boundaries within the lab

---

## Notes

Any testing outside this scope requires explicit modification of this document and environment approval.
