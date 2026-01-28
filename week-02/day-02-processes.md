# Day 02: Process & Performance Monitoring

## 🚀 Performance Tools
### 1. `top` / `htop`
- **Purpose:** Real-time view of system resources.
- **Key Metric:** **Load Average**. (If Load > CPU Cores, system is struggling).
- **Difference:** `htop` is interactive and easier to read than `top`.

### 2. `ps aux`
- **Purpose:** Snapshot of all running processes.
- **Why use it:** To grep for a specific PID or service status (e.g., `ps aux | grep ssh`).

### 3. `free -h`
- **Purpose:** Checks RAM and Swap usage.
- **Warning Sign:** High **Swap** usage indicates the server needs more RAM.

## 📡 Network Process Check
- **Command:** `sudo ss -tulpn | grep ':80'`
- **Result:** (Likely empty right now as no web server is installed).
- **Purpose:** Checks which specific application is listening on Port 80 (HTTP). Crucial for debugging "Port already in use" errors.
