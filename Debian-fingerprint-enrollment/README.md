# Fingerprint Authentication Setup (Debian 13)

This guide enables **fingerprint authentication** on Debian using `fprintd` and PAM integration.

Reference: [Debian Wiki - Fingerprint Authentication](https://wiki.debian.org/SecurityManagement/fingerprint%20authentication)

---

## 🧰 Install Required Packages

```bash
sudo apt install fprintd libpam-fprintd
```

---

## ✋ Enroll Your Fingerprint

If fingerprint enrollment is not available in your user GUI, enroll manually:

```bash
fprintd-enroll
```

Follow the prompts to register one or more fingers.

---

## ✅ Done

Once enrolled, fingerprint login should work for:
- Display Manager (GNOME, GDM, etc.)
- `sudo` authentication
- Screen unlock

---

**Author:** Noah Lanning  
**Last Updated:** October 2025
