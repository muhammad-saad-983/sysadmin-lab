# Day 05: Log Analysis & Troubleshooting Playbook

## 🔍 1. Investigating "Permission Denied" (Auth Failures)
If a user cannot login or a password is rejected:
* **Command:** `sudo tail -f /var/log/auth.log`
* **What to look for:** Lines saying "Failed password", "Invalid user", or "sudo: ... command not allowed".
* **Modern alternative:** `journalctl -u ssh -e`

## 🛠️ 2. Investigating "Service Failed to Start"
If a website is down or a database won't start:
* **Command:** `journalctl -u [service_name] -xe`
* **Example:** `journalctl -u nginx -xe`
* **Flags:**
    * `-x`: Show explanations/solutions.
    * `-e`: Jump to the latest error.

## 💾 3. Investigating "System Slowness" (Resources)
**Check Disk Space:**
* **Command:** `df -h`
* **Why:** `df` (Disk Free) shows usage. `-h` makes it Human-readable (GB/MB). If `/` is 100% full, the system crashes.

**Check Memory (RAM):**
* **Command:** `free -h`
* **Why:** Shows used vs. free RAM. If "Swap" is being used heavily, the system needs more RAM.
