# Week 4 - Day 4: Nginx Hardening & Rate Limiting

## 1. Security Headers Implementation
Added protective headers to the HTTPS block of `site1.lab` to enhance browser-side security:
- **X-Frame-Options**: Set to `SAMEORIGIN` to mitigate Clickjacking attacks.
- **X-Content-Type-Options**: Set to `nosniff` to prevent MIME-type sniffing.
- **Referrer-Policy**: Implemented to control data leakage when navigating away from the site.

## 2. Rate Limiting Configuration
Established a request limit zone to protect the infrastructure from DoS attempts:
- **Zone Definition**: `10MB` shared memory zone tracking binary IP addresses.
- **Policy**: `10 requests/second` with a `20-request burst` capacity.
- **Logic**: Used `nodelay` to ensure smooth performance for legitimate burst traffic while dropping excessive requests.

## 3. Verification
Verified via `curl -k -I`:
```text
HTTP/1.1 200 OK
Server: nginx/1.24.0
X-Frame-Options: SAMEORIGIN
X-Content-Type-Options: nosniff
Referrer-Policy: strict-origin-when-cross-origin
