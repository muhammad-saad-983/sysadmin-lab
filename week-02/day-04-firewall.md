# Day 04: Firewall Configuration (UFW)

## 🛡️ Policy Strategy
We implemented **default deny** policy. This means all incoming ports are closed unless explicitly opened.

## 📝 Rules Implemented
1. **Default:** `Deny Incoming`, `Allow Outgoing`.
2. **SSH (Port 22):** Restricted to specific IP `192.168.56.20` (Admin Client).
3. **HTTP/HTTPs (Port 80/443):** Open to `Any` (Public web access).

## ✅ Verification
- **Client (.20):** Successfully SSH'd into srv1.
- **srv2 (.10):** SSH connection timed out (Blocked by UFW).

## 📊 Final Status
```text
Status: active
     To                         Action      From
     --                         ------      ----
[ 1] 22/tcp                     ALLOW IN    192.168.56.20
[ 2] 80/tcp                     ALLOW IN    Anywhere
[ 3] 443/tcp                    ALLOW IN    Anywhere
