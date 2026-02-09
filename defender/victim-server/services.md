# Victim Server Services

This document outlines the services enabled on the Victim Server, including their ports and purpose, as well as a real-world justification for their deployment.

## Enabled Services

| Service   | Port | Purpose                              | Real-World Justification                                         |
|----------|------|---------------------------------------|------------------------------------------------------------------|
| SSH      | 22   | Secure remote administration          | Allows system administrators to remotely manage and configure the server securely using encrypted communication. |
| Apache2  | 80   | HTTP web server                       | Hosts web applications or static websites, which is common for public-facing servers. |
| DNS      | 53   | Domain Name Resolution                | Provides domain name to IP resolution for internal or public network use. Essential for network communication. |

### Notes

- **SSH**: Enabled for secure server management; password and key-based authentication configured.  
- **Apache2**: Default document root configured with basic site content for testing purposes.  
- **DNS**: Lightweight DNS service is running for lab simulation; not exposed to public Internet for security.
