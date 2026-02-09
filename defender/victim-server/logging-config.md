# Victim Server Logging Configuration

This document outlines how logging is configured for the Victim Server services.

## SSH Logging

- **Log File**: `/var/log/auth.log`
- **Purpose**: Logs all SSH authentication attempts, both successful and failed.

## Apache2 Logging

- **Log Files**:
  - Access Log: `/var/log/apache2/access.log`
  - Error Log: `/var/log/apache2/error.log`
- **Purpose**:
  - Access log tracks every HTTP request for auditing and troubleshooting.
  - Error log records server errors, crashes, and misconfigurations.

### Notes

- Logging is configured for both auditing and incident response.
- Permissions set to restrict unauthorized access to log files.
