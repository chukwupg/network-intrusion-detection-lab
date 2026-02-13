# Shared Attack Timeline (Phase 2)

This timeline documents attacker-side activity for correlation with defender alerts in Phase 3.

| Timestamp WAT (Approx.) | Action | Tool |
|---------------------|--------|------|
| T+03:51 | Network connectivity validation | ping | 
| T+03:52 | Baseline web request | curl |
| T+12:54 | Full TCP SYN scan | nmap |
| T+12:58 | Service version detection | nmap |
| T+13:25 | SSH credential attack initiated | hydra |
| T+13:27 | Multiple SSH authentication failures | hydra |
| T+13:42 | Web enumeration of invalid paths | curl |
| T+13:55 | Attack traffic capture stopped | tcpdump |

Timestamps are approximate and intended for high-level correlation with IDS alerts and server logs.
