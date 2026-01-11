## *PRIMARY PACKAGES*

> ### ***GLOBAL***
> ***Installing Free and Nonfree Repositories:***
> Software app (Disabled by Default)
> ```
> https://rpmfusion.org/Configuration
> ```

> ### ***DESKTOP***
> **GUI Packages:**
> ```
> sudo dnf install gnome-tweaks gnome-themes-extra gnome-extensions-app file-roller gnome-firmware firewall-config seahorse dconf-editor gparted
> ```
> 
> **Utils Packages:**
> ```
> sudo dnf install inxi fastfetch cpufetch duf lnav lshw speedtest-cli whatweb nethogs nload iotop mc pv pwgen nmon bmon nmap iperf whowatch iftop sysstat sslscan dnsmap dnsenum gdu nvtop htop atop btop lsb_release yaru-icon-theme bat lsd hwinfo
> ```
> 
> **Misc Packages:**
> ```
> sudo dnf install composer libxcrypt-compat gtk2 libnsl autoconf meson unrar p7zip python3-pip nvidia-smi
> ```

> ### ***LAPTOP***
> **GUI Packages**
> ```
> sudo dnf install gnome-tweaks gnome-themes-extra gnome-extensions-app file-roller gnome-firmware firewall-config seahorse dconf-editor gparted brasero
> ```
> 
> **Utils Packages:**
> ```
> sudo dnf install inxi fastfetch cpufetch duf lnav lshw speedtest-cli whatweb nethogs nload iotop mc pv pwgen nmon bmon nmap iperf whowatch iftop sysstat sslscan dnsmap dnsenum gdu nvtop htop atop btop lsb_release yaru-icon-theme bat lsd hwinfo igt-gpu-tools
> ```
> 
> **Misc Packages:**
> ```
> sudo dnf install composer libxcrypt-compat gtk2 libnsl autoconf meson unrar p7zip python3-pip
> ```

**PHP (Local Server):**
```
sudo dnf install php
sudo dnf install php-cgi php-gd php-imagick php-redis php-snmp
php -v
php -m
```

**Compile From SOURCES:**
```
sudo dnf install cmake gcc-c++ gcc make
```

**CD / DVD / Blu-ray Burning Applications (LAPTOP):**
k3b — CD/DVD/Blu-ray burning application (sudo chmod 4755 /usr/bin/wodim)
xfburn — CD burning tool

> *DNF Packages (OPTIONAL):*
> nvidia-smi nvidia-xconfig egl-utils apache mtr wireguard-tools adw-gtk3-theme cabextract xorg-x11-font-utils fontconfig

_____

**KVM VM**
```
sudo dnf install virt-manager bridge-utils virt-viewer libguestfs
```

```
sudo systemctl enable libvirtd.service
sudo systemctl start libvirtd.service
sudo usermod -a -G libvirt $USER
```
*sudo gpasswd -a andrew libvirt (kvm) — Alternative method*
```
groups andrew
systemctl status libvirtd.service
```

Permission denied: Open disk image from USB / External devices:
```
sudo nano /etc/libvirt/qemu.conf
```
Uncomment user / group to work as root:
user = "root"
group = "root"
~~swtpm_user = "root"~~
~~swtpm_group = "root"~~
security_driver = "none"
sudo nano /etc/libvirt/network.conf --> firewall_backend = "iptables" (Manjaro Linux)

```
sudo systemctl restart libvirtd.service
systemctl status libvirtd.service
```
*reboot*

> Guest Machine (Spice agent for Linux - For X-session
> Copy / Past, change screen resolution and etc.):
> sudo dnf install spice-vdagent (xf86-video-qxl)

___

**Python packages:**

pip install pdf-watermark
python3 /home/andrew/.local/lib/python3.14/site-packages/pdf_watermark/watermark.py insert -o 0.1 -ha center -ts 100 . "Confidential"

____
## *FAVORITE PACKAGES*
sbctl - Secure Boot Manager (Manjaro Linux)
usb-creator - Create bootable USB from a LiveCD or disc image of Ubuntu
stacer-bin - Linux system optimizer and monitoring *(pamac)*
gpick - Color picker
xfburn - Burning CDs and DVDs
glances - Curses-based monitoring tool
plank - Elegant, simple, clean DOCK
aircrack-ng - Wireless WEP/WPA cracking utilities
preload - Makes applications run faster by prefetching binaries and shared objects *(pamac)*

___
## *Misc Packages (OPTIONAL)*
nvme-cli smartmontools lsof neofetch traceroute whois net-tools gpick gnome-system-tools bpytop btop
hwinfo dmidecode cpuid systemd-coredump gdb hardinfo fping
ghex jpegoptim gtkhash dialog ffmpeg
wig testssl.sh dmitry httpie
mailutils
nvidia-settings

**NVMe S.M.A.R.T.**
sudo dnf install nvme-cli
sudo nvme list
sudo nvme smart-log /dev/nvme0
sudo smartctl -iA /dev/nvme0

____
## *Misc Data*

--- QT ---
sudo nano /etc/environment
Add Line:
QT_QPA_PLATFORM=xcb

QT Debug:
export QT_DEBUG_PLUGINS=1