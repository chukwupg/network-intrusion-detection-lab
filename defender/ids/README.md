# Suricata IDS Configuration

This document contains the configuration documentation for Suricata (Intrusion Detection System) deployed in the defender environment.

## IDS Mode

- **Mode**: Passive IDS (monitoring-only)
- Suricata is configured to run in **IDS mode** rather than IPS mode.
- It inspects network traffic and generates alerts without blocking packets.

**Rationale**:  
IDS mode is suitable for a lab and detection-focused setup where visibility and alerting are prioritized over active traffic manipulation.

---

## Interface Selection and Rationale

- **Monitored Interface**: `enp0s3` 
- The interface is connected to the same subnet as the Victim Server (`192.168.8.0/24`).

**Rationale**:
- Placing the IDS Sensor (Suricata) on the same network segment as the Victim Server allows it to observe inbound and outbound traffic.
- This setup simulates an enterprise deployment where sensors monitor traffic to critical assets.

---

## Ruleset Selection

- **Primary Ruleset**: Emerging Threats Open (ET Open Rules)

**Rationale**:
- ET Open rules provide broad coverage for common attacks such as:
  - Port scanning  
  - Brute-force attempts  
  - Web exploitation  
  - Malware indicators  

---

## Validation Command

After configuring Suricata, the configuration and rules are validated using:

```bash
sudo suricata -T -c /etc/suricata/suricata.yaml -v
````

---

## Purpose:

- Verifies syntax correctness
- Confirms rules load properly
- Ensures Suricata can start without configuration errors

---

## Notes

- Alerts are written to:
  - /var/log/suricata/fast.log
  - /var/log/suricata/eve.json
- Configuration changes should always be followed by a validation test before restarting the service.