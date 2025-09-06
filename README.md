1. Copy .tgz fw file to VTX `/tmp`
2. Run ```sysupgrade --archive=/tmp/openipc.ssc338q-nor-apfpv-greg07.tgz -f -n```

Note: Very old fw can't open .tgz archive.  If it fails, run `sysupgrade -k -r -n` first

3. Unplug Ethernet cable and reboot again
4. Hotspot/AP *should* come up - default ssid is OpenIPC, 12345678.  Find it with your phone or `nmtui` command on radxa -- you want to connect radxa using your external bl-m8812eu2 adapter, not the radxa internal wifi - though it can work to a degree

You may reach the VTX either via the wifi connection `192.168.0.1`, or re-plug Ethernet after AP has initialized `<your LAN dhcp assigned ip>`

5. Visit webUI, aalinkFPV page `http://192.168.0.1` or `http://<VTX LAN ip>`

<a href="https://github.com/user-attachments/assets/dfbd0432-2a15-4393-91a7-de0430bd95b9">
  <img src="https://github.com/user-attachments/assets/dfbd0432-2a15-4393-91a7-de0430bd95b9" width="250"/>
</a>
