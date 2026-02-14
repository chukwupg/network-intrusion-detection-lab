# Attack Correlation Report

## Data Sources
- Suricata IDS (`fast.log`)
- Victim SSH logs (`/var/log/auth.log`)
- Victim Apache logs (`/var/log/apache2/access.log`)
- Attacker timeline (`correlation/shared-timeline.md`)

## Attacker Source IP
192.168.8.190

---

# 1. Reconnaissance Activity 

## ICMP Probing

| Evidence Source | Observation |
|-----------------|------------|
| Attacker Timeline | ICMP connectivity validation |
| Suricata fast.log | ICMP-related scan alert |
| Host Logs | No host-level logging (expected for ICMP) |

ICMP Probing log entry (suricata):
02/13/2026-02:51:27.034226  [**] [1:2100366:8] GPL ICMP PING *NIX [**] [Classification: Misc activity] [Priority: 3] {ICMP} 192.168.8.190:8 -> 192.168.8.100:0
02/13/2026-02:51:27.034226  [**] [1:2100366:8] GPL ICMP PING *NIX [**] [Classification: Misc activity] [Priority: 3] {ICMP} 192.168.8.190:8 -> 192.168.8.100:0
02/13/2026-02:51:28.035487  [**] [1:2100366:8] GPL ICMP PING *NIX [**] [Classification: Misc activity] [Priority: 3] {ICMP} 192.168.8.190:8 -> 192.168.8.100:0
02/13/2026-02:51:28.035487  [**] [1:2100366:8] GPL ICMP PING *NIX [**] [Classification: Misc activity] [Priority: 3] {ICMP} 192.168.8.190:8 -> 192.168.8.100:0
02/13/2026-02:51:29.037446  [**] [1:2100366:8] GPL ICMP PING *NIX [**] [Classification: Misc activity] [Priority: 3] {ICMP} 192.168.8.190:8 -> 192.168.8.100:0
02/13/2026-02:51:29.037446  [**] [1:2100366:8] GPL ICMP PING *NIX [**] [Classification: Misc activity] [Priority: 3] {ICMP} 192.168.8.190:8 -> 192.168.8.100:0
02/13/2026-02:51:30.039223  [**] [1:2100366:8] GPL ICMP PING *NIX [**] [Classification: Misc activity] [Priority: 3] {ICMP} 192.168.8.190:8 -> 192.168.8.100:0
02/13/2026-02:51:30.039223  [**] [1:2100366:8] GPL ICMP PING *NIX [**] [Classification: Misc activity] [Priority: 3] {ICMP} 192.168.8.190:8 -> 192.168.8.100:0
02/13/2026-02:51:31.040483  [**] [1:2100366:8] GPL ICMP PING *NIX [**] [Classification: Misc activity] [Priority: 3] {ICMP} 192.168.8.190:8 -> 192.168.8.100:0
02/13/2026-02:51:31.040483  [**] [1:2100366:8] GPL ICMP PING *NIX [**] [Classification: Misc activity] [Priority: 3] {ICMP} 192.168.8.190:8 -> 192.168.8.100:0

**Assessment:**  
Reconnaissance activity detected at the network layer.  
No host-level artifacts expected for ICMP echo requests.

---

## Nmap SYN Scan

| Evidence Source | Observation |
|-----------------|------------|
| Attacker Timeline | Full TCP SYN scan initiated |
| Suricata fast.log | Scan-related signature triggered |
| Host Logs | No direct application-layer evidence |

