# 🖥️ DisplayLink Dock Fix on Debian 13 (Clamshell Mode)

This guide fixes an issue where **external monitors connected via a DisplayLink dock do NOT activate when the laptop lid is closed** until the user opens the laptop and logs in.

---

## 🧠 Problem

When using a pluggable / DisplayLink dock:

- External monitors stay **black when the laptop lid is closed**
- Displays only activate after:
  - Opening the laptop
  - Logging into the desktop session

---

## 🎯 Root Cause

This behavior is caused by:

- `systemd-logind` suspending or limiting display behavior on lid close
- DisplayLink initializing **only after a user session starts**
- Laptop not entering a true “dock mode” (clamshell mode)

---

## ✅ Solution Overview

We will:

1. Disable lid-close behavior (prevent suspend/display issues)
2. Ensure the DisplayLink service starts at boot

---

# 🔧 Fix 1 — Disable Lid Close Actions

Edit the logind configuration:

```bash
sudo nano /etc/systemd/logind.conf
```

Uncomment and set the following:

```ini
HandleLidSwitch=ignore
HandleLidSwitchDocked=ignore
HandleLidSwitchExternalPower=ignore
```

Apply changes:

```bash
sudo systemctl restart systemd-logind
```

---

## 🔍 What This Does

- Prevents the system from suspending or altering display behavior
- Keeps the system fully active when the lid is closed
- Enables proper **clamshell (dock) operation**

---

# 🔧 Fix 2 — Ensure DisplayLink Service Starts at Boot

Check the service:

```bash
systemctl status displaylink-driver.service
```

If not enabled, run:

```bash
sudo systemctl enable displaylink-driver.service
sudo systemctl start displaylink-driver.service
```

---

## 🔍 What This Does

- Ensures DisplayLink initializes **before login**
- Allows external monitors to be ready immediately at boot

---

# ✅ Expected Result

After applying both fixes:

- Plug in dock → monitors turn on immediately
- Laptop can stay closed
- No need to open lid or log in first
- Behavior matches typical dock experience (Windows/macOS)

---

# 🧪 Verification

After reboot:

1. Close laptop lid
2. Connect dock
3. Confirm:
   - External monitors activate
   - System remains responsive

---

# 🧠 Notes

- Tested on **Debian 13 (Trixie)**
- Works with DisplayLink drivers installed via:
  - AdnanHodzic/displaylink-debian script (recommended)
- Compatible with Wayland

---

# 🧾 Summary

| Fix | Purpose |
|-----|--------|
| Disable lid actions | Prevents system from pausing display behavior |
| Enable DisplayLink service | Ensures monitors initialize before login |

---

## 🚀 Result

Your Debian system now behaves like a proper **docked workstation**:
- Lid closed ✅  
- External monitors active ✅  
- No login required to trigger displays ✅  

---
