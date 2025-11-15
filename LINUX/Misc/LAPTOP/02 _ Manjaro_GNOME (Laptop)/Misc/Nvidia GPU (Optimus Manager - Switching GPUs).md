Install Manjaro Linux with Open Source GPU Driver
```
sudo pacman -S linux66-nvidia-470xx
sudo pacman -S nvidia-settings
```

GNOME:
sudo nano /etc/gdm/custom.conf [Uncomment: #WaylandEnable=false]
sudo pamac install gdm-prime

KDE:
sudo nano /etc/sddm.conf [Comment: DisplayCommand, DisplayStopCommand]

sudo pacman -S optimus-manager-qt
reboot
systemctl status optimus-manager.service

___

sudo pacman -S nvidia-prime (Optional)
