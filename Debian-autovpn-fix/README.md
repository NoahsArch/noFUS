# Debian 13 OpenVPN Auto-Connect Fix

This guide ensures your **OpenVPN** connection in **NetworkManager** starts automatically on boot or when connected to specific networks — without asking for a password or showing a confirmation popup.

Tested on **Framework 13 (Ryzen 7040)** running **Debian 13 GNOME Wayland**.

---

## 🧰 Setup and Dependencies

Install the required packages and open the NetworkManager connection editor to create or import your `.ovpn` configuration:

```bash
sudo apt-get install network-manager-openvpn-gnome
nm-connection-editor
nmcli connection show
```

Use the connection editor to **import your VPN profile**, then verify the connection name using the `nmcli` command above.  
Once the connection exists, continue with the steps below.

---

## ⚙️ Changes Made

Open the VPN configuration file:

```bash
sudo nano /etc/NetworkManager/system-connections/Ovpn.nmconnection
```

Inside `[vpn]`, ensure this line exists or is changed to:

```ini
[vpn]
password-flags=0        # store the password in this file (no prompt)
```

Inside `[connection]`, add or modify these lines:

```ini
[connection]
autoconnect=true         # enable auto-connect on boot or when network is active
autoconnect-retries=0    # keep retrying if disconnected (optional)
```

Save the file and set proper permissions:

```bash
sudo chown root:root /etc/NetworkManager/system-connections/Ovpn.nmconnection
sudo chmod 600 /etc/NetworkManager/system-connections/Ovpn.nmconnection
```

---

## 🚀 Commands Run

Reload and restart NetworkManager so changes take effect:

```bash
sudo nmcli connection reload
sudo systemctl restart NetworkManager
```

Verify the settings:

```bash
nmcli connection show "Ovpn" | grep -E 'autoconnect|password-flags'
```

Expected output:

```
connection.autoconnect: yes
vpn.password-flags: 0
```

Test the connection manually (optional):

```bash
nmcli connection up "Ovpn"
```

If it connects without prompting, your auto-connect setup is complete ✅

---

## 🧠 Notes

- `network-manager-openvpn-gnome` provides the GUI and VPN plugin required by `nm-connection-editor`.
- `password-flags=0` tells NetworkManager to use the stored password instead of prompting.
- `autoconnect=true` ensures the VPN automatically activates when your system connects to a matching network or starts up.
- Works reliably on **Debian 13**, **Kali**, and other pure NetworkManager-based systems (without Netplan or Canonical patches).

---

**Author:** *Noah Lanning*  
**Last Updated:** October 2025  
**License:** MIT (optional)
