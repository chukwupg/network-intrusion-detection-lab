# Suricata fast.log Alert Summary

## Log Source
/var/log/suricata/fast.log

## Analyzed Source IP
192.168.8.190

---

# Alert Breakdown

## Reconnaissance Alerts

| Timestamp | Signature | Priority | Destination Port |
|------------|------------|------------|------------------|
| 11:54:06   | ET SCAN Suspicious inbound to mySQL | 2 | 3306 |
| 11:54:14   | ET SCAN Potential VNC Scan | 2 | 5819 |
| 11:54:26   | ET SCAN Suspicious inbound to Oracle SQL | 2 | 1521
| 11:54:30   | ET SCAN Suspicious inbound to MSSQL port | 2 | 1433 |
| 11:54:37   | ET SCAN Suspicious inbound to PostgreSQL | 2 | 5432 |
| 11:58:23	 | ET SCAN Nmap Scripting Engine User-Agent Detected | 1 | 80
| 11:58:23   | Possible Nmap User-Agent Observed | 1 | 80 |

---

## SSH-Related Alerts

| Timestamp | Signature | Priority | Destination Port |
|------------|------------|------------|------------------|
| 12:25:37 | ET SCAN Potential SSH Scan | 2 | 22 |
| 12:26:06 | ET SCAN Potential SSH Scan OUTBOUND | 1 | 22 |

---

## Web Enumeration

| Timestamp | Signature | Priority | Destination Port |
|------------|------------|------------|------------------|
| 12:42:38 | ET HUNTING curl User-Agent to Dotted Quad | 2 | 80 |

---

## Alert Classification Overview

| Classification | Count | Notes |
|----------------|------|-------|
| Attempted Information Leak | 10+ | Related to network scanning |
| Attempted Information Leak | Multiple count | Related to SSH brute-force |
| Potentially Bad Traffic | 2+ | Related to web enumeration |

---

# Observations

- All alerts originated from a single source IP (198.168.8.190).
- Priority 1 & 2 alerts were primarily reconnaissance-related.
- Priority 2 alerts were associated with SSH brute-force behavior.
- Priority 2 alerts were related to web enumeration.
- No false positives identified during this analysis window.

---

# Notes

fast.log provided sufficient visibility for manual SOC investigation.  
Structured correlation was achieved by matching:

- Source IP
- Timestamp proximity
- Destination port
- Signature context

This confirms IDS operational effectiveness during the simulated attack window.
