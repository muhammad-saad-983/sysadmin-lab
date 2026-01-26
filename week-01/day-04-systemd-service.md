# Day 04: Systemd Services & Timers

## 🎯 Goal
Create a background service that logs a message every minute using native `systemd` timers instead of `cron`.

## 🛠️ Implementation
### 1. The Script
- **Location:** `/usr/local/bin/hello-sysadmin.sh`
- **Function:** Appends the current date to `/var/log/hello-sysadmin.log`.

### 2. The Service Unit (`.service`)
- Defined `Type=oneshot` so systemd knows the process is expected to exit after running.
- Points to the executable script.

### 3. The Timer Unit (`.timer`)
- **OnBootSec=30:** Starts 30s after reboot.
- **OnUnitActiveSec=60:** Repeats every 60s relative to the last run.

## ✅ Verification
- `systemctl list-timers` shows the timer is active.
- `tail /var/log/hello-sysadmin.log` shows entries appearing every minute:
  > Thu Jan 25 10:00:01 UTC 2026 - hello from sysadmin service
  > Thu Jan 25 10:01:01 UTC 2026 - hello from sysadmin service
