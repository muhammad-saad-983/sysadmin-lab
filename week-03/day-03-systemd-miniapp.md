# Day 03: Systemd Service Implementation

## Goal
Convert the manual Python script into a robust background service that survives crashes and reboots.

## Service Configuration (`/etc/systemd/system/miniapp.service`)
- **User:** `saad` (Running as non-root for security).
- **Restart Policy:** `always` (Auto-restarts on crash or clean exit).
- **RestartSec:** `2` (Brief pause to prevent rapid restart loops).

## Crash Test Verification
1. Checked status: PID was `1234`.
2. Killed process: `sudo kill -9 1234`.
3. Checked status again: Service was `active (running)` with a **new** PID.
4. Confirmed `systemd` successfully resurrected the backend.

## Integration Check
`curl http://site1.lab/app/health` returns valid JSON, confirming Nginx can still talk to the background service.
