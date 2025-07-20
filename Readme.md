Connect VTX via Ethernet

Flash firmware by copy/pasting this to VTX command prompt
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

Consider using `nmtui` (for radxa) to connect / manage AP





--------------- Advanced ---------------------




To test OSD with no flight controller, run the following:

```
sed -i '/msposd/ s/\(-b 115200\)/\1 -x 99/; s|> /dev/null|> /dev/null 2>\&1|; s|\$size|1920x1080|' /etc/init.d/S99msposd
/etc/init.d/./S99msposd stop
/etc/init.d/./S99msposd start

```
