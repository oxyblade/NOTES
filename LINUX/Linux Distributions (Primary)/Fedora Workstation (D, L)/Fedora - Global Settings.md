### *Linux BOOT Options (OPTIONAL)*

```
sudo nano /etc/default/grub
```
GRUB_TIMEOUT=3 (OR 1)
GRUB_CMDLINE_LINUX_DEFAULT="rhgb loglevel=3"
```
sudo grub2-mkconfig --output=/boot/grub2/grub.cfg
```

### *RAM, SSD, HDD OPTIMIZATION (OPTIONAL)*

```
sudo nano /etc/sysctl.d/99-sysctl.conf
```
```
sudo nano /etc/sysctl.conf
```
vm.swappiness=5

vm.vfs_cache_pressure=1000
vm.dirty_background_ratio=50
vm.dirty_ratio=80
kernel.watchdog_thresh=30

Read values from file:
```
sysctl -p
```
```
man sysctl.conf
```

### *FS FLAGS (OPTIONAL)*

**BTRFS (NVME & SSD):**
subvol=root,compress=zstd:1
subvol=home,compress=zstd:1
OPTIONAL: defaults,noatime,discard=async

**BTRFS (HDD):**
nosuid,nodev,nofail,x-gvfs-show,compress=zstd:1 (+USB )
*OPTIONAL:* defaults,noatime

**EXT4 (HDD & SSD):**
defaults,noatime,barrier=0

**FSTAB:**
```
sudo nano /etc/fstab
```

*DESKTOP*
```
LABEL=HDD_1 /mnt/HDD_1 btrfs nosuid,nodev,nofail,x-gvfs-show,compress=zstd:1 0 0
LABEL=USB_HDD_1 /mnt/USB_HDD_1 ext4 nosuid,nodev,nofail,noauto,x-gvfs-show,noatime,barrier=0 0 0
LABEL=USB_HDD_2 /mnt/USB_HDD_2 ext4 nosuid,nodev,nofail,noauto,x-gvfs-show,noatime,barrier=0 0 0
LABEL=USB_HDD_3 /mnt/USB_HDD_3 ext4 nosuid,nodev,nofail,noauto,x-gvfs-show,noatime,barrier=0 0 0
```

*LAPTOP*
```
LABEL=USB_HDD_1 /mnt/USB_HDD_1 ext4 nosuid,nodev,nofail,noauto,x-gvfs-show,noatime,barrier=0 0 0
LABEL=USB_HDD_2 /mnt/USB_HDD_2 ext4 nosuid,nodev,nofail,noauto,x-gvfs-show,noatime,barrier=0 0 0
LABEL=USB_HDD_3 /mnt/USB_HDD_3 ext4 nosuid,nodev,nofail,noauto,x-gvfs-show,noatime,barrier=0 0 0
```

### *LOGS OPTIMIZATION (OPTIONAL)*

```
sudo nano /etc/logrotate.d/bootlog
```
{
    missingok
    weekly
    maxsize 500M *(OPTIONAL)*
    copytruncate
    rotate 7
    notifempty
}

*sudo nano /etc/logrotate.conf (OPTIONAL)*

**journalctl (EXT4):**
```
sudo nano /etc/systemd/journald.conf
```
SystemMaxUse=500M

```
sudo journalctl --disk-usage
```
```
sudo journalctl --verify
```
```
sudo journalctl --vacuum-size=100M
```

### *SOUNDCARD - DISABLE SUSPEND / Powersave (OPTIONAL)*

> **WirePlumber configuration**
> ```
> sudo nano /etc/wireplumber/wireplumber.conf.d/disable-idle-timeout.conf
> ```
> Paste the following text into the file:
> ```
> monitor.alsa.rules = [ { matches = [ { ## Matches all sources. * node.name = "~alsa_input.*" } { ## Matches all sinks. * node.name = "~alsa_output.*" } ] actions = { update-props = { session.suspend-timeout-seconds = 0 } } } ]
> ```
> Save the file and exit the editor.
> Restart the WirePlumber service:
> ```
> systemctl --user restart wireplumber.service
> ```
> Or restart the system for the changes to take full effect.

