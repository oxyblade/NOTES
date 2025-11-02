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
