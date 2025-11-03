Problem:
Display managers or Desktop environments fail to launch the user is presented with a black screen and when they try to run startx or sddm as root they are greeted with the following message: "nvidia-drm Failed to grab modeset ownership"

Solution:
The solution is quite simple, i managed to get it working again by modifying the grub configuration, to do this execute the following tasks.

sudo nano /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT=nvidia-drm.modeset=1
sudo update-grub

sudo grub2-mkconfig -o /boot/grub2/grub.cfg
sudo grub2-mkconfig -o /boot/grub/grub.cfg

About nvidia-drm.modeset:
All it really does is enable the DRIVER_MODESET capability flag in the nvidia-drm devices so that DRM clients can use the various modesetting APIs. In addition to allowing clients that talk to the low-level DRM interface to work, it’s also necessary for some PRIME-related interoperability features.

Loading nvidia-drm with modeset=1 causes it to configure and initialize all GPUs immediately rather than waiting for a client to open the /dev/nvidia* device files. This means that some options that require a userspace application to configure them before the GPUs are initialized won’t work if they were already configured by nvidia-drm. The big example at the moment is SLI Mosaic, which is enabled by the X driver if /etc/X11/xorg.conf says it should be.