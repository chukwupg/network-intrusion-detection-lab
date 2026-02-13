# Open Ports Identified

## Summary
A network scan was conducted against the target host (victim server) to identify exposed TCP services.

## Results

| Port | Protocol | State | Service |
|-----:|----------|-------|---------|
| 22   | TCP      | Open  | SSH     |
| 80   | TCP      | Open  | HTTP    |

## Notes
- Only two services were exposed externally. 
- No firewall filtering was observed on the scanned ports.
- Service exposure is consistent with a minimal server deployment.

These ports formed the basis for subsequent reconnaissance and attack simulation.
