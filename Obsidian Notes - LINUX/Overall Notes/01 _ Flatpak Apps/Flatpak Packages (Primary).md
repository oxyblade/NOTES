## Global
```
flatpak install flathub com.github.tchx84.Flatseal -y
flatpak install flathub io.github.flattool.Warehouse -y
flatpak install flathub page.tesk.Refine -y
```
___

## Apps Window
```
flatpak install flathub com.brave.Browser -y
flatpak install flathub com.google.Chrome -y
flatpak install flathub org.filezillaproject.Filezilla -y
flatpak install flathub org.telegram.desktop -y
flatpak install flathub io.github.mimbrero.WhatsAppDesktop -y
flatpak install flathub com.sindresorhus.Caprine -y
flatpak install flathub org.kde.krita -y
flatpak install flathub org.inkscape.Inkscape -y
flatpak install flathub com.transmissionbt.Transmission -y
flatpak install flathub org.kde.kid3 -y
flatpak install flathub org.soundconverter.SoundConverter -y
flatpak install flathub org.ksnip.ksnip -y
flatpak install flathub com.dec05eba.gpu_screen_recorder -y
flatpak install flathub io.missioncenter.MissionCenter -y
flatpak install flathub net.nokyan.Resources -y
```
HiFile, Virtual Machine Manager, Disk Usage Analyzer, Disks, System Monitor

___

## Web
Firefox ESR, Tor Browser, VK Messenger
```
flatpak install flathub org.signal.Signal -y
flatpak install flathub com.viber.Viber -y
flatpak install flathub com.skype.Client -y
flatpak install flathub us.zoom.Zoom -y
flatpak install flathub org.gajim.Gajim -y
flatpak install flathub com.github.unrud.VideoDownloader -y
flatpak install flathub io.github.mhogomchungu.media-downloader -y
flatpak install flathub com.protonvpn.www -y
```
___

## Dev
Sublime Text, JetBrains Apps, Text Editor
```
flatpak install flathub com.visualstudio.code -y
flatpak install flathub dev.zed.Zed -y
```
___

## Multimedia
```
flatpak install flathub org.gimp.GIMP -y
flatpak install flathub com.github.PintaProject.Pinta -y
flatpak install flathub org.nomacs.ImageLounge -y
flatpak install flathub org.gnome.gThumb -y
flatpak install flathub com.kjxbyz.PicGuard -y
flatpak install flathub com.github.huluti.Curtail -y
flatpak install flathub io.gitlab.adhami3310.Converter -y
flatpak install flathub org.kde.optiimage -y
flatpak install flathub com.xnview.XnViewMP -y
flatpak install flathub org.gnome.Showtime -y
flatpak install flathub io.github.celluloid_player.Celluloid -y
flatpak install flathub no.mifi.losslesscut -y
flatpak install flathub org.shotcut.Shotcut -y
flatpak install flathub org.kde.kdenlive -y
flatpak install flathub org.openshot.OpenShot -y
flatpak install flathub org.mixxx.Mixxx -y
flatpak install flathub com.obsproject.Studio -y
flatpak install flathub io.github.yuki_iptv.yuki-iptv -y
flatpak install flathub de.haeckerfelix.Shortwave -y
```
___

## Office
```
flatpak install flathub org.onlyoffice.desktopeditors -y
flatpak install flathub org.gnome.World.Iotas -y
flatpak install flathub net.codeindustry.MasterPDFEditor -y
flatpak install flathub md.obsidian.Obsidian -y
```
___

## Tools
Double Commander, balenaEtcher
```
flatpak install flathub com.github.vkohaupt.vokoscreenNG -y
flatpak install flathub org.flameshot.Flameshot -y
flatpak install flathub com.uploadedlobster.peek -y
flatpak install flathub com.github.finefindus.eyedropper -y
flatpak install flathub org.gnome.design.Emblem -y
flatpak install flathub org.gnome.design.Lorem -y
flatpak install flathub garden.jamie.Morphosis -y
flatpak install flathub com.felipekinoshita.Wildcard -y
flatpak install flathub io.github.nate_xyz.Paleta -y
flatpak install flathub org.gnome.design.Palette -y
flatpak install flathub fr.romainvigier.MetadataCleaner -y
flatpak install flathub io.github.diegoivan.pdf_metadata_editor -y
flatpak install flathub io.github.idevecore.Valuta -y
flatpak install flathub page.codeberg.JakobDev.jdReplace -y
flatpak install flathub dev.geopjr.Collision -y
flatpak install flathub io.github.zefr0x.hashes -y
flatpak install flathub io.github.bytezz.IPLookup -y
flatpak install flathub org.nmap.Zenmap -y
flatpak install flathub io.github.lo2dev.Echo -y
flatpak install flathub xyz.ketok.Speedtest -y
flatpak install flathub io.github.ronniedroid.concessio -y
flatpak install flathub uk.org.greenend.chiark.sgtatham.putty -y
flatpak install flathub io.gitlab.theevilskeleton.Upscaler -y
```
___

## Utilities
Tweaks, NVIDIA X Server Settings, Logs, File Roller, Passwords and Keys, Firewall, GParted, Firmware, Extensions, Fedora Media Writer, dconf Editor, Boxes, Brasero, Connections
```
flatpak install flathub io.github.flattool.Ignition -y
```
___

## Games
```
flatpak install flathub net.zdechov.app.x2048 -y
flatpak install flathub io.github.nokse22.ultimate-tic-tac-toe -y
```
___

## Flatseal - Global options

--- Filesystem Permissions ---
/mnt/HDD_1
/mnt/HDD_2
/run/media/andrew
~/Downloads
~/Pictures

~/STORAGE_ASUS
~/.themes (OPTIONAL)

--- Environment (Variables) ---
GTK_THEME=Adwaita-dark
GTK_THEME=Adw-dark

--- Flatpak commands ---
flatpak run org.gajim.Gajim
flatpak uninstall --delete-data com.google.Chrome -y

--- Permissions ---
Set access permissions to external drives:
sudo flatpak override --filesystem=host name_package_here
sudo flatpak override --filesystem=host org.telegram.desktop
