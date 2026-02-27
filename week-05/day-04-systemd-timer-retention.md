# Automation & Retention

## 1. Automated Scheduling
Implemented a `systemd` timer-service pair to handle daily backups. 
- **Persistence**: Used `Persistent=true` to ensure backups occur even if the system was offline during the scheduled window.
- **Unit Path**: `/etc/systemd/system/srv1-backup.timer`

## 2. Storage Retention Policy
Developed a cleanup script (`cleanup_retention.sh`) to maintain a 7-day rolling window of backups.
- **Method**: Remote execution via SSH on srv2 to prune directories older than 7 days.
- **Purpose**: Prevents disk-full errors and manages storage costs efficiently.

## 3. Evidence
- **Timer Status**: Verified with `systemctl list-timers`.
- **Retention**: Confirmed srv2 `/daily/` directory count stays at <= 7.