Nmap Syn Scan log entry (suricata):
02/13/2026-11:54:06.694352  [**] [1:2010937:3] ET SCAN Suspicious inbound to mySQL port 3306 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.8.190:55165 -> 192.168.8.100:3306
02/13/2026-11:54:14.015512  [**] [1:2002910:6] ET SCAN Potential VNC Scan 5800-5820 [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} 192.168.8.190:55165 -> 192.168.8.100:5819
02/13/2026-11:54:26.970452  [**] [1:2010936:3] ET SCAN Suspicious inbound to Oracle SQL port 1521 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.8.190:55165 -> 192.168.8.100:1521
02/13/2026-11:54:30.011626  [**] [1:2010935:3] ET SCAN Suspicious inbound to MSSQL port 1433 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.8.190:55165 -> 192.168.8.100:1433
02/13/2026-11:54:37.840268  [**] [1:2010939:3] ET SCAN Suspicious inbound to PostgreSQL port 5432 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.8.190:55165 -> 192.168.8.100:5432
02/13/2026-11:58:23.117565  [**] [1:2009358:8] ET SCAN Nmap Scripting Engine User-Agent Detected (Nmap Scripting Engine) [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.8.190:54088 -> 192.168.8.100:80
02/13/2026-11:58:23.117565  [**] [1:2024364:5] ET SCAN Possible Nmap User-Agent Observed [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.8.190:54088 -> 192.168.8.100:80
02/13/2026-11:58:23.131286  [**] [1:2009358:8] ET SCAN Nmap Scripting Engine User-Agent Detected (Nmap Scripting Engine) [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.8.190:54110 -> 192.168.8.100:80
02/13/2026-11:58:23.131286  [**] [1:2024364:5] ET SCAN Possible Nmap User-Agent Observed [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.8.190:54110 -> 192.168.8.100:80
02/13/2026-11:58:23.131944  [**] [1:2009358:8] ET SCAN Nmap Scripting Engine User-Agent Detected (Nmap Scripting Engine) [**] [Classification: Web Application Attack] [Priority: 1] {TCP} 192.168.8.190:54100 -> 192.168.8.100:80

**Assessment:**  
Network-based IDS successfully detected port scanning behavior.  
Host-level logs did not capture this activity, which is expected.

---

# 2. SSH Brute Force Correlation 

| Evidence Source | Observation |
|-----------------|------------|
| Attacker Timeline | Hydra SSH brute-force initiated |
| Suricata fast.log | SSH brute-force / scan signature triggered |
| auth.log | Multiple "Failed password" entries from 192.168.8.190 |

auth.log entry:
2026-02-13T12:27:02.343946+00:00 infrastructure sshd[1317]: Failed password for root from 192.168.8.190 port 33372 ssh2
2026-02-13T12:27:03.350874+00:00 infrastructure sshd[1311]: Failed password for root from 192.168.8.190 port 50542 ssh2
2026-02-13T12:27:03.693582+00:00 infrastructure sshd[1313]: Failed password for root from 192.168.8.190 port 33348 ssh2
2026-02-13T12:27:03.840706+00:00 infrastructure sshd[1311]: error: maximum authentication attempts exceeded for root from 192.168.8.190 port 50542 ssh2 [preauth]
2026-02-13T12:27:03.842579+00:00 infrastructure sshd[1311]: Disconnecting authenticating user root 192.168.8.190 port 50542: Too many authentication failures [preauth]
2026-02-13T12:27:03.843151+00:00 infrastructure sshd[1311]: PAM 5 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.8.190  user=root
2026-02-13T12:27:03.853608+00:00 infrastructure sshd[1311]: PAM service(sshd) ignoring max retries; 6 > 3
2026-02-13T12:27:03.950923+00:00 infrastructure sshd[1319]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.8.190  user=root
2026-02-13T12:27:04.522867+00:00 infrastructure sshd[1315]: Failed password for root from 192.168.8.190 port 33356 ssh2
2026-02-13T12:27:05.992998+00:00 infrastructure sshd[1319]: Failed password for root from 192.168.8.190 port 58488 ssh2
2026-02-13T12:27:06.348319+00:00 infrastructure sshd[1313]: Failed password for root from 192.168.8.190 port 33348 ssh2
2026-02-13T12:27:06.505228+00:00 infrastructure sshd[1313]: Connection reset by authenticating user root 192.168.8.190 port 33348 [preauth]

fast.log entry (suricata)
attacker-alerts.log:02/13/2026-12:25:37.235438  [**] [1:2001219:20] ET SCAN Potential SSH Scan [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} 192.168.8.190:50396 -> 192.168.8.100:22
attacker-alerts.log:02/13/2026-12:25:37.235438  [**] [1:2003068:7] ET SCAN Potential SSH Scan OUTBOUND [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} 192.168.8.190:50396 -> 192.168.8.100:22
attacker-alerts.log:02/13/2026-12:26:06.899320  [**] [1:2003068:7] ET SCAN Potential SSH Scan OUTBOUND [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} 192.168.8.190:55224 -> 192.168.8.100:22
attacker-alerts.log:02/13/2026-12:26:25.399495  [**] [1:2003068:7] ET SCAN Potential SSH Scan OUTBOUND [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} 192.168.8.190:59082 -> 192.168.8.100:22
attacker-alerts.log:02/13/2026-12:26:43.611009  [**] [1:2003068:7] ET SCAN Potential SSH Scan OUTBOUND [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} 192.168.8.190:50536 -> 192.168.8.100:22

**Assessment:**  
SSH authentication abuse was detected at both the network and host level.  
Cross-validation confirms high-confidence detection.

---

# 3. Web Enumeration Correlation

| Evidence Source | Observation |
|-----------------|------------|
| Attacker Timeline | Invalid HTTP path requests via curl |
| Suricata fast.log | Web-related alert (if triggered) |
| Apache access.log | 404 responses for invalid paths |

access.log entry:
192.168.8.190 - - [13/Feb/2026:00:46:59 +0000] "GET /robots.txt HTTP/1.1" 404 455 "-" "Mozilla/5.0 (compatible; Nmap Scripting Engine; https://nmap.org/book/nse.html)"
192.168.8.190 - - [13/Feb/2026:00:46:59 +0000] "POST /sdk HTTP/1.1" 404 455 "-" "Mozilla/5.0 (compatible; Nmap Scripting Engine; https://nmap.org/book/nse.html)"
192.168.8.190 - - [13/Feb/2026:00:46:59 +0000] "GET /nmaplowercheck1770943618 HTTP/1.1" 404 455 "-" "Mozilla/5.0 (compatible; Nmap Scripting Engine; https://nmap.org/book/nse.html)"
192.168.8.190 - - [13/Feb/2026:00:46:59 +0000] "GET /.git/HEAD HTTP/1.1" 404 455 "-" "Mozilla/5.0 (compatible; Nmap Scripting Engine; https://nmap.org/book/nse.html)"
192.168.8.190 - - [13/Feb/2026:00:46:59 +0000] "GET /evox/about HTTP/1.1" 404 455 "-" "Mozilla/5.0 (compatible; Nmap Scripting Engine; https://nmap.org/book/nse.html)"
192.168.8.190 - - [13/Feb/2026:00:46:59 +0000] "GET /HNAP1 HTTP/1.1" 404 455 "-" "Mozilla/5.0 (compatible; Nmap Scripting Engine; https://nmap.org/book/nse.html)"
192.168.8.190 - - [13/Feb/2026:00:46:59 +0000] "GET /favicon.ico HTTP/1.1" 404 455 "-" "Mozilla/5.0 (compatible; Nmap Scripting Engine; https://nmap.org/book/nse.html)"

fast.log entry (suricata):
02/13/2026-12:42:38.939155  [**] [1:2034567:1] ET HUNTING curl User-Agent to Dotted Quad [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.8.190:48930 -> 192.168.8.100:80
02/13/2026-12:43:21.387556  [**] [1:2034567:1] ET HUNTING curl User-Agent to Dotted Quad [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.8.190:54604 -> 192.168.8.100:80

**Assessment:**  
Web enumeration attempts confirmed via host logs.  
IDS detection is dependent on rule coverage.

---

# 4. Detection Summary

| Activity Type | IDS Detected | Host Logs Confirmed | Confidence |
|---------------|-------------|---------------------|------------|
| ICMP Probe | Yes | N/A | High |
| Nmap Scan | Yes | Yes | High |
| SSH Brute Force | Yes | Yes | Very High |
| Web Enumeration | Yes | Yes | High |

---

# 5. Conclusion

- The attack simulation conducted from 192.168.8.100 was successfully detected and correlated across multiple data sources.
- Network-layer reconnaissance and ssh authentication abuse were identified through Suricata alerts.  
- Host-level logging provided additional confirmation for SSH and HTTP activity.
- This demonstrates effective layered detection capability.
