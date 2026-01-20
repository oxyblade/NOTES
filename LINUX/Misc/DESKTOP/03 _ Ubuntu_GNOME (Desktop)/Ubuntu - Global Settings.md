## Overall Settings
Terminal: Window Size: 150 x 40
Text Editor: Custom font: Monospace, 11

## LINUX BOOT OPTIONS
[ GENERAL Options ]
sudo nano /etc/default/grub

GRUB_TIMEOUT=3 (OR 1)
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3"
sudo update-grub

## RAM, SSD, HDD OPTIMIZATION (OPTIONAL)
sudo nano /etc/sysctl.d/99-sysctl.conf
sudo nano /etc/sysctl.conf (Alternative)
vm.swappiness=5

[ OR ]

vm.vfs_cache_pressure=1000
vm.dirty_background_ratio=50
vm.dirty_ratio=80
kernel.watchdog_thresh=30

man sysctl.conf
sysctl -p (Read values from file)

## FS FLAGS (OPTIONAL)
**BTRFS (NVME & SSD):**
compress=zstd:1,defaults,noatime,discard=async

**BTRFS (HDD):**
compress=zstd:1,defaults,noatime
compress=zstd:1,x-gvfs-show,defaults,noatime [ USB ]

**EXT4 (HDD & SSD):**
defaults,noatime,barrier=0

**FSTAB (/etc/fstab):**
```
LABEL=HDD_1 /mnt/HDD_1 btrfs nosuid,nodev,nofail,x-gvfs-show,compress=zstd:1 0 0
LABEL=USB_HDD_1 /mnt/USB_HDD_1 ext4 nosuid,nodev,nofail,noauto,x-gvfs-show,noatime,barrier=0 0 0
LABEL=USB_HDD_2 /mnt/USB_HDD_2 ext4 nosuid,nodev,nofail,noauto,x-gvfs-show,noatime,barrier=0 0 0
LABEL=USB_HDD_3 /mnt/USB_HDD_3 ext4 nosuid,nodev,nofail,noauto,x-gvfs-show,noatime,barrier=0 0 0
```

## SOUNDCARD - DISABLE AUTO SUSPEND (Powersave)
--- Method 1 (MAIN) ---
sudo nano /etc/modprobe.d/alsa-base.conf
Add the following line:
options snd_hda_intel power_save=0 power_save_controller=N

--- Method 2 (MAIN)---
sudo nano /etc/pulse/default.pa
Comment this string: load-module module-suspend-on-idle
reboot

--- CHECK FIX ---
cat /sys/module/snd_hda_intel/parameters/power_save
power_save 0

## LOGS OPTIMIZATION (OPTIONAL)
--- rsyslog ---
sudo nano /etc/logrotate.d/rsyslog
{
        rotate 4
        weekly
        maxsize 500M -> OPTIONAL
        missingok
        notifempty
        compress
        delaycompress
        sharedscripts
        postrotate
                /usr/lib/rsyslog/rsyslog-rotate
        endscript
}

sudo nano /etc/logrotate.conf

--- journalctl (EXT4) ---
sudo nano /etc/systemd/journald.conf
SystemMaxUse=500M

sudo journalctl --disk-usage
sudo journalctl --vacuum-size=100M
sudo journalctl --verify

Forced clean file:
sudo su
echo "" > /var/log/syslog
reboot

## Stop, Disable & Mask systemd Services
sudo systemctl status sssd.service
sudo systemctl status NetworkManager-wait-online.service
sudo systemctl status ModemManager.service

sudo systemctl stop sssd.service
sudo systemctl stop NetworkManager-wait-online.service
sudo systemctl stop ModemManager.service

sudo systemctl disable sssd.service
sudo systemctl disable NetworkManager-wait-online.service
sudo systemctl disable ModemManager.service

sudo systemctl mask sssd.service
sudo systemctl mask NetworkManager-wait-online.service
sudo systemctl mask ModemManager.service

Check masked list:
systemctl list-unit-files --state=masked

## Snap refresh timer
sudo snap set system refresh.timer=sat1,11:00			- Once in month
sudo snap set system refresh.timer=mon-sun,11:00		- Every day

## GNOME Settings (dconf-editor)

Terminal:  
dconf-editor /org/gnome/settings-daemon/plugins/power/sleep-inactive-ac-timeout - '0'  
dconf-editor /org/gnome/settings-daemon/plugins/power/sleep-inactive-ac-type - 'nothing'  
dconf-editor /org/gnome/settings-daemon/plugins/power/sleep-inactive-battery-timeout - '0'  
dconf-editor /org/gnome/settings-daemon/plugins/power/sleep-inactive-battery-type - 'nothing'

___
## dconf-editor - GNOME settings
dconf-editor /org/gnome/shell/extensions/dash-to-dock/click-action 	- 'minimize'
dconf-editor /org/gnome/mutter/center-new-windows 					- 'True'
dconf-editor /org/gnome/mutter/attach-modal-dialogs 					- 'False'

