# MediaTek Wi-Fi Driver and Firmware Setup (Debian 13)

This guide explains how to install **MediaTek Wi-Fi adapter firmware** (including MT7922) on Debian-based systems.

---

## 🌐 Requirements

Make sure you have an active internet connection.  
If your repositories do not include non-free firmware, you may need to enable them first.  

Search for the package online if needed:  
[Debian Package: firmware-misc-nonfree](https://packages.debian.org/search?keywords=firmware-misc-nonfree)

---

## 🧰 Install Official Firmware Package

```bash
sudo apt update
sudo apt install firmware-misc-nonfree
```

This package provides firmware for many MediaTek chipsets.

---

## 🧩 Alternative: Manual Firmware Installation (for MT7922 or Similar)

If Debian’s firmware package does not include your adapter (e.g., MT7922), you can install it manually using the community-maintained drivers.

Reference: [morrownr USB-WiFi Repository](https://github.com/morrownr/USB-WiFi/blob/main/home/How_to_Install_Firmware_for_Mediatek_based_USB_WiFi_adapters.md)

---

### Steps for MT7922 Firmware

1. Download the firmware from the kernel repository:  

```bash
sudo wget https://github.com/NoahsArch/noFUS/raw/main/Debian-Mediatek-MT7922/WIFI_MT7922_patch_mcu_1_1_hdr.bin -O WIFI_MT7922_patch_mcu_1_1_hdr.bin
sudo wget https://github.com/NoahsArch/noFUS/raw/main/Debian-Mediatek-MT7922/WIFI_RAM_CODE_MT7922_1_1.bin -O WIFI_RAM_CODE_MT7922_1_1.bin
sudo wget https://github.com/NoahsArch/noFUS/raw/main/Debian-Mediatek-MT7922/BT_RAM_CODE_MT7922_1_1.bin -O BT_RAM_CODE_MT7922_1_1.bin
```

2. Create the firmware directory if it doesn’t exist:  

```bash
sudo mkdir -p /lib/firmware/mediatek
sudo mkdir -p /lib/firmware/mediatek
```

3. Copy the downloaded files into it:  

```bash
sudo cp WIFI_MT7922_patch_mcu_1_1_hdr.bin /lib/firmware/mediatek/
sudo cp WIFI_RAM_CODE_MT7922_1_1.bin /lib/firmware/mediatek/
sudo cp BT_RAM_CODE_MT7922_1_1.bin /lib/firmware/mediatek/
```

4. Reboot your system:  

```bash
sudo reboot
```

5. After reboot, check that the driver loaded successfully:  

```bash
sudo dmesg | grep mt7922
```

You should see messages confirming the firmware was loaded.

---

## ✅ Summary

- Use Debian’s `firmware-misc-nonfree` package when possible.  
- If missing, download the MT7922 firmware manually from the official Linux firmware repository.  
- Files go into `/lib/firmware/mediatek/`.  
- Reboot after installation to activate the firmware.

---

**Author:** Noah Lanning  
**Last Updated:** October 2025
