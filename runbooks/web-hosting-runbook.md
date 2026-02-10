# Web Hosting Platform Runbook

## Architecture Overview
* **Frontend:** Nginx (Reverse Proxy) listening on Port 80.
* **Backend:** Python `miniapp` listening on `127.0.0.1:8080`.
* **Service Manager:** Systemd handles auto-starts and restarts.

## Deployment Operations
### How to enable a new site
1.  Create config in `/etc/nginx/sites-available/`.
2.  Link it: `sudo ln -s /etc/nginx/sites-available/yoursite /etc/nginx/sites-enabled/`.
3.  **Validate:** `sudo nginx -t`.
4.  Reload: `sudo systemctl reload nginx`.

### How to restart the backend app
```bash
sudo systemctl restart miniapp
# Check status immediately after
sudo systemctl status miniapp
