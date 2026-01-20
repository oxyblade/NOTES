## PACKAGES

--- Primary SYSTEM Packages (APT) ---

GUI Packages:
```
sudo apt-get install gnome-tweaks synaptic gnome-extensions-app gnome-firmware firewall-config dconf-editor gparted
```

Utils Packages:
```
sudo apt-get install nvme-cli smartmontools flatpak inxi fastfetch neofetch cpufetch duf lnav lshw speedtest-cli whatweb nethogs nload iotop mc pv mtr pwgen nmon bmon nmap iperf whowatch iftop lm-sensors git htop curl traceroute whois net-tools sslscan dnsmap dnsenum gdu nvtop atop btop bat lsd
```

Misc Packages:
```
sudo apt-get install nvidia-smi nvidia-xconfig composer gcc make cmake autoconf meson [rar unrar p7zip]
```

--- PHP: Local Server ---
sudo apt-get install php
sudo apt-get install php-apache php-cgi php-gd php-embed php-imagick php-redis php-snmp
php -v
php -m

___

--- OPTIONAL packages (APT) ---
gufw iostat wireguard ttf-mscorefonts-installer

--- Launch Appimage Apps ---
sudo apt-get install libfuse2t64

--- Apache Local Server ---
sudo apt-get install php
sudo apt-get install php8.1-mbstring php8.1-cgi php8.1-zip php8.1-xml php8.1-gd

--- H.264 (High Profile) Decoder & Multimedia Codecs ---
Ubuntu App Center - GStreamer Multimedia Codecs
(ugly, ffmpeg, base, good, GL, ALSA, X11 and Pango)

Alternative:
Ubuntu App Center - GStreamer plugins from the "bad" set
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install gstreamer1.0-plugins-bad
sudo apt-get install ffmpeg

--- MISC ---
gnome-system-tools
hwinfo dmidecode cpuid systemd-coredump gdb hardinfo fping
ghex jpegoptim gtkhash dialog ffmpeg
wig testssl.sh dmitry httpie
mailutils (-> for smartmontools)
nvidia-settings

___

## KVM VM
sudo apt-get install virt-manager bridge-utils virt-viewer libguestfs
[ qemu-system-x86 libvirt-daemon libvirt-clients (build-essential gcc) ]

sudo systemctl enable libvirtd.service
sudo systemctl start libvirtd.service
sudo usermod -a -G libvirt $USER [sudo gpasswd -a andrew libvirt (Alternative: kvm)]
[ sudo gpasswd -a andrew libvirt (Alternative: kvm) ] -- Alternative method
groups andrew
systemctl status libvirtd.service
kvm-ok
reboot

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
sudo apt-get install spice-vdagent

___

--- For Compile From SOURCES ---
sudo apt-get install gcc make cmake -y (libx11-dev)
sudo apt-get install libgtk-3-dev libpolkit-gobject-1-dev

--- Secondary ---
sudo apt-get install gdebi
sudo apt-get install gsmartcontrol hddtemp chrome-gnome-shell
sudo apt-get install libqt5pas-dev (For QT Double Commander)

--- NVMe S.M.A.R.T. ---
sudo apt-get install nvme-cli  
sudo nvme list  
sudo nvme smart-log /dev/nvme0  
sudo smartctl -iA /dev/nvme0

--- Remote access to Android ---
Share Files between Linux and Android by Wireless

Install on Linux:
sudo apt-get install openssh-client openssh-server

--- VMware VM ---
wget http://nz2.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1f-1ubuntu2.16_amd64.deb
sudo dpkg -i libssl1.1_1.1.1f-1ubuntu2.16_amd64.deb

--- Check dependencies ---
ldd /usr/sbin/vmware-authdlauncher

--- Services ---
sudo /etc/init.d/vmware status
sudo /etc/init.d/vmware restart

Guest Machine (Open VMware Tools - Drivers):
sudo apt-get install open-vm-tools

--- Uninstall ---
sudo vmware-installer -u vmware-player

___

