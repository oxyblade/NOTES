## PACKAGES

--- Primary SYSTEM Packages (Pacman) ---

GUI Packages:
```
sudo pacman -S dconf-editor gparted
```

Utils Packages:
```
sudo pacman -S base-devel inxi fastfetch neofetch cpufetch duf lnav lshw speedtest-cli nethogs nload iotop mc pv mtr pwgen nmon bmon nmap iperf whowatch iftop traceroute whois net-tools speedtest-cli smartmontools lsof sbctl manjaro-log-helper intel-gpu-tools sslscan sysstat htop atop btop bat lsd
```

Misc Packages:
```
sudo pacman -S composer libxcrypt-compat gtk2 libnsl meson [unrar p7zip]
```

CD / DVD / Blu-ray Burning Applications:
k3b — CD/DVD/Blu-ray burning application (sudo chmod 4755 /usr/bin/wodim)
xfburn — CD burning tool

--- PHP: Local Server ---
sudo pacman -S php
sudo pacman -S php-apache php-cgi php-gd php-embed php-imagick php-redis php-snmp
php -v
php -m

--- OPTIONAL packages (Pacman) ---
nvidia-smi nvidia-xconfig wireguard-tools xorg-xrandr apache

--- AUR (Pamac GUI) (Optional) ---
ttf-ms-fonts 			2.0-12
whatweb 				0.5.5-1
dnslookup-bin 			1.10.0-1
freedownloadmanager 	6.21.0.5639-1
pktstat-git 			1.8.5.r11.g1289b1d-1
pktstat 				1.8.5-3 [ Failed to build pktstat ]

--- Manjaro MINIMAL ISO ---
sudo pacman -S git baobab gufw inxi htop curl

___

## KVM VM

sudo pacman -S virt-manager bridge-utils virt-viewer libguestfs
(Manjaro MINIMAL ISO: qemu-desktop libvirt edk2-ovmf dnsmasq vde2)

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
sudo nano /etc/libvirt/network.conf --> firewall_backend = "iptables"

sudo systemctl restart libvirtd.service
systemctl status libvirtd.service
reboot

Guest Machine (Spice agent for Linux - For X-session
Copy / Past, change screen resolution and etc.):
sudo pacman -S spice-vdagent (xf86-video-qxl)

___

--- For Compile From SOURCES ---
sudo pacman -S cmake (Manjaro FULL ISO: gcc make - Have been installed)

___

--- PACKAGES - Misc ---
gnome-system-tools rar bpytop btop
hwinfo dmidecode cpuid systemd-coredump gdb hardinfo fping
ghex jpegoptim gtkhash dialog ffmpeg
wig testssl.sh dmitry httpie
mailutils
nvidia-settings

--- NVMe S.M.A.R.T. ---
sudo pacman -S nvme-cli  
sudo nvme list  
sudo nvme smart-log /dev/nvme0  
sudo smartctl -iA /dev/nvme0

___

## FAVORITES PACKAGES ####################

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