> **PipeWire configuration** (for older Fedora versions)
> ```
> sudo nano /etc/pulse/default.pa
> ```
> Find the line and comment it out by adding a # at the beginning of the line: *load-module module-suspend-on-idle*
> Save the file and reload PulseAudio or reboot:
> ```
> pulseaudio -k
> pulseaudio -D
> ```

** Legacy Method**
cat /proc/asound/modules
sudo nano /etc/modprobe.d/audio_disable_powersave_snd_hda_intel.conf
Add the following line:
options snd_hda_intel power_save=0 (power_save_controller=N — *OPTIONAL*)
options snd_usb_audio power_save=0 *(OPTIONAL)*
*reboot*
CHECK FIX:
cat /sys/module/snd_hda_intel/parameters/power_save (Result: power_save 0)

### *Disable Suspend when Lid Is Closed (LAPTOP)*

```
cd /etc/systemd/
sudo mkdir logind.conf.d
sudo cp /usr/lib/systemd/logind.conf /etc/systemd/logind.conf.d/logind.conf
cd logind.conf.d/
sudo nano /etc/systemd/logind.conf.d/logind.conf
```

**Uncomment lines:**
HandleLidSwitch=ignore
HandleLidSwitchDocked=ignore
LidSwitchIgnoreInhibited=yes

*Description:*
HandleLidSwitch=ignore to do nothing
HandleLidSwitch=poweroff to shutdown computer when lid is closed
HandleLidSwitch=hibernate to hibernate computer when lid is closed

### *Stop, Disable & Mask systemd Services (OPTIONAL)*

```
sudo systemctl status nvidia-powerd.service
sudo systemctl stop nvidia-powerd.service
sudo systemctl disable nvidia-powerd.service
sudo systemctl mask nvidia-powerd.service
systemctl list-unit-files --state=masked
```

### *GNOME Settings (dconf-editor) (OPTIONAL)*

*Terminal:*
dconf-editor /org/gnome/settings-daemon/plugins/power/sleep-inactive-ac-timeout - '0'
dconf-editor /org/gnome/settings-daemon/plugins/power/sleep-inactive-ac-type - 'nothing'
dconf-editor /org/gnome/settings-daemon/plugins/power/sleep-inactive-battery-timeout - '0'
dconf-editor /org/gnome/settings-daemon/plugins/power/sleep-inactive-battery-type - 'nothing'

### *Additional settings (OPTIONAL)*

sudo nano /etc/environment
####### Totem Video Player Error: failed to initialize opengl with gtk
GDK_GL=gles

____
### *MISC (Optional)*

**Nautilus DEFAULT file manager**
To set Nautilus file manager as the DEFAULT file manager type:
xdg-mime default org.gnome.Nautilus.desktop inode/directory

**GNOME Settings**
dconf-editor /org/gnome/mutter/center-new-windows - 'True'

**GSConnect**
Firewall: Rules -> Rules -> Add a rule -> Simple -> Name (GSConnect) -> Port (1716 , 1739)

___
### *SECONDARY*

**PulseAudio - Check status & info:**
pactl - Control a running PulseAudio sound server
pactl stat && pactl info

**Check CPU Mitigations:**
ll /sys/devices/system/cpu/vulnerabilities
cat /sys/devices/system/cpu/vulnerabilities/spectre_v1
cat /sys/devices/system/cpu/vulnerabilities/spectre_v2
cat /sys/devices/system/cpu/vulnerabilities/meltdown
cat /sys/devices/system/cpu/vulnerabilities/mmio_stale_data

**HP Printer FIX (Scanner Backend):**
sudo nano /etc/udev/rules.d/40-libsane.rules
sudo nano /etc/udev/rules.d/S99-2000S1.rules
ACTION!="add", GOTO="libsane_rules_end" -> ACTION!="add", GOTO="libsane_usb_rules_end"

**Disable IPv6:**
sudo nano /etc/sysctl.conf
add lines:
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
*Certain network interface:*
net.ipv6.conf.lo.disable_ipv6 = 1
net.ipv6.conf.enp7s0.disable_ipv6 = 1
net.ipv6.conf.wlp2s0.disable_ipv6 = 1
reboot OR sudo sysctl -p

**systemctl commands:**
systemctl list-timers

**Add Fonts:**
*Global fonts:*
/usr/share/fonts
*Current user fonts:*
~/.fonts
*Update fonts cache:*
fc-cache -f -v