### GRUB
--- grub-customizer (GUI to configure GRUB2 and BURG) ---
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

--- Mainline Ubuntu Kernel ---
sudo add-apt-repository ppa:cappelikan/ppa
sudo apt-get update
sudo apt-get install mainline
https://github.com/bkw777/mainline

___

### YARN (OLD KEY)
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt-get update
sudo apt-get install yarn

___

## FAVORITES PACKAGES
stacer - Linux system optimizer and monitoring
endeavour - TO DO, personal task manager
gpick - Color picker
usb-creator-gtk (usb-creator-common) - Create a startup disk using a CD or disc image
xfburn -  Burning CDs and DVDs
pavucontrol - Extended PulseAudio Volume Control
glances - Curses-based monitoring tool
indicator-multiload - System load indicator
plank - Elegant, simple, clean DOCK
aircrack-ng - Wireless WEP/WPA cracking utilities
preload - Preload applications that users run, and fetches binaries and dependencies into memory
kazam - Screencast
rtorrent - Terminal Torrent
ark - Archive Manager
iftop - Displays network usage
openarena - Quake 3 Arena

## SNAP
--- Delete SNAP System ---
sudo snap remove --purge firefox
sudo snap remove --purge snap-store
sudo snap remove --purge gnome-3-38-2004
sudo snap remove --purge gtk-common-themes
sudo snap remove --purge snapd-desktop-integration
sudo snap remove --purge hunspell-dictionaries-1-7-2004
sudo snap remove --purge bare
sudo snap remove --purge core20
sudo snap remove --purge snapd
sudo apt-get remove gnome-software-plugin-snap

sudo systemctl stop snapd.socket
sudo systemctl stop snapd.service
sudo systemctl stop snapd.seeded.service
sudo systemctl disable snapd.socket
sudo systemctl disable snapd.service
sudo systemctl disable snapd.seeded.service

sudo apt-get autoremove --purge snapd
sudo apt-get remove --purge snapd
sudo apt-get remove --autoremove snapd
sudo apt-get purge snapd
sudo rm -rf /var/cache/snapd
sudo rm -rf /snap
sudo rm -rf snap

sudo nano /etc/apt/preferences.d/nosnap.pref
Add text:
Package: snapd
Pin: release a=*
Pin-Priority: -10

sudo apt-get update
sudo apt-mark hold snapd

--- REVERT BACK SNAP System ---
sudo rm /etc/apt/preferences.d/nosnap.pref
sudo apt-get update && sudo apt-get upgrade
sudo snap install snap-store
sudo apt install firefox

--- Delete Snap App ---
sudo systemctl --failed
sudo systemctl status snap-firefox-1943.mount

sudo snap disable firefox
sudo snap remove --purge firefox
sudo rm -r /snap/firefox
sudo rm -r /etc/firefox
sudo rm -r /var/lib/snapd/snaps/firefox_1918.snap
sudo rm -r /var/lib/snapd/seed/snaps/firefox_1635.snap
sudo rm /etc/systemd/system/snap-firefox-1943.mount

## SERVER
sudo apt-get install apache2 libapache2-mod-php
sudo apt-get install mysql-server
sudo apt install sudo apt-get install php7.4 php7.4-{xml,mysql,zip,intl,imap,ldap,gd,cli,bz2,curl,mbstring,pgsql,opcache,soap,cgi,imagick,xdebug}
sudo apt-get install phpmyadmin
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash - [ OR ] sudo apt-get install nodejs
sudo apt-get install npm

System node_module pathes:
/usr/lib/node_modules
/usr/local/lib/node_modules

## MISC
--- QT Settings ---
sudo apt-get install libxcb-xinerama0

sudo nano /etc/environment
Add Line:
QT_QPA_PLATFORM=xcb

QT DEBUG
export QT_DEBUG_PLUGINS=1

sudo apt-get install qt6-qpa-plugins
sudo apt-get install libxkbcommon-x11-de

--- Use QT5 GTK theme ---
sudo apt-get install qt5-style-kvantum qt5ct
