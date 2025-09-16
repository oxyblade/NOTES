```shell
## System
alias qq-update-repos='sudo apt-get update'
alias qq-update-deb='sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade'
alias qq-update-full='sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade && flatpak update && flatpak uninstall --unused && sudo snap refresh'
alias qq-upgrade='sudo apt-get upgrade'
alias qq-dist-upgrade='sudo apt-get dist-upgrade'
alias qq-apt-clean='sudo apt-get autoremove && sudo apt-get autoclean && sudo apt-get clean'
alias qq-apt-info='apt-cache show'
alias qq-apt-search='apt-cache search'
alias qq-grub-config='nano -v /etc/default/grub'
alias qq-fstab-config='nano -v /etc/fstab'
alias qq-kernels='cat /boot/grub/grub.cfg | grep "Loading Linux"'
alias qq-process-ram-load='ps -eo pmem,ppid,comm | sort -k 1 -r | head -21 | tail -20'
alias qq-process-zombie='ps aux | grep defunct'
alias qq-process-service-running='systemctl list-units --type service --state running'
alias qq-process-service-exited='systemctl list-units --type service --state exited'
alias qq-systemd-analyze='systemd-analyze'
alias qq-systemd-analyze-critical-chain='systemd-analyze critical-chain'
alias qq-systemd-analyze-blame='systemd-analyze blame'
alias qq-systemd-analyze-plot-export-svg='systemd-analyze plot > /mnt/HDD_1/Downloads__HDD_1/bootup.svg'
alias qq-service-status-all='service --status-all'
alias qq-free='free --mega'
alias qq-sensors-cpu-temperature='watch -n 1 sensors'
alias qq-sensors-cpu-frequency='watch -n 1 grep MHz /proc/cpuinfo'
alias qq-sensors-gpu-nvidia-smi='watch -n 1 nvidia-smi'
alias qq-sensors-gpu-nvtop='nvtop'
alias qq-smart-nvme='sudo nvme smart-log /dev/nvme0n1'
alias qq-inxi='inxi -Fxxxrs'
alias qq-tracker-info='tracker3 status && tracker3 daemon'
alias qq-cpu-vulnerability-check='lscpu | grep -i Vulnerability'
alias qq-dmesg-grep='sudo dmesg | grep -i'
alias qq-system-iostat='iostat' # Report Central Processing Unit (CPU) statistics
alias qq-system-lslogins='lslogins' # User Accounts
alias qq-system-lsmod='lsmod' # Listing Kernel modules
alias qq-system-modinfo='modinfo' # Show information about a Linux Kernel module
alias qq-nano='nano -vl'
alias qq-grep='grep -inE'
alias qq-grep-recursive='grep -r'
alias qq-ping='ping -c 3'
alias qq-tool-files-du-1='du -sh * | sort -h'
alias qq-tool-files-du-2='du -h | sort -h'
alias qq-tool-files-gdu-root='gdu /'
alias qq-tool-files-gdu-home='gdu'
alias qq-tool-files-gdu-hdd_1='gdu /mnt/HDD_1'
alias qq-tool-files-gdu-usb_hdd_1='gdu /mnt/USB_HDD_1'
alias qq-tool-files-gdu-usb_hdd_2='gdu /mnt/USB_HDD_2'
alias qq-tool-files-gdu-usb_hdd_3='gdu /mnt/USB_HDD_3'
alias qq-pro-status='pro status --all'
alias qq-duf='watch -n 1 duf'
alias qq-password-generation-pwgen='pwgen -syB'
alias qq-unzip='unzip -o "*.zip"'
alias qq-rar-add-all='/mnt/HDD_1/01_Apps/Portable/002/rar/rar a -m5 Archive *'
alias qq-rar-add-single='/mnt/HDD_1/01_Apps/Portable/002/rar/rar a -m5 Archive'
alias qq-rar-test='/mnt/HDD_1/01_Apps/Portable/002/rar/rar t'
alias qq-rar-extract='/mnt/HDD_1/01_Apps/Portable/002/rar/rar x'
alias qq-unrar='unrar x -o+ "*.rar"'
alias qq-7z-extract='7z x -y "*.7z"'
alias qq-smart-nvme='sudo smartctl -a /dev/nvme0n1'
alias qq-smart-sda='sudo smartctl -a /dev/sda'
alias qq-smart-sdb='sudo smartctl -a /dev/sdb'
alias qq-smart-sdc='sudo smartctl -a /dev/sdc'
####### alias qq-screen-off='xset dpms force off'

## Packages
alias qq-flatpak-update='flatpak update && flatpak uninstall --unused'
alias qq-flatpak-uninstall-delete-data='flatpak uninstall --delete-data'
alias qq-flatpak-installation-list='flatpak --columns=app,name,version,size,installation list'
alias qq-flatpak-depends='flatpak list --app --columns=application,runtime'
alias qq-flatpak-app-info='flatpak list | grep -i'
alias qq-flatpak-remote-info='flatpak remote-info --log flathub'
alias qq-update-snap='sudo snap refresh'
alias qq-ppa-list='grep -r --include "*.list" "^deb " /etc/apt/sources.list /etc/apt/sources.list.d'
alias qq-pkg-list='dpkg -l | grep'
alias qq-pkg-process-name='ps aux | grep'
alias qq-pkg-process-name-pid='ps -Flww -p'
alias qq-root-hifile='sudo /mnt/HDD_1/01_Apps/Apps_Portable/001/HiFile/HiFile.AppImage'
alias qq-root-doublecommander='sudo /mnt/HDD_1/01_Apps/Apps_Portable/001/doublecmd/doublecmd'
alias qq-root-sublime_text='sudo /mnt/HDD_1/01_Apps/Apps_Portable/001/sublime_text/sublime_text'

## System Logs
alias qq-journalctl-log-search='journalctl | grep -i'
alias qq-journalctl-disk-usage='journalctl --disk-usage'
alias qq-journalctl-verify='journalctl --verify'
alias qq-log-auth='lnav /var/log/auth.log'
alias qq-log-faillog='sudo lnav /var/log/faillog'
alias qq-log-bootstrap='lnav /var/log/bootstrap.log'
alias qq-log-boot='sudo lnav /var/log/boot.log'
alias qq-log-dmesg='lnav /var/log/dmesg'
alias qq-log-dpkg='lnav /var/log/dpkg.log'
alias qq-log-dpkg-installed-1='cat /var/log/apt/history.log'
alias qq-log-dpkg-installed-2='cat /var/log/dpkg.log | grep -i "installed"'
alias qq-log-gpu-manager='lnav /var/log/gpu-manager.log'
alias qq-log-kern='lnav /var/log/kern.log'
alias qq-log-syslog='lnav /var/log/syslog'
alias qq-log-ufw='lnav /var/log/ufw.log'
alias qq-log-xorg0='lnav /var/log/Xorg.0.log'
alias qq-log-xorg1='lnav /var/log/Xorg.1.log'

## Network
alias qq-network-pktstat='sudo pktstat -n -w 1'
alias qq-network-ifconfig='watch -n 1 ifconfig'
alias qq-network-netstat='watch -n 1 netstat -antp && watch -n 1 netstat -t && netstat -lpn'
alias qq-network-ip-external='curl https://ipinfo.io/ip && echo "" && echo ""' # wget -qO- ifconfig.co # ifconfig.me
alias qq-network-dns-local='resolvectl status'
alias qq-network-dns-info='nslookup -type=any'
alias qq-network-dns-debug='nslookup -debug'
alias qq-network-ports-web-info-1='sudo nmap -sTU -O'
alias qq-network-ports-web-info-2='sudo nmap -n -PN -sT -sU -p-'
alias qq-network-nmap-scan-home='nmap -sP 192.168.100.1/24'
alias qq-network-wifi-list='nmcli device wifi list'

## System Scripts
alias qq-sensors-full='/mnt/HDD_1/01_Apps/Apps_Backup/01_LINUX/Overall_Files/Scripts/qq-script-sensors-desktop.sh'
alias qq-script-df-lsblk='/mnt/HDD_1/01_Apps/Apps_Backup/01_LINUX/Overall_Files/Scripts/qq-script-df-lsblk.sh'
alias qq-script-dns-ping='/mnt/HDD_1/01_Apps/Apps_Backup/01_LINUX/Overall_Files/Scripts/qq-script-dns-ping.sh'
alias qq-script-hostname='/mnt/HDD_1/01_Apps/Apps_Backup/01_LINUX/Overall_Files/Scripts/qq-script-hostname.sh'
alias qq-script-npm-yarn-sudo='sudo /mnt/HDD_1/01_Apps/Apps_Backup/01_LINUX/Overall_Files/Scripts/qq-script-npm-yarn-sudo.sh'
alias qq-script-ports-local-sudo='sudo /mnt/HDD_1/01_Apps/Apps_Backup/01_LINUX/Overall_Files/Scripts/qq-script-ports-local-sudo.sh'
alias qq-script-resources-desktop='/mnt/HDD_1/01_Apps/Apps_Backup/01_LINUX/Overall_Files/Scripts/qq-script-resources-desktop.sh'

## Extended Scripts
alias qq-script-external-geekbench='sudo /mnt/HDD_1/01_Apps/Portable/002/Geekbench/geekbench6'
alias qq-script-external-memconf='sudo /mnt/HDD_1/01_Apps/Portable/002/memconf/memconf.pl'
alias qq-script-external-spectre-meltdown-checker='sudo /mnt/HDD_1/01_Apps/Portable/002/spectre-meltdown-checker/spectre-meltdown-checker.sh'

## XAMPP Local Server
alias xampp='sudo /opt/lampp/manager-linux-x64.run'
alias xampp-status='xampp status apache && xampp status mysql' # Alternative: sudo /opt/lampp/lampp status apache
alias xampp-start='xampp start apache && xampp start mysql && xampp status apache && xampp status mysql'
alias xampp-stop='xampp stop apache && xampp stop mysql && xampp status apache && xampp status mysql'
alias xampp-restart='xampp restart apache && xampp restart mysql && xampp status apache && xampp status mysql'
alias xampp-permissions-777='sudo chmod -R 777 /mnt/HDD_1/01_Apps/Servers_Local/htdocs/'
alias xampp-permissions-755='sudo chmod -R 755 /mnt/HDD_1/01_Apps/Servers_Local/htdocs/'
alias xampp-permissions-directories-755='sudo find /mnt/HDD_1/01_Apps/Servers_Local/htdocs/ -type d -exec chmod 755 {} \;'
alias xampp-permissions-files-644='sudo find /mnt/HDD_1/01_Apps/Servers_Local/htdocs/ -type f -exec chmod 644 {} \;'

## Apache Local Server
alias qq-apache-status='sudo systemctl status apache2.service'
alias qq-apache-start='sudo systemctl start apache2.service'
alias qq-apache-stop='sudo systemctl stop apache2.service'
alias qq-apache-reload='sudo systemctl reload apache2.service'
alias qq-apache-restart='sudo systemctl restart apache2.service'
alias qq-apache-enable='sudo systemctl enable apache2.service'
alias qq-apache-disable='sudo systemctl disable apache2.service'
alias qq-apache-permissions='sudo chmod -R 777 /var/www/'
alias qq-apache-configtest='apachectl configtest'

## MISC
alias qq-vm-libvirtd-service-status='sudo systemctl status libvirtd.service'
alias qq-vm-libvirtd-service-start='sudo systemctl start libvirtd.service'
alias qq-vm-libvirtd-service-stop='sudo systemctl stop libvirtd.service'
alias qq-vm-libvirtd-service-disable='sudo systemctl disable libvirtd.service'
alias qq-vm-libvirtd-service-enable='sudo systemctl enable libvirtd.service'
alias qq-vm-libvirtd-service-restart='sudo systemctl restart libvirtd.service'
alias qq-libreoffice-convertALL-to-pdf='soffice --headless --convert-to pdf --outdir ./ *.docx *.doc *.rtf *.odt *.pptx *.ppt *.xlsx *.xls *.txt *.png *.jpg *.jpeg'
alias qq-libreoffice-fs-structure-convertALL-to-pdf='find . -type f \( -name "*.docx" -o -name "*.doc" -o -name "*.rtf" -o -name "*.odt" -o -name "*.pptx" -o -name "*.ppt" -o -name "*.xlsx" -o -name "*.xls" -o -name "*.txt" -o -name "*.png" -o -name "*.jpg" -o -name "*.jpeg" \) -execdir soffice --headless --convert-to pdf "{}" \;'
alias qq-libreoffice-convert-docx-to-pdf='soffice --headless --convert-to pdf --outdir ./ *.docx'
alias qq-libreoffice-convert-doc-to-pdf='soffice --headless --convert-to pdf --outdir ./ *.doc'
alias qq-libreoffice-convert-rtf-to-pdf='soffice --headless --convert-to pdf --outdir ./ *.rtf'
alias qq-libreoffice-convert-odt-to-pdf='soffice --headless --convert-to pdf --outdir ./ *.odt'
alias qq-libreoffice-convert-pptx-to-pdf='soffice --headless --convert-to pdf --outdir ./ *.pptx'
alias qq-libreoffice-convert-ppt-to-pdf='soffice --headless --convert-to pdf --outdir ./ *.ppt'
alias qq-libreoffice-convert-xlsx-to-pdf='soffice --headless --convert-to pdf --outdir ./ *.xlsx'
alias qq-libreoffice-convert-xls-to-pdf='soffice --headless --convert-to pdf --outdir ./ *.xls'
alias qq-libreoffice-convert-txt-to-pdf='soffice --headless --convert-to pdf --outdir ./ *.txt'
alias qq-libreoffice-convert-png-to-pdf='soffice --headless --convert-to pdf --outdir ./ *.png'
alias qq-libreoffice-convert-jpg-to-pdf='soffice --headless --convert-to pdf --outdir ./ *.jpg'
alias qq-libreoffice-convert-jpeg-to-pdf='soffice --headless --convert-to pdf --outdir ./ *.jpeg'
alias qq-fs-structure-export-xlsx='find -printf "%P\n" > listing.xlsx'

## GIT - Global
alias qq-git-full='qq-git-status && qq-git-add && qq-git-commit && qq-git-push && qq-git-status'
alias qq-git-status='git status'
alias qq-git-add='git add .'
alias qq-git-commit='git commit -m "Commit: `date`"'
alias qq-git-push='git push'
alias qq-git-tree='git ls-tree -r --name-only HEAD | tree --fromfile'

## GIT - htdocs
alias qq-git-htdocs-status='cd /mnt/HDD_1/01_Apps/Servers_Local/htdocs; git status'
alias qq-git-htdocs-add='cd /mnt/HDD_1/01_Apps/Servers_Local/htdocs; git add .'
alias qq-git-htdocs-commit='cd /mnt/HDD_1/01_Apps/Servers_Local/htdocs; git commit -m commit'
alias qq-git-htdocs-push='cd /mnt/HDD_1/01_Apps/Servers_Local/htdocs; git push --force https://oxyblade:TOKEN@github.com/oxyblade/www.git'

## GIT - oxyblade.github.io
alias qq-git-oxyblade_github_io-status='cd /mnt/HDD_1/03_JetBrainsProjects/oxyblade.github.io; git status'
alias qq-git-oxyblade_github_io-add='cd /mnt/HDD_1/03_JetBrainsProjects/oxyblade.github.io; git add .'
alias qq-git-oxyblade_github_io-commit='cd /mnt/HDD_1/03_JetBrainsProjects/oxyblade.github.io; git commit -m commit'
alias qq-git-oxyblade_github_io-push='cd /mnt/HDD_1/03_JetBrainsProjects/oxyblade.github.io; git push --force https://oxyblade:TOKEN@github.com/oxyblade/oxyblade.github.io.git'

## Work — Scripts
alias qq-work-script-php-domains-ping='php /mnt/HDD_1/02_Docs/WORK/003_Stuff/Scripts/script-php-domains-ping/script-php-domains-ping.php'
alias qq-work-script-php-domains-ssl='php /mnt/HDD_1/02_Docs/WORK/003_Stuff/Scripts/script-php-domains-ssl/script-php-domains-ssl.php'
alias qq-work-script-php-domains-unavailable='php /mnt/HDD_1/02_Docs/WORK/003_Stuff/Scripts/script-php-domains-unavailable/script-php-domains-unavailable.php'
```

