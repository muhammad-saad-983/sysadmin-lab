# System Administration Lab

## Goal of the Lab
To build a simulated corporate network using VirtualBox to learn Linux administration, networking, SSH, and server management.

## VM List
| Hostname | OS | RAM | Storage | Role |
|----------|----|-----|---------|------|
| **srv1** | Ubuntu Server 24.04 | 2GB | 25GB | Main Server |
| **srv2** | Ubuntu Server 24.04 | 2GB | 25GB | Secondary Server |
| **client** | Ubuntu Desktop 24.04 | 2GB | 25GB | User Workstation |

## Network Diagram
```text
[ Internet ]
      |
    (NAT)
      |
+---------------------+---------------------+
|      Switch (Host-Only Network)           |
+----------+----------+----------+----------+
           |          |          |
        [srv1]     [srv2]     [client]
