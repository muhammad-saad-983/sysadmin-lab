# Week 5 - Day 3: Automated rsync Backup Engine

## 1. Overview
Implemented an automated backup system that synchronizes critical infrastructure and application data from srv1 to srv2.

## 2. Infrastructure & Security
- **Identity Management**: Established an Ed25519 SSH key-based trust for the `root` user to allow non-interactive, system-level backups.
- **Firewall Handling**: Navigated UFW restrictions on srv2 to ensure a secure, whitelisted data tunnel.
- **Differential Transfer**: Utilized `rsync` with archival flags (`-aHAX`) to preserve permissions and minimize bandwidth.

## 3. Backup Scope
The following high-priority directories are captured in every run:
- `/etc` (System Configuration)
- `/etc/nginx` (Web Server & SSL Certs)
- `/var/www` (Frontend Content)
- `/home/saad/miniapp` (Python Backend Code)

## 4. Final Verification Results
The backup vault on srv2 (`192.168.56.11`) confirms successful receipt of all assets:
```text
/home/saad/backups/srv1/daily/2026-02-21_19-17-34:
drwxr-xr-x 109 saad saad 4096 etc
drwxrwxr-x   2 saad saad 4096 miniapp
drwxr-xr-x   9 saad saad 4096 nginx
drwxr-xr-x   3 saad saad 4096 www
