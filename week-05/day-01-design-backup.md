# Day 1: Automated Backup Design (srv1 -> srv2)

## 1. Strategy Overview
To ensure high availability and disaster recovery, srv1 will perform an automated nightly backup to srv2. This protects against configuration loss, code deletion, and OS corruption.

## 2. Backup Scope (srv1)
| Component | Directory Path | Priority |
| :--- | :--- | :--- |
| System Configs | `/etc/` | High |
| Web Server | `/etc/nginx/` | High |
| Web Content | `/var/www/` | Medium |
| Application Code | `/home/saad/miniapp/` | Critical |

## 3. Destination (srv2)
- **Path**: `/home/saad/backups/srv1/`
- **Method**: rsync over SSH (Key-based)

## 4. Acceptance Criteria (The "Restoration" Test)
A backup is only successful if it can be restored. I will prove success by:
1. Deleting the `index.html` on srv1 and restoring it from srv2.
2. Deleting the `miniapp` code and restoring it from srv2.
3. Successfully restarting the Nginx service after a config restoration.
