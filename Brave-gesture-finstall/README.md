# Brave – Wayland & Gesture Setup

This guide installs **Brave Browser** and enables **Wayland** + **touchpad overscroll history navigation** for smooth, native gestures on GNOME.

---

## 🧰 Setup & Dependencies

Install Curl (used by Brave's official installer):

```bash
sudo apt install -y curl
```

---

## 🦁 Install Brave (Official Script)

Run Brave’s installer (adds repo, key, and installs Brave Stable):

```bash
curl -fsS https://dl.brave.com/install.sh | sh
```

After installation, you should have the desktop entry at:

```
/usr/share/applications/brave-browser.desktop
```

---

## ⚙️ Enable Wayland & Overscroll Gestures

Edit Brave’s desktop entry to force Wayland and enable back/forward two‑finger swipe:

```bash
sudo nano /usr/share/applications/brave-browser.desktop
```

Replace the `Exec=` line with: (You can also just comment out the default and add in this)

```ini
Exec=/usr/bin/brave-browser-stable %U --ozone-platform=wayland --enable-features=TouchpadOverscrollHistoryNavigation
```

Save and exit.

> Tip: If you prefer creating a user override instead of editing the system file, copy it first:
> ```bash
> cp /usr/share/applications/brave-browser.desktop ~/.local/share/applications/brave-browser.desktop
> nano ~/.local/share/applications/brave-browser.desktop
> ```

---

## 📦 If You Installed Brave via Flatpak

Edit the Flatpak desktop entry instead:

```bash
nano ~/.local/share/applications/com.brave.Browser.desktop
```

Update the `Exec=` line the same way:

```ini
Exec=/usr/bin/brave-browser-stable %U --ozone-platform=wayland --enable-features=TouchpadOverscrollHistoryNavigation
```

> Note: Some Flatpak wrappers use a different `Exec` path (e.g., `flatpak run com.brave.Browser`). Keep that path but append the same flags above.

---

## 🧠 Verify Wayland Rendering

Open Brave flags:

```
brave://flags
```

Set **Preferred Ozone Platform** to **“Wayland”** (or **“Auto”**). Restart Brave.

You can also confirm Wayland at `brave://gpu` (look for **Ozone platform: wayland**).

---

---

**Author:** Noah Lanning  
**Last Updated:** Oct 2025
