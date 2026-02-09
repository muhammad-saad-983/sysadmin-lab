# Debugging & Observability (logs, errors, failure clues) Runbook

## The Checklist
When website goes down, run the below cmds to figure out the root cause.

### 1. Check the Ports
* **Cmd:** `sudo ss -tulpn | grep -E ':80|:8080'`
* **Pass:** We see lines for both `:80` (nginx) and `:8080` (python app)
* **Fail:** 
    * Missing `:80`? -> Start Nginx
    * Missing `:8080`? -> Start Miniapp

### 2. Check the Doorman (Nginx Status)
* **Cmd:** `sudo systemctl status nginx`
* **Cmd:** `sudo nginx -t` (Check for config typos)
* **Cmd:** `sudo tail /var/log/nginx/site1.error.log`
* **Clue:**
    * `Connection refused`: Nginx tried to talk to app, but the app was closed.
    * `Permission denied`: Nginx config is pointing to a wrong file path.

### 3. Check the Worker (App Status)
* **Cmd:** `sudo systemctl status miniapp`
* **Cmd:** `journalctl -u miniapp -e`
* **Clue:**
    * `python: command not found`: Path failure.
    * `Traceback (most recent call last)`: The Python code itself crashed.

## Health Checks
* **Frontend:** `curl -I http://site1.lab` (Should be 200 Success)
* **Backend Path:** `curl http://site1.lab/app/health` (Should be JSON)