___

```shell
## WireGuard
####### alias wireguard-nl-enable='sudo wg-quick up wg-NL'
####### alias wireguard-nl-disable='sudo wg-quick down wg-NL'
####### alias wireguard-us-enable='sudo wg-quick up wg-US'
####### alias wireguard-us-disable='sudo wg-quick down wg-US'
####### alias wireguard-jp-enable='sudo wg-quick up wg-JP'
####### alias wireguard-jp-disable='sudo wg-quick down wg-JP'
## GIT - projects
####### alias qq-git-projects-status='cd /mnt/HDD_2/GitHub/projects; git status'
####### alias qq-git-projects-add='cd /mnt/HDD_2/GitHub/projects; git add .'
####### alias qq-git-projects-commit='cd /mnt/HDD_2/GitHub/projects; git commit -m commit'
####### alias qq-git-projects-push='cd /mnt/HDD_2/GitHub/projects; git push --force https://oxyblade:TOKEN@github.com/oxyblade/projects.git'

## GIT - projects-custom-01
####### alias qq-git-projects_custom_01-status='cd /mnt/HDD_2/GitHub/projects-custom-01; git status'
####### alias qq-git-projects_custom_01-add='cd /mnt/HDD_2/GitHub/projects-custom-01; git add .'
####### alias qq-git-projects_custom_01-commit='cd /mnt/HDD_2/GitHub/projects-custom-01; git commit -m commit'
####### alias qq-git-projects_custom_01-push='cd /mnt/HDD_2/GitHub/projects-custom-01; git push --force https://oxyblade:TOKEN@github.com/oxyblade/projects-custom-01.git'

## VPS Instances
####### alias vps-oracle-1='ssh ubuntu@158.101.203.99'
####### alias vps-oracle-2='ssh ubuntu@141.144.206.42'
####### alias vps-aws-1='ssh -i ~/.ssh/aws-vps-1.pem ubuntu@3.135.117.225'
```
