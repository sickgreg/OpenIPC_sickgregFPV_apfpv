# Flash Ready-to-Fly FW to VTX

### 1. Flash firmware  
If your VTX has an Internet connection, SSH in and paste:  
```bash
curl -L -o /tmp/openipc.ssc338q-nor-apfpv-greg07.tgz https://github.com/sickgreg/OpenIPC_sickgregFPV_apfpv/raw/main/openipc.ssc338q-nor-apfpv-greg07.tgz && sysupgrade --archive=/tmp/openipc.ssc338q-nor-apfpv-greg07.tgz -f -n
```

Or, manually copy the `.tgz` file to `/tmp` on the VTX and run:  
```bash
sysupgrade --archive=/tmp/openipc.ssc338q-nor-apfpv-greg07.tgz -f -n
```

>  **Note:** Very old firmware may not open `.tgz` archives.  
If it fails, run this first:  
```bash
sysupgrade -k -r -n
```

---

### 2. **Unplug the Ethernet cable and reboot (again)**  
This is important — don’t skip it.

---

### 3. Connect to the VTX  
- The hotspot *should* come up:  
  - **SSID:** `OpenIPC`  
  - **Password:** `12345678`  

- Connect using your phone **or** `nmtui` on the Radxa.  
  - Recommended: use an **external adapter** (e.g. `bl-m8812eu2`)  
  - Radxa internal Wi-Fi can work, just not well.

- Once connected:  
  - On **Android**, run **PixelPilot** → video should start.  
  - On **Radxa**, run **pixelpilot_rk** → video should display.

> 📡 You can reach the VTX:  
- Over the air at **`192.168.0.1`**  
- Or re-plug Ethernet after AP has initialized at **`<VTX-LAN-ip>`**

---

### 4. Access the WebUI  
- Open:  
  - `http://192.168.0.1` (Wi-Fi)  
  - `http://<VTX-LAN-ip>` (Ethernet)  

<p align="center">
  <a href="https://github.com/user-attachments/assets/dfbd0432-2a15-4393-91a7-de0430bd95b9">
    <img src="https://github.com/user-attachments/assets/dfbd0432-2a15-4393-91a7-de0430bd95b9" width="400"/>
  </a>
</p>

---

### Notes  
- **20 MHz channels** use a single number (e.g. `36`)  
- **40 MHz channels** use two numbers (e.g. `36_40`)  

- Press **Apply** to negotiate a new channel (**EU wlan**)  
- Use **Forcing** for **AU wlan**  

- Video mode reports correctly after setting your first mode  
- Sometimes the WebUI may break the connection — if so, just **restart the VTX**  
