sudo bootctl - Check & Control EFI firmware boot settings and manage boot loader

dmesg Список устройств системы
dmesg -T

inxi -F - Hardware Info
sudo lshw Информация об аппаратном обеспечении в Linux (Terminal)
lshw-gtk Информация об аппаратном обеспечении в Linux (GUI)
hardinfo Информация об аппаратном обеспечении в Linux (GUI)
lsusb Получение списка и определения USB-устройств
sudo ethtool Работа с сетевыми устройствами

cat /proc/cpuinfo | grep -i mhz
cat /proc/asound/card*/codec* | grep Codec

sudo apt-get install sysstat - System performance tools for Linux
sudo apt-get install procinfo - Reporter for system information from /proc and /sys
sudo apt-get install acpi

efibootmgr - change the UEFI Boot Manager configuration (sudo efibootmgr -b 3 -B -v)
modinfo - Show information about a Linux Kernel module
lscpu Инфо о процессоре
cat /proc/cpuinfo
cat or less /proc/meminfo
free - RAM
cat /proc/swaps
lsb_release -a - Version distro
uname -a
cat /proc/cmdline Параметры запуска ядра
sysctl -a | more Параметры запуска ядра
sudo fdisk -l | grep '^Disk /dev'
sudo fdisk-l or sudo fdisk -l /dev/sda
lsblk
df or df -HT - Filesystem
lspci, lspci -vt, lspci -vvvn| less - PCI devices
lsusb or lsusb -vt - USB devices
iwconfig - WIRELESS
sudo lshw -class display, lspci | grep -i vga, lspci -vvnn | grep VGA
upower -i /org/freedesktop/UPower/devices/battery_BAT0
sudo ip a, ifconfig -a, - network info

AudioCard Check:
cat /proc/asound/card0/codec#0
arecord -l
arecord -L

service --status-all
initctl list
pstree, pstree | less - processes info


To set the scaling_governor to "performance" mode for each CPU, run:
sudo echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

