### *SETTINGS*

**Linux Config**
Change the drive location for GNOME Boxes VMs:
```
mv ~/.local/share/gnome-boxes /mnt/HDD_2/GnomeBoxes
ln -s /mnt/SEAGATE/GnomeBoxes/gnome-boxes ~/.local/share/gnome-boxes
```

___

SPICE - solution for remote access to virtual machines:
https://www.spice-space.org/download.html

**Linux Client**
sudo apt-get install spice-vdagent (spice-webdavd)

**Windows Client**
Windows guest tools - spice-guest-tools:
https://www.spice-space.org/download.html#windows-binaries

**Windows NSIS installer for VirtIO/QXL guest drivers and SPICE guest agent**
https://gitlab.freedesktop.org/spice/win32/spice-nsis

UsbDk - A Windows filter driver developed for Spice USB redirection
(windows client side) - UsbDk_1.0.22_x64.msi

