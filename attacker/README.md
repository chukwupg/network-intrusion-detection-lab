# Attacker Overview (Phase 2)

## Role
External attacker / penetration tester conducting a black-box assessment against a target host within a controlled lab environment.

## Objective
To identify exposed services, perform limited reconnaissance, and simulate authentication abuse in order to generate detectable malicious traffic for defensive analysis.

## Scope Summary
- Target IP: 192.168.8.100
- Interface: eth0
- In-scope services: SSH (22), HTTP (80)
- Engagement type: Black-box
- Credentials: None provided
- Techniques used: Network scanning, service enumeration, SSH brute-force simulation, web enumeration.

## Tooling
- Nmap
- Hydra
- curl
- tcpdump

## Rules of Engagement
- No exploitation beyond authentication abuse
- No denial-of-service attacks
- No privilege escalation attempts

All actions were performed to simulate realistic attacker behavior while maintaining lab safety.