# Day 01: Nginx Virtual Hosting

## Goal
Host two distinct websites (`site1.lab` and `site2.lab`) on a single server using Nginx Server Blocks.

## Configuration Details
- **Document Roots:**
  - `/var/www/site1` -> Holds Site 1 HTML
  - `/var/www/site2` -> Holds Site 2 HTML
- **Nginx Configs:**
  - Created files in `/etc/nginx/sites-available/`
  - Symlinked to `/etc/nginx/sites-enabled/`
- **DNS Stubbing:**
  - Modified `/etc/hosts` on Client to point `site1.lab` and `site2.lab` to `192.168.56.10`.

## Verification
`curl http://site1.lab` -> Returns Site 1 content.
`curl http://site2.lab` -> Returns Site 2 content.
