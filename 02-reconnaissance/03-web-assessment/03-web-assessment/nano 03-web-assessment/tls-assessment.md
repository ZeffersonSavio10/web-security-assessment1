# TLS/SSL Security Assessment

## Objective

Assess the TLS configuration of `zeffersquin.tech` and identify weak or insecure
protocols and cipher suites.

## Target

- Domain: `zeffersquin.tech`
- Port: `443/tcp`
- Service: HTTPS
- Server: nginx

## Tool

- Nmap 7.98
- NSE Script: `ssl-enum-ciphers`

## Command

```bash
nmap -Pn -p 443 --script ssl-enum-ciphers zeffersquin.tech \
-oN 02-reconnaissance/results/tls-enum-ciphers.txt
