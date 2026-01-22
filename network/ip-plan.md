# Lab IP Address Plan

## Network Details
* **Network ID:** 192.168.56.0
* **Subnet Mask:** 255.255.255.0 (/24)
* **Host Gateway:** 192.168.56.1

## VM Allocation
| Hostname  | Adapter 1 (NAT)  | Adapter 2 (Host-Only) | Role |
|-----------|------------------|-----------------------|------|
| **srv1**  | DHCP (Internet)  | 192.168.56.10  | DNS / Web Server |
| **srv2**  | DHCP (Internet)  | 192.168.56.20  | Backup / Database |
| **client**| DHCP (Internet)  | 192.168.56.30  | Admin Workstation |
