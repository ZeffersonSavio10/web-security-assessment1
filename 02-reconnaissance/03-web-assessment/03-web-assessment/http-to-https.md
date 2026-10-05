# HTTP to HTTPS Redirect Assessment

## Objective

Verify that HTTP requests to the Zeffer Squin website are redirected to HTTPS.

## Target

`zeffersquin.tech`

## Test

The following command was used:

```bash
curl -I -L http://zeffersquin.tech
```

## Result

The initial HTTP request returned:

```text
HTTP/1.1 301 Moved Permanently
Location: https://zeffersquin.tech/
```

The redirected HTTPS request returned:

```text
HTTP/1.1 200 OK
```

## Request Flow

```text
HTTP
http://zeffersquin.tech
        │
        │ 301 Moved Permanently
        ↓
HTTPS
https://zeffersquin.tech
        │
        │ 200 OK
        ↓
Web Application
```

## Security Assessment

The application correctly redirects HTTP traffic to HTTPS.

This helps ensure that users accessing the application through HTTP are directed to the encrypted HTTPS endpoint.

## Finding

**No vulnerability identified.**

## Security Control

**Status: PASS**

HTTP-to-HTTPS redirection is correctly implemented.

## Evidence

Command:

```bash
curl -I -L http://zeffersquin.tech
```

Result:

```text
HTTP/1.1 301 Moved Permanently
Location: https://zeffersquin.tech/
```

followed by:

```text
HTTP/1.1 200 OK
```

## Conclusion

The HTTP-to-HTTPS redirect control was successfully verified during the assessment.

Further testing will evaluate TLS configuration and other web security controls.
