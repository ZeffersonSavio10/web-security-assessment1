# Security Headers Assessment

## Objective

The objective of this assessment was to review HTTP response security headers configured on the Zeffer Squin web application.

## Target

`zeffersquin.tech`

## Method

HTTP response headers were reviewed using `curl`.

```bash
curl -I http://zeffersquin.tech
curl -I https://zeffersquin.tech
```

## Results

| Security Control | Result |
|---|---|
| Content-Security-Policy | Present |
| Strict-Transport-Security | Present |
| X-Content-Type-Options | Present |
| X-Frame-Options | Present |
| Referrer-Policy | Present |
| Cross-Origin-Opener-Policy | Present |
| Cross-Origin-Resource-Policy | Present |
| X-Permitted-Cross-Domain-Policies | Present |

## CSP

The application returns a Content Security Policy containing controls including:

- `default-src 'self'`
- `object-src 'none'`
- `frame-ancestors 'self'`
- `base-uri 'self'`
- `form-action 'self'`

The policy also uses:

```text
script-src 'self' 'unsafe-inline'
```

This configuration should be reviewed periodically because allowing inline JavaScript can reduce some of the protections normally provided by a strict CSP.

However, the presence of `'unsafe-inline'` alone does not establish a vulnerability.

## HSTS

The application returns:

```text
Strict-Transport-Security:
max-age=15552000; includeSubDomains
```

This indicates that HTTP Strict Transport Security is enabled.

## Additional Security Headers

The following controls were also observed:

```text
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Referrer-Policy: no-referrer
Cross-Origin-Opener-Policy: same-origin
Cross-Origin-Resource-Policy: same-origin
X-Permitted-Cross-Domain-Policies: none
```

## Initial Assessment

The application demonstrates a relatively strong baseline of HTTP security header configuration.

No confirmed vulnerability is assigned based solely on these headers.

Further assessment is required to determine whether:

- HTTP traffic is correctly redirected to HTTPS.
- TLS configuration is appropriately hardened.
- Server information disclosure can be reduced.
- CSP can be strengthened without affecting application functionality.

## Evidence

Raw header results:

```text
02-reconnaissance/results/http-headers.txt
02-reconnaissance/results/https-headers.txt
```

## Status

**Completed — Initial Security Header Review**
