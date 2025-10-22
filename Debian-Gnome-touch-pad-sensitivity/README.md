# libinput-config: Scroll Speed Tuning (Framework / Debian)

Steps to build and install **libinput-config** and set sane scroll factors for touchpad sensitivity.

---

## 🧰 Install Dependencies

```bash
sudo apt update
sudo apt install -y meson libsystemd-dev gcc ninja-build git pkg-config libinput-dev
```

---

## ⚙️ Create libinput.conf

```bash
sudo nano /etc/libinput.conf
```

Paste (or update) the following and save:

```
# .2 is good — stop thinking you need to change it, dummy
scroll-factor-x=0.2
scroll-factor-y=0.2
```

---

## 🛠️ Build & Install libinput-config

```bash
cd ~
git clone https://gitlab.com/warningnonpotablewater/libinput-config.git
cd libinput-config
meson build
cd build
ninja
sudo ninja install
```

---

## 🔁 Reboot

```bash
sudo reboot
```

---

## 🙌 Credit

Guide inspired by:  
https://www.reddit.com/r/framework/comments/1jbi9if/touch_pad_scrolling_too_sensitive_on_ubuntu/
