# Incident Summary Report

## Incident Overview
- **Attacker Source IP:** 192.168.8.190
- **Attack Simulation Type:** Reconnaissance, SSH brute-force, and web enumeration
- **Victim Systems:** SSH service, Apache web server
- **Detection Method:** Suricata IDS (`fast.log`) and host logs (auth.log, access.log)

---

## Timeline Summary

| Time (UTC)| Attacker Action | Detected by IDS | Detected by Host Logs |
|------|----------------|----------------|---------------------|
| 02:51:27 | ICMP Probing | Yes | N/A |
| 11:54:06 | Nmap SYN Scan | Yes | No |
| 12:25:37 | SSH Brute Force | Yes | Yes |
| 12:42:38 | Web Enumeration | Yes | Yes |

---

## Detection Coverage

- **Network IDS:** Effective at detecting reconnaissance attacks, SSH brute-force, and web enumeration.
- **Host Logs:** Effective at confirming authentication failures and web enumeration
- **Gaps:** Some minor IDS coverage gaps for web enumeration, dependent on rule set.

---

## Impact Assessment

- No successful SSH login occurred (attacker blocked/failure captured and logged)
- No web content accessed outside intended paths (404 errors only)
- No host compromise occurred
- Simulated attack demonstrates network and host visibility

---

## Confidence

- High confidence in network scanning detection
- High confidence in SSH brute-force detection
- High confidence in web enumeration detection

---

## Notes

- All alerts and host logs correlated to a single attacker IP.
- This structured evidence supports incident reporting and future detection tuning.
- Phase 3 establishes a solid foundation for **Phase 4: Detection Engineering & Hardening**.
