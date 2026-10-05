# 02 — Reconnaissance

## Objective

The objective of this phase was to identify externally exposed TCP services and determine the service versions associated with the authorized Zeffer Squin web infrastructure.

## Target

**Domain:** `zeffersquin.tech`

**Assessment Type:** Authorized Security Assessment

**Tool:** Nmap 7.98

**Scan Type:** TCP service and version detection

## Command

```bash
nmap -Pn -sV zeffersquin.tech -oN nmap-service-scan.txt
```

## Results

| Port | State | Service | Version |
|---:|---|---|---|
| 22 | Open | SSH | OpenSSH 10.2p1 Ubuntu |
| 80 | Open | HTTP | nginx 1.28.3 |
| 443 | Open | HTTPS | nginx 1.28.3 |
| 3871 | Closed | avocent-adsap | — |
| 5678 | Closed | rrac | — |
| 7741 | Closed | scriptview | — |
| 7920 | Closed | Unknown | — |
| 9200 | Closed | wap-wsp | — |
| 32768 | Closed | filenet-tms | — |

## Initial Observations

### SSH — Port 22

SSH is externally reachable and is likely used for remote server administration.

An open SSH port is not automatically a vulnerability. Further configuration assessment is required.

Areas for review:

- Password authentication
- Root login
- SSH key authentication
- Authentication rate limiting
- Fail2Ban
- Allowed users
- SSH configuration
- Logging

### HTTP — Port 80

HTTP is exposed through nginx.

The next assessment phase will determine whether HTTP redirects correctly to HTTPS and whether unnecessary information is disclosed.

### HTTPS — Port 443

HTTPS is exposed through nginx and represents the primary public web application interface.

Further testing will examine:

- TLS configuration
- Security headers
- HTTP methods
- Certificate configuration
- Web server configuration
- Application behavior

## Attack Surface Summary

The initial external attack surface consists primarily of:

```text
Internet
   │
   ├── 22/tcp   SSH
   │
   ├── 80/tcp   HTTP
   │
   └── 443/tcp  HTTPS
```

The remaining ports identified during the scan were closed.

## Security Assessment Status

**Phase:** Reconnaissance

**Status:** Completed

**Next Phase:** Web Application Enumeration

## Evidence

Raw Nmap output:

`results/nmap-service-scan.txt`

## Important Note

This scan identifies exposed services but does not by itself confirm vulnerabilities.

Each exposed service requires additional configuration and security assessment before a vulnerability can be reported.
