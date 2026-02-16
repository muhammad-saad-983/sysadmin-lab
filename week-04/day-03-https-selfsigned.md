# Week 4 - Day 3: HTTPS & Service Restoration

## Overview
Implemented SSL/TLS encryption for the internal lab environment to secure traffic between the Client and srv1.

## 1. HTTPS Implementation
- Generated self-signed certificates for `site1.lab`.
- Configured Nginx Port 443 with SSL termination.
- Verified 301 redirection from Port 80 to Port 443.

## 2. Certificate Generation
Generated a self-signed X.509 certificate using OpenSSL:
```bash
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout /etc/nginx/certs/lab.key \
  -out /etc/nginx/certs/lab.crt \
  -subj "/CN=site1.lab"

## 3. Verification Output
```bash
# Verify Redirect
curl -I [http://site1.lab](http://site1.lab) | grep "301 Moved Permanently"

curl -k [https://site1.lab/app/health](https://site1.lab/app/health)
# Expected: {"status": "healthy"}
