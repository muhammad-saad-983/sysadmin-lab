# Day 01 & 02: Lab Environment Setup

## Tasks Completed
1. **VirtualBox Installation:** Installed VirtualBox 7.0 on Ubuntu 24.04 host.
2. **VM Creation:** Created 3 Virtual Machines (srv1, srv2, client).
   - Configured 2GB RAM and 2 CPUs per VM.
3. **Network Configuration:**
   - **Adapter 1:** NAT (for internet access).
   - **Adapter 2:** Host-Only (for internal static IP communication).
4. **OS Installation:**
   - Installed Ubuntu Server 24.04 on `srv1` and `srv2`.
   - Installed Ubuntu Desktop 24.04 on `client`.
   - Enabled OpenSSH Server during installation.
5. **Snapshots:** Taken "clean-install" snapshots for all VMs as a safety baseline.

---

## 🔧 Troubleshooting Log (Challenges & Fixes)

### Issue 1: VirtualBox Installation Failed (Secure Boot)
* **Error:** `modprobe vboxdrv failed` during installation.
* **Cause:** UEFI Secure Boot was blocking the unsigned VirtualBox kernel modules.
* **Solution:** 1. Rebooted into BIOS.
  2. Set a Supervisor Password (required to change Secure Boot settings on Acer/HP).
  3. Changed Secure Boot to **Disabled**.
  4. Ran `sudo /sbin/vboxconfig` to rebuild drivers.

### Issue 2: VM Failed to Start (KVM Conflict)
* **Error:** `VERR_VMX_IN_VMX_ROOT_MODE`
* **Cause:** The Linux KVM module was already using the virtualization hardware, preventing VirtualBox from accessing it.
* **Solution:** - Unloaded KVM temporarily: `sudo rmmod kvm_intel`
  - Created a permanent blacklist file: `echo 'blacklist kvm-intel' | sudo tee /etc/modprobe.d/blacklist-kvm.conf`

### Issue 3: Reboot Hung on "Failed unmounting cdrom"
* **Observation:** After installation, the VM screen turned black and displayed CD-ROM mount errors.
* **Solution:** This is a known VirtualBox quirk. I simply pressed `ENTER` to force the ISO ejection and the reboot proceeded normally.
