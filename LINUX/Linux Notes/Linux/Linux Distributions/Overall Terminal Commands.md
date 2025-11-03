## apt-get
```
alias qq-update-full='sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo apt-get autoremove && sudo apt-get autoclean && sudo apt-get clean'
```

```
sudo update-grub
```

## dnf
```
alias qq-update-full='sudo dnf update && sudo dnf upgrade && sudo dnf autoremove && sudo dnf clean all'
```

```
sudo grub2-mkconfig --output=/boot/grub2/grub.cfg
```

## pacman
```
alias qq-update-full='sudo pacman -Syyu && sudo pacman -Scc'
```

## zypper
```
alias qq-update-full='sudo zypper refresh && sudo zypper update && sudo zypper dist-upgrade && zypper packages --orphaned'
```

```
sudo grub2-mkconfig --output=/boot/grub2/grub.cfg
```

___


--- Install NVIDIA Video Driver ---
ubuntu-drivers

--- wget ---
Background downloading files
wget -bqc https://domain.com/file.zip

--- Download certain directory ---
wget -r -np -nH --cut-dirs=1 https://www.busybox.net/downloads/binaries/1.35.0-x86_64-linux-musl/
wget -np -r -l 2 https://www.busybox.net/downloads/binaries/1.35.0-x86_64-linux-musl/

--- Check DRM-KMS ---
sudo cat /sys/module/nvidia_drm/parameters/modeset
Value - Y

--- Check opened ports ---
Как узнать какие порты открыты в Linux ? / Порты / Linux / Netstat / ss / lsof / Nmap

--- Upgrade operating system to latest release (devel-release) ---
sudo do-release-upgrade -d
(If using the latest supported release, upgrade to the development release)

___

# MISC

netstat
sudo apt install net-tools
sudo netstat -ltupan
sudo netstat -lntup | grep "ssh"
sudo netstat -lntup | grep ":80"

ss
sudo ss -lntu

nmap
sudo apt install nmap
sudo nmap n -PN -sT -sU -p ВашIP

lsof
sudo lsof -i
sudo lsof -i :80