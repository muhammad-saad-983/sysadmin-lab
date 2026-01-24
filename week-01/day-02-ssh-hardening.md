# Day 02: SSH Hardening & Troubleshooting

## 🎯 Lab Goals
1. Configure Static IP (`192.168.56.10`) on **srv1**.
2. Generate SSH Key Pair (`ed25519`) on Client/Host.
3. Disable Password Authentication to prevent Brute Force attacks.
4. Disable Root Login for audit security.

## 🛠️ Configuration Steps
### 1. Static IP Setup (Netplan)
- Edited `/etc/netplan/50-cloud-init.yaml` to assign `192.168.56.10/24` to `enp0s8`.
- Applied via `sudo netplan apply`.

### 2. SSH Keys
- Generated keys: `ssh-keygen -t ed25519`
- Copied to server: `ssh-copy-id saad@192.168.56.10`

### 3. Hardening `sshd_config`
- **File:** `/etc/ssh/sshd_config`
- **Settings Changed:**
  - `PermitRootLogin no`
  - `PasswordAuthentication no`
  - `PubkeyAuthentication yes`

---

## 🔧 Troubleshooting Log (The "Real" Work)

### Issue 1: "Permission Denied" despite correct password
* **Symptom:** `ssh-copy-id` rejected my password repeatedly.
* **Root Cause:** **Keyboard Layout Mismatch**. The Server was installed with **UK (GB)** layout, but I was typing on a **US** keyboard. Special characters like `@` and `"` were swapped, so the password I typed was not what the server received.
* **Fix:**
  1. Edited `/etc/default/keyboard` and changed `XKBLAYOUT="gb"` to `"us"`.
  2. Ran `sudo dpkg-reconfigure keyboard-configuration`.
  3. Rebooted `srv1`.

### Issue 2: Hardening Settings Ignored
* **Symptom:** Even after setting `PasswordAuthentication no`, I could still log in with a password.
* **Root Cause:** **Cloud-Init Override**. Ubuntu creates a file at `/etc/ssh/sshd_config.d/50-cloud-init.conf` that explicitly sets `PasswordAuthentication yes`, overriding my main config file.
* **Fix:** Renamed the conflicting file to disable it:
  `sudo mv /etc/ssh/sshd_config.d/50-cloud-init.conf /etc/ssh/sshd_config.d/50-cloud-init.conf.disabled`

## ✅ Verification Results
- `ssh saad@192.168.56.10` -> **Logs in instantly** (No password).
- `ssh -o PreferredAuthentications=password ...` -> **Permission denied** (Success).
