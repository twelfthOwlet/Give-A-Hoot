# Updates, Issues, and Fixes
A running diary of troubleshooting, configurations, and field methods.

## Quick Links
- [Automotive Maintenance Log](slw_Automobile_README.md)
- [Bicycle Rebuild Log](slw_Bicycle_Rebuild_README.md)

---

## December 2023

### Ubuntu 22.04.3: Yellow Tint After 2nd Monitor Install
- **The Issue:** Yellow color distortion appeared immediately after adding a second display.
- **The Fix:** Identified that an incorrect video driver had auto-installed. Installed the correct Nvidia driver package to resolve the coloration issue. *(Version omitted to prevent compatibility reference confusion).*

### Ubuntu Studio VM Upgrade (20.04 to 22.04)
- **Objective:** Command-line upgrade experience.
- **Reference:** [Ubuntu Server Upgrade Documentation](https://ubuntu.com/server/docs/upgrade-introduction)
- **Key Takeaways:**
  - Encountered prompt between `sddm` and `lightdm` — selected `lightdm`.
  - Firefox bundled as a snap package (forced migration).
  - Total upgrade time: ~2 hours.

### RedHat / CentOS 7 VM & SSH Troubleshooting
*(Note: CentOS 7 EOL reached June 30, 2024)*

#### Dec 26, 2023: RHEL 9 Initial Setup
- Installed RHEL 9 minimum into VirtualBox. Encountered network isolation: guest could access the web, but no ping communication between host and guest.
- **Cause:** Left network adapter on default NAT (VirtualBox internal DHCP) instead of bridging.
- **Resolution:** Bridged the adapter and successfully established SSH.

#### Dec 27, 2023: CentOS 7 Pivot
- Replaced RHEL 9 with CentOS 7 minimum install. Configured guest network adapters manually via `vi`.
- Applied lessons learned: immediately bridged the network adapter and installed `net-tools` for port and routing verification.
- **The SSH Host Conflict:** Port 22 was open, but connection failed because the host complained about a conflicting remote host fingerprint for the IP address (leftover from the RHEL 9 test).
- **The Fix:** Cleared the old key using:
  ```bash
  ssh-keygen -f "/home/user/.ssh/known_hosts" -R "xxx.xx.x.xx"
