# DisplayLink Dock Support on Debian (Wayland Compatible)

This guide sets up **DisplayLink drivers** for external monitors and docks on Debian systems running **Wayland**.

---

## 🧰 Requirements

You’ll need **git** and **curl** installed before proceeding:

```bash
sudo apt install -y git curl
```

---

## 🖥️ Install DisplayLink Driver (Adnan Hodzic Script)

Clone the official DisplayLink Debian installer repository and run the setup script:

```bash
git clone https://github.com/AdnanHodzic/displaylink-debian.git
cd displaylink-debian
sudo ./displaylink-debian.sh
```

This script automatically downloads the latest DisplayLink driver, compiles required kernel modules, and configures system services.

---

## 🧠 Notes

- Works well on Debian 12 / 13 under **Wayland**.  
- The repository link: [AdnanHodzic/displaylink-debian](https://github.com/AdnanHodzic/displaylink-debian)  
- After installation, reboot your system and connect the dock.  
- Check that the DisplayLink service is running with:  

```bash
systemctl status displaylink-driver
```

---

**Author:** Noah Lanning  
**Last Updated:** October 2025
