## Overall Settings
Terminal: Custom font, Window Size: (Monospace 11, 140 x 35) (10, 145 x 35)
Terminal: Change Shortcuts
Text Editor: Custom font: Monospace, 11

## Linux BOOT Options
[ GENERAL Options ]
sudo nano /etc/default/grub

GRUB_TIMEOUT=3 (OR 1)
GRUB_CMDLINE_LINUX_DEFAULT="rhgb loglevel=3"
sudo grub2-mkconfig --output=/boot/grub2/grub.cfg

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
BTRFS (NVME & SSD):
compress=zstd:1,defaults,noatime,discard=async

BTRFS (HDD):
compress=zstd:1,defaults,noatime
compress=zstd:1,x-gvfs-show,defaults,noatime,noauto [ USB ]

EXT4 (HDD & SSD):
defaults,noatime

## SOUNDCARD - DISABLE SUSPEND / Powersave (OPTIONAL)
--- Method 1 (MAIN) ---
sudo nano /etc/modprobe.d/audio_disable_powersave_snd_hda_intel.conf
Add the following line:
options snd_hda_intel power_save=0 power_save_controller=N

[ OR ]

options snd_usb_audio power_save=0
reboot

--- CHECK FIX ---
cat /sys/module/snd_hda_intel/parameters/power_save
power_save 0

## LOGS OPTIMIZATION (OPTIONAL)
--- bootlog (syslog) ---
sudo nano /etc/logrotate.d/bootlog
{
    missingok
    weekly
    maxsize 500M -> OPTIONAL
    copytruncate
    rotate 7
    notifempty
}

sudo nano /etc/logrotate.conf

--- journalctl (EXT4) ---
sudo nano /etc/systemd/journald.conf
SystemMaxUse=500M

sudo journalctl --disk-usage
sudo journalctl --vacuum-size=100M
sudo journalctl --verify

## Stop, Disable & Mask systemd Services (OPTIONAL)
```
sudo systemctl status nvidia-powerd.service
sudo systemctl stop nvidia-powerd.service
sudo systemctl disable nvidia-powerd.service
sudo systemctl mask nvidia-powerd.service
systemctl list-unit-files --state=masked
```

## Additional settings

sudo nano /etc/environment
####### Totem Video Player Error: failed to initialize opengl with gtk
GDK_GL=gles

____

## MISC
--- Nautilus DEFAULT file manager ---
To set Nautilus file manager as the DEFAULT file manager type:
xdg-mime default org.gnome.Nautilus.desktop inode/directory

--- GNOME Settings ---
dconf-editor /org/gnome/mutter/center-new-windows - 'True'

--- GSConnect ---
Firewall: Rules -> Rules -> Add a rule -> Simple -> Name (GSConnect) -> Port (1716 , 1739)

## Laptops: Disable Suspend when Lid Is Closed
sudo nano /usr/lib/systemd/logind.conf

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
--- PulseAudio - Check status & info ---
pactl - Control a running PulseAudio sound server
pactl stat && pactl info

--- Check CPU Mitigations ---
ll /sys/devices/system/cpu/vulnerabilities
cat /sys/devices/system/cpu/vulnerabilities/spectre_v1
cat /sys/devices/system/cpu/vulnerabilities/spectre_v2
cat /sys/devices/system/cpu/vulnerabilities/meltdown
cat /sys/devices/system/cpu/vulnerabilities/mmio_stale_data

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
