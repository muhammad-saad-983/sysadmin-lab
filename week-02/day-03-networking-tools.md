# Day 03: Networking Essentials Toolkit

## 🛠️ Command Breakdown

### 1. `ip a` (Address)
- **Layer:** 2 (Data Link) & 3 (Network)
- **Use:** Displays IP addresses and MAC addresses. Used to verify "Do I have an IP?"

### 2. `ip r` (Route)
- **Layer:** 3 (Network)
- **Use:** Shows the Routing Table. Crucial for debugging "Why can't I reach the internet?"

### 3. `ping`
- **Layer:** 3 (Network - ICMP)
- **Use:** Tests end-to-end connectivity. "Is the other machine alive?"

### 4. `traceroute`
- **Layer:** 3 (Network)
- **Use:** Traces the path packets take. Identifies exactly which router is dropping packets.

### 5. `dig`
- **Layer:** 7 (Application - DNS)
- **Use:** DNS Lookup utility. "Why is google.com not resolving to an IP?"

### 6. `curl -I`
- **Layer:** 7 (Application - HTTP)
- **Use:** Fetches HTTP headers. Used to check if a web server is up and what software it is running.


