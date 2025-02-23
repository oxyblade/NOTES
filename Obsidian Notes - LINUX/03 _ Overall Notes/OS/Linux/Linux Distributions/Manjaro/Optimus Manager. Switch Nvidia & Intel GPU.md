> [!NOTE] Step 1
> Installation of packages: optimus-manager from repo and optimus-manager-qt from AUR (it's possible to install git versions from AUR):
> 
> sudo pacman -S optimus-manager
> 
> Use choosen AUR helper or GUI program like Pamac or Octopi to find and install optimus-manager-qt:
> trizen optimus-manager-qt
> yay optimus-manager-qt

> [!NOTE] Step 2
> Disable Bumblebee daemon:
> sudo systemctl disable bumblebeed.service
> 
> The sole act of installing optimus-manager packages makes Bumblebee not work correctly, so this is normal if you try run Bumblebee and see errors at this point. Bumblebee process cannot be active for proper optimus-manager work so let's just disable it as shown above. Bumblebee package may stay on the system if you want reconsider and uninstall optimus-manager in the future but without active daemon, it's not doing anything, just as it should.

> [!NOTE] Step 3
> Disable Xorg graphic configurations in /etc/X11/xorg.conf.d/
> 
> Go to /etc/X11/xorg.conf.d/ and disable any graphic related configs. Instead deleting them, just rename them by adding.bak for the case if you want to restore them manually.
> 
> So for example, I had in this location:
> 00-keyboard.conf 20-intel.conf 30-touchpad.conf 90-mhwd.conf
> 
> Your files may be different so don't worry if you don't have those or have a bit different ones.
> 
> Keyboard and touchpad configs are self explanatory and have nothing to do with GPUs. Intel is clearly graphic related config while mhwd is a Manjaro specific configuration file of mhwd script (won't be present on non-Manjaro systems) that configures graphic.
> I renamed intel and mhwd confs by adding.bak so in the end my files in this locations are:
> 
> 00-keyboard.conf 20-intel.conf.bak 30-touchpad.conf
> 10-optimus-manager.conf 20-intel.conf.bak-old 90-mhwd.conf.bak
> 
> Did you noticed a new one: 10-optimus-manager.conf? This one WILL BE GENERATED
> AUTOMATICALLY LATER by optimus-manager and you won't have it at this poin't so don't worry. Optimus manager simply edits this config to switch between graphical modes (Intel and NVIDIA) so its content change dependently which GPU you choose at the moment.

> [!NOTE] Step 4
> Disable Xorg graphic configurations in /etc/X11/
> 
> The same situation as above. I had in this location a file:
> nvidia-xorg.conf
> 
> You can rename it to nvidia-xorg.conf.bak, however, I noticed that some updates may restore the file and optimus-manager still works as intended... so it's not crucial, however advised to disable this conf anyway.
> 
> You may see in this location again different files, like:
> xorg.conf or nvidia-xonfig
> 
> The same deal, disable it by renaming it.

> [!NOTE] Step 5
> For Manjaro Gnome users (others ignore this point):
> 
> install gdm-prime from AUR
> 
> Dependently which AUR helper you use, install a package gdm-prime and remove gdm from Manjaro repo:
> yay gdm-prime OR trizen gdm-prime (or just use Pamac or Octopi).
> 
> The reason for that is that optimus-manager cannot switch GPUs with default gdm config, while gdm-prime has Canonical's patches that add two script entry points for GPU Prime switching. The package is otherwise identical to the official one.
> 
> You need to edit the file /etc/gdm/custom.conf and remove the # before the line
> ####### WaylandEnable=false
> 
> So it would look:
> WaylandEnable=false

Gnome launches Wayland sessions by default, which are incompatible with optimus-manager, so the above change forces X session. Another quirk of GDM is that the X server may not automatically restart after a GPU switch. If you see an empty black screen or a black screen with a blinking cursor, try switching back to an empty TTY (with Ctrl+Alt+F5 for instance), then back to TTY1 with Ctrl+Alt+F1

Check if optimus-manager daemon is running correctly:
systemctl status optimus-manager.service