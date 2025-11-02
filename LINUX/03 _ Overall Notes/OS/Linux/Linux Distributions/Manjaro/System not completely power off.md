Manjaro won’t completely power off.
I was able to follow this and it worked (Kernel options: acpi=force apm=power_off)

sudo gedit /etc/default/grub

Change the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force apm=power_off"
sudo update-grub