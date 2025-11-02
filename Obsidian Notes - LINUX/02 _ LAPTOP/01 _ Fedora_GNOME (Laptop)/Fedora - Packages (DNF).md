## PACKAGES

--- Primary SYSTEM Packages (DNF) ---

GUI Packages:
```

```

Utils Packages:
```

```

Misc Packages:
```

```

CD / DVD / Blu-ray Burning Applications:
k3b — CD/DVD/Blu-ray burning application (sudo chmod 4755 /usr/bin/wodim)
xfburn — CD burning tool




___

## KVM VM
sudo dnf install virt-manager bridge-utils virt-viewer libguestfs

sudo systemctl enable libvirtd.service
sudo systemctl start libvirtd.service
sudo usermod -a -G libvirt $USER
[ sudo gpasswd -a andrew libvirt (Alternative: kvm) ] -- Alternative method
groups andrew
systemctl status libvirtd.service

--- Permission denied: Open disk image from USB / External devices ---
sudo nano /etc/libvirt/qemu.conf
Uncomment user / group to work as root:
user = "root"
group = "root"
~~swtpm_user = "root"~~  
~~swtpm_group = "root"~~
security_driver = "none"
sudo nano /etc/libvirt/network.conf --> firewall_backend = "iptables" (Manjaro Linux)

sudo systemctl restart libvirtd.service
systemctl status libvirtd.service
reboot

Guest Machine (Spice agent for Linux - For X-session
Copy / Past, change screen resolution and etc.):
sudo dnf install spice-vdagent (xf86-video-qxl)

___

--- For Compile From SOURCES ---
sudo dnf install cmake gcc make

--- PACKAGES - Misc ---
smartmontools lsof neofetch traceroute whois net-tools gpick gnome-system-tools bpytop btop
hwinfo dmidecode cpuid systemd-coredump gdb hardinfo fping
ghex jpegoptim gtkhash dialog ffmpeg
wig testssl.sh dmitry httpie
mailutils
nvidia-settings

--- NVMe S.M.A.R.T. ---
sudo dnf install nvme-cli  
sudo nvme list  
sudo nvme smart-log /dev/nvme0  
sudo smartctl -iA /dev/nvme0

___

## FAVORITES PACKAGES
sbctl - Secure Boot Manager
usb-creator - Create bootable USB from a LiveCD or disc image of Ubuntu
stacer-bin - Linux system optimizer and monitoring [pamac]
gpick - Color picker
xfburn - Burning CDs and DVDs
glances - Curses-based monitoring tool
plank - Elegant, simple, clean DOCK
aircrack-ng - Wireless WEP/WPA cracking utilities
preload - Makes applications run faster by prefetching binaries and shared objects [pamac]

___

## MISC
sudo nano /etc/environment
Add Line:
QT_QPA_PLATFORM=xcb

QT DEBUG
export QT_DEBUG_PLUGINS=1
