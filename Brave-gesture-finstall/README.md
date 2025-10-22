# Brave Browser Setup (Wayland + Gesture Optimization)
This guide covers installing Brave Browser on Debian-based systems and enabling Wayland support for smooth touchpad gestures and proper overscroll navigation.

## 1. Install Curl (if not already installed)
Brave’s installer is fetched via Curl. Install it first:
sudo apt install curl

## 2. Install Brave Browser
Run the official Brave installation script:
curl -fsS https://dl.brave.com/install.sh | sh
This will add Brave’s repository, import its signing key, and install the browser.

## 3. Enable Wayland and Touchpad Gestures
Edit the Brave desktop entry so it launches with Wayland and gesture support enabled:
sudo nano /usr/share/applications/brave-browser.desktop

Find the line starting with Exec= and replace it with:
Exec=/usr/bin/brave-browser-stable %U --ozone-platform=wayland --enable-features=TouchpadOverscrollHistoryNavigation
Save the file and exit.

## 4. If Using Flatpak Instead
If Brave was installed via Flatpak, edit this file instead:
nano ~/.local/share/applications/com.brave.Browser.desktop

Then replace the Exec= line in the same way:
Exec=/usr/bin/brave-browser-stable %U --ozone-platform=wayland --enable-features=TouchpadOverscrollHistoryNavigation

## 5. Verify Wayland Support
In Brave, go to:
brave://flags
Set “Preferred Ozone Platform” to either:
- Wayland — for full Wayland-native rendering, or
- Auto — lets Brave detect the optimal backend automatically.
Restart Brave after changing the flag.

## Summary
- Curl is required to fetch Brave’s installer.
- The --ozone-platform=wayland flag enables native Wayland support.
- The --enable-features=TouchpadOverscrollHistoryNavigation flag enables smooth two-finger back/forward navigation.
- Works best on GNOME Wayland and Framework laptops with precision touchpads.

Author: Noah Lanning
Last Updated: October 2025
License: MIT (optional)
