# Detection Effectiveness Report

## Data Sources
- Suricata IDS (`fast.log`)
- Host SSH logs (`/var/log/auth.log`)
- Host Apache logs (`/var/log/apache2/access.log`)
- Attacker timeline (`correlation/shared-timeline.md`)

---

# 1. Detection Assessment by Activity

| Activity Type | Detected by IDS | Detected by Host Logs | Confidence | Notes |
|---------------|----------------|---------------------|------------|-------|
| ICMP Probe | Yes | N/A | High | Network-layer detection only |
| Nmap Scan | Yes | No | High | IDS signatures triggered SYN scan detection |
| SSH Brute Force (Hydra) | Yes | Yes | Very High | Both network and host logs confirm attack |
| Web Enumeration | Yes | Yes | High | Some IDS coverage and host 404 logs confirm activity |

---

# 2. Summary

- IDS (`fast.log`) successfully detected reconnaissance and brute-force attempts.
- Host logs provide confirmation for authentication and web-related events.
- No false positives observed within the analysis window.
- Priority 1 & 2 alerts corresponded to reconnaissance activity.
- Priority 2 alerts corresponded to high-risk SSH attacks.

---

# 3. Conclusion

The layered detection approach was effective.  
Network IDS captured scanning and brute-force attempts, while host-level logs confirmed attack impact.  
The detection coverage is sufficient to track attacker activity and inform incident response actions.
