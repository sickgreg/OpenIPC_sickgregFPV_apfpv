Flash ready-to-fly fw to VTX

1. If VTX has Internet connection, SSH in and paste this:
```
curl -L -o /tmp/openipc.ssc338q-nor-apfpv-greg07.tgz https://github.com/sickgreg/OpenIPC_sickgregFPV_apfpv/raw/main/openipc.ssc338q-nor-apfpv-greg07.tgz && \
sysupgrade --archive=/tmp/openipc.ssc338q-nor-apfpv-greg07.tgz -f -n
```

Or manually copy .tgz to VTX `/tmp` and run `sysupgrade --archive=/tmp/openipc.ssc338q-nor-apfpv-greg07.tgz -f -n`


Note: Very old fw can't open .tgz archive.  If it fails, run `sysupgrade -k -r -n` first

2. Unplug Ethernet cable and reboot (again)
3. Hotspot *should* come up - default ssid is OpenIPC, 12345678.  Find it with your phone or `nmtui` command on radxa -- connect using external (recommend: bl-m8812eu2) adapter, not radxa internal wifi, though it can work to a degree.

Run pixelpilot on Android device and video *should* start

or

Radxa running pixelpilot_rk *should* start displaying video


You may reach the VTX over the air at `192.168.0.1`, or re-plug Ethernet after AP has initialized at `<VTX-LAN-ip>`

4. Visit webUI, aalinkFPV page `http://192.168.0.1` over wifi, or `http://<VTX-LAN-ip>` over Ethernet

<p align="center">
  <a href="https://github.com/user-attachments/assets/dfbd0432-2a15-4393-91a7-de0430bd95b9">
    <img src="https://github.com/user-attachments/assets/dfbd0432-2a15-4393-91a7-de0430bd95b9" width="400"/>
  </a>
</p>



- 20MHz channels are single numbers, eg `36`

- 40Mhz channels are two numbers, eg `36_40`

Press Apply to negotiate new channel (EU wlan) --  Forcing is for AU wlan
- Video mode reports correctly after setting your first mode

- Sometimes webUI can break the connection.  Please restart VTX if this occurs
