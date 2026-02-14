# IP Addressing

This document defines the IP addressing scheme and network configuration used within the lab environment.

## Network Configuration

| Device         | Network Mode    | IP Address        | Subnet Mask        | Default Gateway | Purpose / Rationale                                                                 |
|----------------|-----------------|-------------------|--------------------|------------------|--------------------------------------------------------------------------------------|
| Victim Server  | Bridged Adapter | 192.168.8.100     | 255.255.255.0 (/24) | 192.168.8.1      | Hosts production-like services (SSH, Apache, DNS) and represents the protected asset. |
| IDS Sensor     | Bridged Adapter | 192.168.8.200     | 255.255.255.0 (/24) | 192.168.8.1      | Monitors and analyzes traffic within the same subnet as the victim server for intrusion detection. |
| Attacker VM    | Bridged Adapter | 192.168.8.190     | 255.255.255.0 (/24) | 192.168.8.1      | Simulates attack to the victim server. |

## Design Rationale

1. **Same Subnet Deployment**: Placing the Victim Server and IDS Sensor on the same network segment enables the IDS to observe service traffic and potential attack patterns directly.  
2. **Bridged Adapter Mode**: Allows both systems to participate on the physical LAN, simulating real enterprise deployments.  
3. **Static IP Allocation**: Ensures predictable addressing for service access, monitoring, log correlation, and alerting.  
4. **Gateway Consistency**: A shared default gateway simplifies routing and ensures outbound connectivity for updates and testing.

### Notes

- Network segment: `192.168.8.0/24`  
- Usable host range: `192.168.8.1 – 192.168.8.254`  
- Broadcast address: `192.168.8.255`  