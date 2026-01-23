# Day 1: Static IP Configuration & Troubleshooting

## Task Overview

Configured Host-Only networking with Static IPs for a 3-VM lab environment (2 Servers, 1 Desktop Client) to enable internet communication.

## Network Configuration
* **Network Type:** Host-Only Adapter (VirtualBox)
* **Subnet:** 192.168.56.0/24
* **Gateway:** None (Internal Network)

### Machine Details

| Hostname | Interface | IP Address | Method |
|----------|-----------|------------|--------|
| **srv1** | `enp0s8` | `192.168.56.10` | Netplan (CLI) |
| **srv2** | `enp0s8` | `192.168.56.11` | Netplan (CLI) |
| **client** | `enp0s8` | `192.168.56.20` | Netplan |

---

## 🔧 Troubleshooting Log (Issues Faced)

### 1. Terminal Hidden Inout (No Echo)
* **Issue:** On `srv1`, typing commands produced no text on the screen, through pressing Enter still executed again.
* **Cause:** The terminal's "local echo" was disabled, likely due to interrupted `sudo` password prompt.
* **Solution:** Typed `reset` blindly and pressed Enter to restore terminal functionality. Also, cleared history (`history -c`) to remove accidently typed passwords.

### 2. Ubuntu Client Boot Freeze
* **Issue:** The Ubuntu Desktop client hanged indefinitely at the spinning logo (Plymouth splash screen).
* **Diagnosis:** Pressing `Esc` revealed the boot process was stuck or hidden.
* **Solution:** Changed VirtualBox Display settings:
    * Graphic Controller: **VBoxSVGA**
    * Video Memory: Increase to **128 MB** 

### 3. "Network Unreachable" on Client
* **Issue:** `ping 192.168.56.10` failed immediately with "Network is unreachable" even after editing the Netplan file.
* **Cause:** The configuration was saved but not loaded into the kernel.
* **Solution:** Ran `sudo netplan apply` to enforce the changes. Verified interface status with `ip a`.

---

## Verification
Successful connectivity confirmed via ping tests:
- [x] Client -> srv1 (`ping -c 3 192.168.56.10`)
- [x] Client -> srv2 (`ping -c 3 192.168.56.11`)
- [x] srv1 -> Client (`ping -c 3 192.168.56.20`)
