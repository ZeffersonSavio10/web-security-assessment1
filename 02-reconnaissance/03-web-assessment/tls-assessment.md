# TLS Configuration Assessment

## Objective

Assess the publicly accessible TLS configuration of the Zeffer Squin web application and identify weak or outdated cryptographic configurations.

## Target

`zeffersquin.tech:443`

## Tool

Nmap 7.98

## Script

`ssl-enum-ciphers`

## Command

```bash
nmap -Pn -p 443 --script ssl-enum-ciphers zeffersquin.tech \
-oN 02-reconnaissance/results/tls-enum-ciphers.txt
```

## Results

### TLS 1.2

The server supports the following cipher suites:

- `TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256`
- `TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384`
- `TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256`

Nmap rated the supported cipher suites as **A**.

### TLS 1.3

The server supports:

- `TLS_AKE_WITH_AES_128_GCM_SHA256`
- `TLS_AKE_WITH_AES_256_GCM_SHA384`
- `TLS_AKE_WITH_CHACHA20_POLY1305_SHA256`

Nmap rated the supported cipher suites as **A**.

## Overall Result

```text
Least Strength: A
```

No weak cipher suite was identified by this assessment.

## Security Assessment

**Status: PASS**

The current TLS configuration demonstrates a strong cryptographic baseline based on the Nmap `ssl-enum-ciphers` assessment.

## Finding

**No vulnerability identified.**

## Recommendation

Continue monitoring TLS configuration and periodically review supported protocols and cipher suites when the web server or operating system is upgraded.

## Evidence

Raw scan output:

```text
02-reconnaissance/results/tls-enum-ciphers.txt
```

## Conclusion

The TLS configuration was assessed using Nmap and received a minimum cipher strength rating of **A**. No weak cipher configuration was identified during this assessment.
