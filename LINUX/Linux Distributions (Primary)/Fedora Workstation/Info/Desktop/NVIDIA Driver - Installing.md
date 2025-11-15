### Installing NVIDIA Drivers in Terminal

```
lspci | grep -Ei 'VGA|3D'
sudo dnf upgrade --refresh
```

Installing NVIDIA Drivers Using RPM Fusion in Fedora:
```
sudo dnf install kernel-devel kernel-headers gcc make dkms libglvnd-glx libglvnd-opengl libglvnd-devel acpid pkgconfig
```
reboot
```
sudo grub2-mkconfig --output=/boot/grub2/grub.cfg
```
reboot
```
sudo dnf install akmod-nvidia
```
(Optional packages: xorg-x11-drv-nvidia-cuda nvidia-gpu-firmware)
reboot
```
modinfo -F version nvidia
nvidia-smi
```

```
sudo cp -p /usr/share/X11/xorg.conf.d/nvidia.conf /etc/X11/xorg.conf.d/nvidia.conf
```
reboot
sudo nano /etc/X11/xorg.conf.d/nvidia.conf (OPTIONAL)

-----------------------------

### Installing NVIDIA Drivers Manually in Fedora (Downloaded NVIDIA Driver):
https://www.nvidia.com/en-us/drivers/unix

```
sudo dnf install kernel-devel kernel-headers gcc make dkms libglvnd-glx libglvnd-opengl libglvnd-devel acpid pkgconfig
```
reboot
```
sudo echo -e "blacklist nouveau\noptions nouveau modeset=0" | sudo tee /etc/modprobe.d/blacklist-nouveau.conf
sudo dracut --force
sudo systemctl set-default multi-user.target
```
reboot

```
cd Downloads
chmod +x NVIDIA-Linux-*.run
sudo ./NVIDIA-Linux-*.run
```
"NVIDIA 32-bit C compatibility libraries" -> "Yes"
"Kernel Module Sources with DKMS" -> "Yes"
```
sudo systemctl set-default graphical.target
```
reboot
```
modinfo -F version nvidia
nvidia-smi
sudo cp -p /usr/share/X11/xorg.conf.d/nvidia.conf /etc/X11/xorg.conf.d/nvidia.conf
```
reboot
sudo nano /etc/X11/xorg.conf.d/nvidia.conf (OPTIONAL)

___

###### Configs:
System config directory: /usr/share/X11/xorg.conf.d/nvidia.conf
Config file: /etc/X11/xorg.conf (Generated: sudo nvidia-settings)
Config directory: /etc/X11/xorg.conf.d (xorg.conf EMPTY)
