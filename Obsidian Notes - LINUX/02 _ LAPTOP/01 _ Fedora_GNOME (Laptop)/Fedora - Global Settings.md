## Overall Settings
Terminal: Custom font, Window Size: (Monospace 10, 140 x 33)
Terminal: Change Shortcuts
Text Editor: Custom font: Monospace, 11

## Linux BOOT Options
[ GENERAL Options ]
sudo nano /etc/default/grub

GRUB_TIMEOUT=3 (OR 1)
GRUB_CMDLINE_LINUX="rhgb loglevel=3"
sudo grub2-mkconfig --output=/boot/grub2/grub.cfg

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
LABEL=USB_HDD_1 /mnt/USB_HDD_1 ext4 nosuid,nodev,nofail,noauto,x-gvfs-show,noatime,barrier=0 0 0
LABEL=USB_HDD_2 /mnt/USB_HDD_2 ext4 nosuid,nodev,nofail,noauto,x-gvfs-show,noatime,barrier=0 0 0
LABEL=USB_HDD_3 /mnt/USB_HDD_3 ext4 nosuid,nodev,nofail,noauto,x-gvfs-show,noatime,barrier=0 0 0
```

## LOGS OPTIMIZATION
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

sudo nano /etc/logrotate.conf (OPTIONAL Settings)

--- journalctl (EXT4) (OPTIONAL) ---
sudo nano /etc/systemd/journald.conf
SystemMaxUse=500M

sudo journalctl --disk-usage
sudo journalctl --vacuum-size=100M
sudo journalctl --verify

## SOUNDCARD - DISABLE AUTO SUSPEND (Powersave)
--- Method 1 (MAIN) ---
sudo nano /etc/modprobe.d/audio_disable_powersave_snd_hda_intel.conf
At the end of the file add the following line:
options snd_hda_intel power_save=0 power_save_controller=N

[ OR ]

options snd_usb_audio power_save=0
reboot

--- CHECK FIX ---
cat /sys/module/snd_hda_intel/parameters/power_save
power_save 0

## RAM, SSD, HDD OPTIMIZATION
sudo nano /etc/sysctl.d/99-sysctl.conf
sudo nano /etc/sysctl.conf (Alternative)
vm.swappiness=5

[ OR ]

sudo echo -e "vm.swappiness=5" | sudo tee -a /etc/sysctl.conf
sudo echo -e "vm.vfs_cache_pressure=1000" | sudo tee -a /etc/sysctl.conf

sudo echo -e "vm.dirty_background_ratio = 50" | sudo tee -a /etc/sysctl.conf
sudo echo -e "vm.dirty_ratio = 80" | sudo tee -a /etc/sysctl.conf
sudo echo -e "kernel.watchdog_thresh=30" | sudo tee -a /etc/sysctl.conf

man sysctl.conf
sysctl -p (Read values from file)

## Disable Suspend when Lid Is Closed on Laptops
cd /etc/systemd/
sudo mkdir logind.conf.d
sudo cp /usr/lib/systemd/logind.conf /etc/systemd/logind.conf.d/logind.conf
cd logind.conf.d/
sudo nano /etc/systemd/logind.conf.d/logind.conf

Uncomment lines:
HandleLidSwitch=ignore
HandleLidSwitchDocked=ignore
LidSwitchIgnoreInhibited=yes

Description:
HandleLidSwitch=ignore to do nothing
HandleLidSwitch=poweroff to shutdown computer when lid is closed
HandleLidSwitch=hibernate to hibernate computer when lid is closed

## GNOME Settings (dconf-editor)

Terminal:  
dconf-editor /org/gnome/settings-daemon/plugins/power/sleep-inactive-ac-timeout - '0'  
dconf-editor /org/gnome/settings-daemon/plugins/power/sleep-inactive-ac-type - 'nothing'  
dconf-editor /org/gnome/settings-daemon/plugins/power/sleep-inactive-battery-timeout - '0'  
dconf-editor /org/gnome/settings-daemon/plugins/power/sleep-inactive-battery-type - 'nothing'

## Additional settings (OPTIONAL)

sudo nano /etc/environment  
####### Totem Video Player Error: failed to initialize opengl with gtk  
GDK_GL=gles

___

## MISC
--- Nautilus DEFAULT file manager ---
To set Nautilus file manager as the DEFAULT file manager type:
xdg-mime default org.gnome.Nautilus.desktop inode/directory

--- GNOME Settings ---
dconf-editor /org/gnome/mutter/center-new-windows - 'True'

--- GSConnect ---
Firewall: Rules -> Rules -> Add a rule -> Simple -> Name (GSConnect) -> Port (1716 , 1739)

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
