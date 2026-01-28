# Day 01: Storage Management Basics

## 📊 Command Breakdown
### 1. `df -h` (Disk Free)
- **Purpose:** Checks available space on mounted filesystems.
- **Why use it:** First step when a "No space left on device" error occurs.
- **Key Output:** Look at `/` (Root) Use%.

### 2. `du -sh` (Disk Usage)
- **Purpose:** Estimates file space usage for specific directories.
- **Why use it:** To find *which* folder is filling up the disk.
- **Example:** `du -sh /var/log/*` showed me the size of individual log folders.

### 3. `lsblk` (List Block Devices)
- **Purpose:** Lists all storage devices (physical disks) and their partitions.
- **Why use it:** To verify if a new virtual hard disk is attached before formatting it.

## 🛠️ Practice
- Created directory `/mnt/lab` to serve as a future mount point for external storage.
