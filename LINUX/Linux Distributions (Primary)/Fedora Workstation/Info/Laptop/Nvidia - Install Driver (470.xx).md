Legacy GPU NVIDIA Driver Version (470.xx series)

```
/sbin/lspci | grep -e VGA && /sbin/lspci | grep -e 3D
```

```
https://rpmfusion.org/Configuration#Graphical_Setup_via_Firefox_web_browser
```

Optional
```
https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-41.noarch.rpm
```

```
sudo dnf upgrade -y
```

```
sudo dnf install xorg-x11-drv-nvidia-470xx akmod-nvidia-470xx
```


> [!TIP] Important
> After the RPM transaction ends, please remember to wait until the kmod has been built. This can take up to 5 minutes on some systems.


Optional (for CUDA up to 11.4 support, nvidia-smi...)
```
sudo dnf install xorg-x11-drv-nvidia-470xx-cuda
```

```
reboot
```