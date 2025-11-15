## PACKAGES

--- Primary SYSTEM Packages (Pacman) ---

GUI Packages:
```
sudo pacman -S dconf-editor gparted
```

Utils Packages:
```
sudo pacman -S base-devel fastfetch neofetch cpufetch duf lnav lshw speedtest-cli nethogs nload iotop mc pv pwgen nmon bmon nmap iperf whowatch iftop net-tools mtr sslscan gdu nvtop htop atop btop bat lsd
```

Misc Packages:
```
sudo pacman -S nvme-cli smartmontools nvidia-smi nvidia-xconfig manjaro-log-helper lsof sbctl composer libxcrypt-compat libnsl autoconf meson [unrar p7zip]
```

--- PHP: Local Server ---
sudo pacman -S php
sudo pacman -S php-apache php-cgi php-gd php-embed php-imagick php-redis php-snmp
php -v
php -m

--- OPTIONAL packages (Pacman) ---
gtk2 wireguard-tools apache adw-gtk3-theme cabextract xorg-x11-font-utils fontconfig firewalld

--- AUR (Pamac GUI) (Optional) ---
ttf-ms-fonts 			2.0-12
whatweb 				0.5.5-1
dnslookup-bin 			1.10.0-1
freedownloadmanager 	6.21.0.5639-1
pktstat-git 			1.8.5.r11.g1289b1d-1
pktstat 				1.8.5-3 [ Failed to build pktstat ]

Manjaro MINIMAL ISO:
sudo pacman -S git baobab gufw inxi htop curl

[ KDE DE: sudo pacman -S gnome-disk-utility baobab gnome-logs ]

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
gnome-system-tools rar unrar p7zip bpytop btop
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

____

## FAVORITES PACKAGES
sbctl - Secure Boot Manager
usb-creator - Create bootable USB from a LiveCD or disc image of Ubuntu
stacer-bin - Linux system optimizer and monitoring [pamac]
gpick - Color picker
xfburn -  Burning CDs and DVDs
glances - Curses-based monitoring tool
plank - Elegant, simple, clean DOCK
aircrack-ng - Wireless WEP/WPA cracking utilities
preload - Makes applications run faster by prefetching binaries and shared objects [pamac]

## MISC
--- QT ---  
sudo nano /etc/environment  
Add Line:  
QT_QPA_PLATFORM=xcb

QT Debug:  
export QT_DEBUG_PLUGINS=1

