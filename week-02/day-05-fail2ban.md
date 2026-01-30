# Day 05: Fail2Ban (Brute Force Protection)

## 🛡️ Concept
Fail2Ban monitors log files (like `/var/log/auth.log`) for malicious patterns (e.g., repeated failed login attempts). When a pattern is matched, it dynamically updates the firewall (iptables/nftables) to reject the offending IP address for a set amount of time.

## ⚙️ Configuration (`/etc/fail2ban/jail.local`)
We used a `.local` file to override defaults without touching `jail.conf`.

```ini
[sshd]
enabled = true
maxretry = 3        # 3 strikes and you're out
findtime = 10m      # Strikes must happen within 10 mins
bantime = 1h        # Penalty box for 1 hour
ignoreip = 192.168.56.20  # Never ban the Admin Client
