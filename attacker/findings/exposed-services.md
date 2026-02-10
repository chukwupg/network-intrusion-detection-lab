# Exposed Services Analysis

## SSH (Port 22)
- Service identified as OpenSSH.
- Accepts password-based authentication.
- No visible rate limiting or CAPTCHA protection detected.
- Suitable target for credential-based attacks.

## HTTP (Port 80)
- Apache web server detected.
- Default web page accessible.
- No authentication required for access.
- Error responses observed when requesting invalid paths.

## Security Observations
- Services are exposed without apparent hardening.
- Logging and monitoring presence unknown from attacker perspective.
- Configuration appears typical of small enterprise or lab environments.
