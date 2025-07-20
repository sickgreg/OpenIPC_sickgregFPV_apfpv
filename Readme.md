# 🚀 OpenIPC AP-FPV VTX Setup Guide

## 1. 🔌 Connect VTX via Ethernet

## 2. 🔧 Flash Firmware

Paste the following into the **VTX command prompt(SSH)**:

```sh
curl -L -o /tmp/tmpFW.tgz https://github.com/sickgreg/OpenIPC_sickgregFPV_apfpv/raw/main/openipc.ssc338q-nor-apfpv-viktorJul14.tgz
sysupgrade --archive=/tmp/tmpFW.tgz -f -n
```

> ⚠️ Don't forget to press Enter to executefinal line.  VTX will reboot. Close the SSH session and start a new one for the next step

---

## 3. 📦 Add Overlay Files

Paste this into the **VTX command prompt (SSH)**:

```sh
curl -L https://github.com/sickgreg/OpenIPC_sickgregFPV_apfpv/raw/main/overlay.tar | tar -C /overlay -xf -
```

---

## 4. 🔌 Disconnect Ethernet

Then:

```sh
reboot
```

---

## 5. 📶 Connect to Access Point

Once rebooted, connect to the VTX's Wi-Fi access point.

> 🛠️ On **Radxa or similar systems**, use `nmtui` for easy network setup:

```sh
nmtui
```

---

# ⚙️ Advanced: Test OSD Without Flight Controller

To force text OSD for testing, run:

```sh
sed -i '/msposd/ s/\(-b 115200\)/\1 -x 99/; s|> /dev/null|> /dev/null 2>\&1|; s|\$size|1920x1080|' /etc/init.d/S99msposd
/etc/init.d/./S99msposd stop
/etc/init.d/./S99msposd start
```

---