dconf-editor /org/gnome/settings-daemon/plugins/power/lid-close-battery-action - 'nothing'
dconf-editor /org/gnome/settings-daemon/plugins/power/lid-close-ac-action - 'nothing'
dconf-editor /org/gnome/shell/extensions/dash-to-dock/transparency-mode - 'DYNAMIC'
dconf-editor /org/gnome/desktop/wm/keybindings/switch-input-source-backward - Use default value
dconf-editor /org/gnome/desktop/interface/cursor-theme - DMZ-White
dconf-editor /org/gnome/desktop/calendar/show-weekdate - True

dconf-editor /org/gnome/shell/extensions/dash-to-dock/show-mounts - False
####### dconf-editor /org/gnome/shell/extensions/dash-to-dock/extend-height - False
####### dconf-editor /org/gnome/shell/extensions/dash-to-dock/unity-backlit-items - True

___
## MISC
--- Nautilus DEFAULT file manager ---
To set Nautilus file manager as the DEFAULT file manager type:
xdg-mime default org.gnome.Nautilus.desktop inode/directory

--- GNOME Settings ---
dconf-editor /org/gnome/mutter/center-new-windows - 'True'

--- GSConnect ---
Firewall: Rules -> Rules -> Add a rule -> Simple -> Name (GSConnect) -> Port (1716 , 1739)

## Laptops: Disable Suspend when Lid Is Closed
sudo nano /etc/systemd/logind.conf

Uncomment lines:
HandleLidSwitch=ignore
HandleLidSwitchDocked=ignore
LidSwitchIgnoreInhibited=yes

Description:
HandleLidSwitch=ignore to do nothing
HandleLidSwitch=poweroff to shutdown computer when lid is closed
HandleLidSwitch=hibernate to hibernate computer when lid is closed

___

## SECONDARY
--- Disable WAYLAND ---
sudo nano /etc/gdm3/custom.conf
WaylandEnable=false
sudo systemctl restart gdm3

GRUB parameters:
GRUB_CMDLINE_LINUX_DEFAULT="nvidia-drm.modeset=0"

___

### Laptop
--- Select Intel HD Graphics ---
prime-select
sudo prime-select intel

--- WI-FI PowerSave ---
sudo nano /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
wifi.powersave = 2
sudo systemctl restart NetworkManager.service

(0): use the default value
(1): do not touch existing setting
(2): disable powersave
(3): enable powersave

### MISC
--- DELETE SWAP File ---
sudo swapoff -v /swapfile
sudo nano /etc/fstab => #swapfile swap swap defaults 0 0
sudo rm /swapfile

--- CHANGE KERNEL ---
grub-customizer (5.1.0-2) (Linux Mint Software Manager)

cat /boot/grub/grub.cfg | grep "Loading Linux"	- Kernels List
cat /etc/default/grub - GRUB Config
GRUB_DEFAULT=0 - Order -> 0, 1 , 2...
sudo update-grub

--- Deactivate Bluetooth on system startup ---
sudo nano /etc/bluetooth/main.conf - AutoEnable=true -> false

--- Check CPU Mitigations ---
ll /sys/devices/system/cpu/vulnerabilities
cat /sys/devices/system/cpu/vulnerabilities/spectre_v1
cat /sys/devices/system/cpu/vulnerabilities/spectre_v2
cat /sys/devices/system/cpu/vulnerabilities/meltdown
cat /sys/devices/system/cpu/vulnerabilities/mmio_stale_data

--- update-alternatives ---
sudo update-alternatives --config www-browser

--- Locale ---
sudo nano /etc/locale.gen 
sudo locale-gen

--- HP Printer FIX (Scanner Backend) ---
sudo nano /etc/udev/rules.d/40-libsane.rules
sudo nano /etc/udev/rules.d/S99-2000S1.rules
ACTION!="add", GOTO="libsane_rules_end" -> ACTION!="add", GOTO="libsane_usb_rules_end"

--- Disable IPv6 ---
sudo nano /etc/sysctl.conf
add lines:
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1

Certain network interface:
net.ipv6.conf.lo.disable_ipv6 = 1
net.ipv6.conf.enp7s0.disable_ipv6 = 1
net.ipv6.conf.wlp2s0.disable_ipv6 = 1
reboot OR sudo sysctl -p

--- systemctl commands ---
systemctl list-timers

--- Add Fonts ---
Global fonts:
/usr/share/fonts

Current user fonts:
~/.fonts

Update fonts cache:
fc-cache -f -v

--- NVIDIA Default Settings ---
cat /usr/lib/modprobe.d/nvidia-graphics-drivers.conf
blacklist nouveau
blacklist lbm-nouveau
alias nouveau off
alias lbm-nouveau off

cat /etc/modprobe.d/nvidia-graphics-drivers-kms.conf
####### This file was generated by nvidia-driver-535
####### Set value to 0 to disable modesetting
options nvidia-drm modeset=1

### NVIDIA Boot Modules (Linux Mint)
--- Decision 1 ---
/etc/modules (Add a few lines)
nvidia
nvidia-drm
nvidia-modeset

--- Decision 2 ---
/etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="verbose nomodeset --OR-- nvidia-drm.modeset=1 nouveau.modeset=0"
sudo update-grub

--- Set permission to change GPU Fan Settings ---
sudo nano /etc/X11/Xwrapper.config
Add line:
needs_root_rights=yes
reboot
