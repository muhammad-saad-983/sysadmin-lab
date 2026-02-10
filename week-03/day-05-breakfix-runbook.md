# Day 05: Break/Fix Drills & Final Runbook

## Drill A: Backend Failure
- **Action:** Stopped `miniapp` service.
- **Sign:** `curl` returned **502 Bad Gateway**.
- **Solution:** Restarted service. `curl` returned **200 OK**.
- **Key Learning:** Nginx protects the user from seeing "Connection Refused" and shows a polite error page instead, but a 502 always means "Check the App Server".

## Drill B: Config Corruption
- **Action:** Removed semicolon from Nginx config.
- **Sign:** `sudo nginx -t` failed with `[emerg]`.
- **Solution:** Fixed syntax error.
- **Key Learning:** `nginx -t` is a mandatory safety step. Reloading a broken config can crash the production server.
