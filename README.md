# Flash Ready-to-Fly FW to VTX

### 1. Flash firmware (4 variants)
Pick the command that matches your SoC and WLAN driver set. Each command is a single line and uses a legacy-safe extraction method (`busybox gunzip ... | tar ... && sysupgrade --kernel --rootfs`), which should work on very old (factory) firmware too.

`normal` builds support: `8812eu`, `8812au`, `8812cu`
`_bu` builds support: `8812eu`, `8812au`, `8733bu` (replaces `8812cu`)

**SSC338Q normal (`greg10.1`)**
```bash
curl -L -o /tmp/openipc.ssc338q-nor-apfpv-greg10.1.tgz https://raw.githubusercontent.com/sickgreg/OpenIPC_sickgregFPV_apfpv/main/openipc.ssc338q-nor-apfpv-greg10.1.tgz && busybox gunzip -c /tmp/openipc.ssc338q-nor-apfpv-greg10.1.tgz | tar -xf - -C /tmp uImage.ssc338q rootfs.squashfs.ssc338q && sysupgrade --kernel=/tmp/uImage.ssc338q --rootfs=/tmp/rootfs.squashfs.ssc338q --force_all -n
```

**SSC338Q `_bu` (`greg10.1_bu`)**
```bash
curl -L -o /tmp/openipc.ssc338q-nor-apfpv-greg10.1_bu.tgz https://raw.githubusercontent.com/sickgreg/OpenIPC_sickgregFPV_apfpv/main/openipc.ssc338q-nor-apfpv-greg10.1_bu.tgz && busybox gunzip -c /tmp/openipc.ssc338q-nor-apfpv-greg10.1_bu.tgz | tar -xf - -C /tmp uImage.ssc338q rootfs.squashfs.ssc338q && sysupgrade --kernel=/tmp/uImage.ssc338q --rootfs=/tmp/rootfs.squashfs.ssc338q --force_all -n
```

**SSC30KQ normal (`greg10.1`)**
```bash
curl -L -o /tmp/openipc.ssc30kq-nor-apfpv-greg10.1.tgz https://raw.githubusercontent.com/sickgreg/OpenIPC_sickgregFPV_apfpv/main/openipc.ssc30kq-nor-apfpv-greg10.1.tgz && busybox gunzip -c /tmp/openipc.ssc30kq-nor-apfpv-greg10.1.tgz | tar -xf - -C /tmp uImage.ssc30kq rootfs.squashfs.ssc30kq && sysupgrade --kernel=/tmp/uImage.ssc30kq --rootfs=/tmp/rootfs.squashfs.ssc30kq --force_all -n
```

**SSC30KQ `_bu` (`greg10.1_bu`)**
```bash
curl -L -o /tmp/openipc.ssc30kq-nor-apfpv-greg10.1_bu.tgz https://raw.githubusercontent.com/sickgreg/OpenIPC_sickgregFPV_apfpv/main/openipc.ssc30kq-nor-apfpv-greg10.1_bu.tgz && busybox gunzip -c /tmp/openipc.ssc30kq-nor-apfpv-greg10.1_bu.tgz | tar -xf - -C /tmp uImage.ssc30kq rootfs.squashfs.ssc30kq && sysupgrade --kernel=/tmp/uImage.ssc30kq --rootfs=/tmp/rootfs.squashfs.ssc30kq --force_all -n
```

---

### 2. Connecting to apfpv Access Point
- Access point details:
- SSID: `OpenIPC`
- Password: `12345678`

#### Rockchip VRX (Radxa)
- Choose `apfpv` mode on your VRX (ground station) to connect.
- Recommended: adapter `bl-m8812eu2`.
- Connect Ethernet to home network. Open a web browser to `http://<your-VTX-LAN-ip>` and log in with `root` / `12345` for WebUI.

#### Android
- Disable auto-connect to other saved networks first.
- Join `OpenIPC` with password `12345678`.
- View stream in player such as `PixelPilot`.
- Open a web browser to `http://192.168.0.1` and log in with `root` / `12345` for WebUI.

#### Windows
- On your chosen Wi-Fi adapter, disable auto-connect to other saved networks first.
- Connect to Wi-Fi network `OpenIPC` using password `12345678`.
- If it stops on channel initialization or channel change, disconnect and reconnect.
- Open your player (for example `QGroundControl` set to UDP h265) for video. Browse to `http://192.168.0.1` and log in with `root` / `12345` for WebUI.

#### Linux
- On your chosen Wi-Fi adapter, disable auto-connect to other saved networks first.
- Connect to Wi-Fi network `OpenIPC` using password `12345678`.
- If it stops on channel initialization or channel change, disconnect and reconnect.
- Open your player (for example `QGroundControl` set to UDP h265) for video. Browse to `http://192.168.0.1` and log in with `root` / `12345` for WebUI.

#### Mac
- On your chosen Wi-Fi adapter, disable auto-connect to other saved networks first.
- Connect to Wi-Fi network `OpenIPC` using password `12345678`.
- If it stops on channel initialization or channel change, disconnect and reconnect.
- Open your player (for example `QGroundControl` set to UDP h265) for video. Browse to `http://192.168.0.1` and log in with `root` / `12345` for WebUI.
---

### WebUI Access Summary
- WLAN: `http://192.168.0.1` (login `root` / `12345`)
- Ethernet: `http://<VTX-LAN-ip>` (login `root` / `12345`)

<p align="center">
  <a href="https://github.com/user-attachments/assets/dfbd0432-2a15-4393-91a7-de0430bd95b9">
    <img src="https://github.com/user-attachments/assets/dfbd0432-2a15-4393-91a7-de0430bd95b9" width="400"/>
  </a>
</p>

---

### Notes
- WebUI includes 20/40/80 MHz options and dedicated channel selection.
- 20 MHz channels use one number (example: `36`).
- 40 MHz channels use two numbers (example: `36_40`).
- 80 MHz channels use the lowest and highest spanning channels (example: `36_48`).
- Press `Apply` to negotiate a new channel (normal WLAN).
- Use `Forcing` only for AU WLAN.
- Video mode reports correctly after first mode set.
- WebUI or changing of video modes may occasionally break connection; restart VTX if that happens.
