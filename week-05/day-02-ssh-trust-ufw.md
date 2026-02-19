# Day 2: Secure Channel & Firewall Hardening

## 1. Passwordless Authentication
- **Algorithm**: Ed25519 (Asymmetric Encryption)
- **Purpose**: To allow automated, non-interactive `rsync` transfers for nightly backups.
- **Result**: Successfully verified `ssh-copy-id` handshake between srv1 and srv2.

## 2. Firewall Configuration (srv2)
Implemented a "Default Deny" policy to protect the backup repository:
- **Rule 1**: Allow TCP/22 from 192.168.56.20 (Client Desktop)
- **Rule 2**: Allow TCP/22 from 192.168.56.10 (srv1 Backup Source)
- **Status**: UFW Active and verified.

## 3. Evidence
- Output of `ssh saad@192.168.56.11 "echo BACKUP_CHANNEL_OK"`:
```text
BACKUP_CHANNEL_OK
