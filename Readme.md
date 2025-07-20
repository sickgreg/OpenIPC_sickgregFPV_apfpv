Connect VTX via Ethernet
Flash this firmware by copy/pasting this to VTX command prompt
```
curl -L -o /tmp/tmpFW.tgz https://github.com/sickgreg/OpenIPC_sickgregFPV_apfpv/raw/main/openipc.ssc338q-nor-apfpv-viktorJul14.tgz
sysupgrade --archive=/tmp/tmpFW.tgz -f -n
```

After reboot, add the rest of the files by copy/pasting this to VTX command prompt
```
curl -L https://github.com/sickgreg/OpenIPC_sickgregFPV_apfpv/raw/main/overlay.tar | tar -C /overlay -xf -
```

Disconnect Ethernet !
Reboot
Connect to Access Point

You can use `nmtui` on radxa to connect / manage AP

