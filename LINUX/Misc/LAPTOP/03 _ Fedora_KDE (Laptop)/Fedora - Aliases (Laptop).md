```shell
## System
alias qq-update-full='sudo dnf upgrade --refresh && flatpak update && flatpak uninstall --unused'
alias qq-dnf-clean='sudo dnf autoremove && sudo dnf clean all'
alias qq-dnf-makecache='sudo dnf makecache'
alias qq-dnf-upgrade-refresh='sudo dnf upgrade --refresh'
alias qq-dnf-install='sudo dnf install'
alias qq-dnf-remove='sudo dnf remove'
alias qq-dnf-search='dnf search'
alias qq-dnf-info='dnf info'
alias qq-free='free -m'
alias qq-fstab-config='nano -v /etc/fstab'
alias qq-grub-config='nano -v /etc/default/grub'
alias qq-kernels='rpm -qa kernel-core && echo "" && dnf list installed kernel'
alias qq-btrfs='sudo btrfs filesystem show && echo "" && sudo btrfs filesystem df / && echo "" && sudo btrfs filesystem usage / && echo "" && sudo btrfs device stats /'
alias qq-fs-compsize='sudo compsize -x'
alias qq-system-grub2-mkconfig='sudo grub2-mkconfig --output=/boot/grub2/grub.cfg'
alias qq-system-sb-status='mokutil --sb-state && echo "pk:" && mokutil --pk && echo "db:" && mokutil --db && echo "kek:" && mokutil --kek && echo "dbx:" && mokutil --dbx | wc -l'
alias qq-system-process-ram-load='ps -eo pmem,ppid,comm | sort -k 1 -r | head -21 | tail -20'
alias qq-system-process-zombie='ps aux | grep defunct'
alias qq-system-process-service-running='systemctl list-units --type service --state running'
alias qq-system-process-service-exited='systemctl list-units --type service --state exited'
alias qq-system-systemd-analyze='systemd-analyze'
alias qq-system-systemd-analyze-critical-chain='systemd-analyze critical-chain'
alias qq-system-systemd-analyze-blame='systemd-analyze blame'
alias qq-system-systemd-analyze-plot-export-svg='systemd-analyze plot > ~/bootup.svg'
alias qq-system-sleep-suspend-hibernate-hybridSleep='systemctl status sleep.target suspend.target hibernate.target hybrid-sleep.target'
alias qq-system-inxi='inxi -Fxxxrs'
alias qq-system-tracker-info='tracker3 status && tracker3 daemon'
alias qq-system-cpu-vulnerability-check='lscpu | grep -i Vulnerability'
alias qq-system-dmesg-grep='sudo dmesg | grep -i'
alias qq-system-iostat='iostat'
alias qq-sensors-cpu-temperature='watch -n 1 sensors'
alias qq-sensors-cpu-frequency='watch -n 1 grep MHz /proc/cpuinfo'
alias qq-sensors-gpu-intel='sudo watch -n 1 intel_gpu_frequency && sudo intel_gpu_top'
alias qq-sensors-gpu-nvidia='watch -n 1 nvidia-smi'
alias qq-sensors-gpu-nvtop='nvtop'
alias qq-sensors-smart-sda='sudo smartctl -a /dev/sda'
alias qq-sensors-smart-sdb='sudo smartctl -a /dev/sdb'
alias qq-sensors-smart-sdc='sudo smartctl -a /dev/sdc'
alias qq-ping='ping -c 3'
alias qq-tool-nano='nano -vl'
alias qq-tool-grep='grep -inE'
alias qq-tool-grep-recursive='grep -r'
alias qq-tool-files-du-1='du -sh * | sort -h'
alias qq-tool-files-du-2='du -h | sort -h'
alias qq-tool-files-gdu-root='gdu /'
alias qq-tool-files-gdu-home='gdu'
alias qq-tool-files-gdu-usb_hdd_1='gdu /mnt/USB_HDD_1'
alias qq-tool-files-gdu-usb_hdd_2='gdu /mnt/USB_HDD_2'
alias qq-tool-files-gdu-usb_hdd_3='gdu /mnt/USB_HDD_3'
alias qq-tool-duf='watch -n 1 duf'
alias qq-tool-password-generation-pwgen='pwgen -syB'
alias qq-firewall-status='sudo firewall-cmd --list-all'
alias qq-firewall-reload='sudo firewall-cmd --reload'
alias qq-archive-zip-extract='unzip -o *.zip'
alias qq-archive-rar-extract='unrar x -o+ *.rar'
alias qq-archive-7z-extract='7z x -y *.7z'
alias qq-archive-external-lib-rar-add-all='~/STORAGE_ASUS/01_Apps/Apps_Portable/002/rar/rar a -m5 Archive *'
alias qq-archive-external-lib-rar-add-single='~/STORAGE_ASUS/01_Apps/Apps_Portable/rar/rar a -m5 Archive'
alias qq-archive-external-lib-rar-test='~/STORAGE_ASUS/01_Apps/Apps_Portable/002/rar/rar t'
alias qq-archive-external-lib-rar-extract-single='~/STORAGE_ASUS/01_Apps/Apps_Portable/002/rar/rar x'
alias qq-optirun='__NV_PRIME_RENDER_OFFLOAD=1'

## Packages & Apps
alias qq-flatpak-update='flatpak update && flatpak uninstall --unused'
alias qq-flatpak-uninstall-delete-data='flatpak uninstall --delete-data'
alias qq-flatpak-installation-list='flatpak --columns=app,name,version,size,installation list'
alias qq-flatpak-depends='flatpak list --app --columns=application,runtime'
alias qq-flatpak-app-info='flatpak list | grep -i'
alias qq-flatpak-remote-info='flatpak remote-info --log flathub'
alias qq-pkg-process-name='ps aux | grep'
alias qq-pkg-process-name-pid='ps -Flww -p'
alias qq-pkg-list-all='dnf list all'
alias qq-pkg-list-installed='dnf list installed'
alias qq-pkg-list-available='dnf list available'
alias qq-pkg-repolist='dnf repolist'
alias qq-pkg-history-list='dnf history list'
alias qq-root-hifile='sudo ~/STORAGE_ASUS/01_Apps/Apps_Portable/001/HiFile/HiFile.AppImage'
alias qq-root-doublecommander='sudo ~/STORAGE_ASUS/01_Apps/Apps_Portable/001/doublecmd/doublecmd'
alias qq-root-sublime_text='sudo ~/STORAGE_ASUS/01_Apps/Apps_Portable/001/sublime_text/sublime_text'

## System Logs
alias qq-journalctl-log-search='journalctl | grep -i'
alias qq-journalctl-disk-usage='journalctl --disk-usage'
alias qq-journalctl-verify='journalctl --verify'
alias qq-journalctl-boot-current='journalctl -b'
alias qq-journalctl-boot-1Day='journalctl -b -1'
alias qq-journalctl-boot-2Day='journalctl -b -2'
alias qq-journalctl-boot-3Day='journalctl -b -3'
alias qq-log-boot='sudo lnav /var/log/boot.log'
alias qq-log-dnf-events='lnav /var/log/dnf.log'
alias qq-log-dnf-rpm='lnav /var/log/dnf.rpm.log'
####### alias qq-log-xorg0='lnav ~/.local/share/xorg/Xorg.0.log'

## Network
alias qq-network-ifconfig='watch -n 1 ifconfig'
alias qq-network-interfaces='echo "PC network interfaces:" && echo "" && nmcli -p device show' # PC network interfaces
alias qq-network-ip-internal='ip addr | grep -i "inet " && echo "" && ifconfig -a | grep -i "inet " '
alias qq-network-ip-external='curl https://ipinfo.io && echo "" && echo ""' # wget -qO- ifconfig.co # ifconfig.me
alias qq-network-netstat='watch -n 1 netstat -antp && netstat -lpn'
alias qq-network-iftop='sudo iftop'
alias qq-network-nmap-scan-domain-ip-dns-1='sudo nmap -sTU -O'
alias qq-network-nmap-scan-domain-ip-dns-2='sudo nmap -n -PN -sT -sU -p-'
alias qq-network-nmap-scan-home='nmap -sP 192.168.100.1/24'
alias qq-network-resolvectl-dns-local='resolvectl status'
alias qq-network-wifi-list='nmcli device wifi list'
alias qq-network-sslscan='sslscan'

## System Scripts
alias qq-sensors-full='~/STORAGE_ASUS/01_Apps/Apps_Backup/01_LINUX/Overall_Files/Scripts/qq-script-sensors-laptop.sh'
alias qq-script-df-lsblk='~/STORAGE_ASUS/01_Apps/Apps_Backup/01_LINUX/Overall_Files/Scripts/qq-script-df-lsblk.sh'
alias qq-script-dns-ping='~/STORAGE_ASUS/01_Apps/Apps_Backup/01_LINUX/Overall_Files/Scripts/qq-script-dns-ping.sh'
alias qq-script-hostname='~/STORAGE_ASUS/01_Apps/Apps_Backup/01_LINUX/Overall_Files/Scripts/qq-script-hostname.sh'
alias qq-script-npm-yarn-sudo='sudo ~/STORAGE_ASUS/01_Apps/Apps_Backup/01_LINUX/Overall_Files/Scripts/qq-script-npm-yarn-sudo.sh'
alias qq-script-ports-local-sudo='sudo ~/STORAGE_ASUS/01_Apps/Apps_Backup/01_LINUX/Overall_Files/Scripts/qq-script-ports-local-sudo.sh'
alias qq-script-resources-laptop='~/STORAGE_ASUS/01_Apps/Apps_Backup/01_LINUX/Overall_Files/Scripts/qq-script-resources-laptop.sh'

## Extended Scripts
alias qq-script-external-geekbench='sudo ~/STORAGE_ASUS/01_Apps/Apps_Portable/002/Geekbench/geekbench6'
alias qq-script-external-memconf='sudo ~/STORAGE_ASUS/01_Apps/Apps_Portable/002/memconf/memconf.pl'
alias qq-script-external-spectre-meltdown-checker='sudo ~/STORAGE_ASUS/01_Apps/Apps_Portable/002/spectre-meltdown-checker/spectre-meltdown-checker.sh'

## XAMPP Local Server
alias xampp='sudo /opt/lampp/manager-linux-x64.run'
alias xampp-status='xampp status apache && xampp status mysql' # Alternative: sudo /opt/lampp/lampp status apache
alias xampp-start='xampp start apache && xampp start mysql && xampp status apache && xampp status mysql'
alias xampp-stop='xampp stop apache && xampp stop mysql && xampp status apache && xampp status mysql'
alias xampp-restart='xampp restart apache && xampp restart mysql && xampp status apache && xampp status mysql'
alias xampp-permissions-777='sudo chmod -R 777 ~/STORAGE_ASUS/01_Apps/Servers_Local/htdocs/'
alias xampp-permissions-755='sudo chmod -R 755 ~/STORAGE_ASUS/01_Apps/Servers_Local/htdocs/'
alias xampp-permissions-directories-755='sudo find ~/STORAGE_ASUS/01_Apps/Servers_Local/htdocs/ -type d -exec chmod 755 {} \;'
alias xampp-permissions-files-644='sudo find ~/STORAGE_ASUS/01_Apps/Servers_Local/htdocs/ -type f -exec chmod 644 {} \;'

## Apache Local Server
alias qq-apache-status='sudo systemctl status httpd.service'
alias qq-apache-start='sudo systemctl start httpd.service'
alias qq-apache-stop='sudo systemctl stop httpd.service'
alias qq-apache-reload='sudo systemctl reload httpd.service'
alias qq-apache-restart='sudo systemctl restart httpd.service'
alias qq-apache-enable='sudo systemctl enable httpd.service'
alias qq-apache-disable='sudo systemctl disable httpd.service'
alias qq-apache-permissions='sudo chmod -R 777 /srv/http/'
alias qq-apache-configtest='apachectl configtest'

## Misc
alias qq-vm-libvirtd-service-status='sudo systemctl status libvirtd.service'
alias qq-vm-libvirtd-service-start='sudo systemctl start libvirtd.service'
alias qq-vm-libvirtd-service-stop='sudo systemctl stop libvirtd.service'
alias qq-vm-libvirtd-service-disable='sudo systemctl disable libvirtd.service'
alias qq-vm-libvirtd-service-enable='sudo systemctl enable libvirtd.service'
alias qq-vm-libvirtd-service-restart='sudo systemctl restart libvirtd.service'
alias qq-libreoffice-convertALL-to-pdf='soffice --headless --convert-to pdf --outdir ./ *.docx *.doc *.rtf *.odt *.pptx *.ppt *.xlsx *.xls *.txt *.png *.jpg *.jpeg *.djvu'
alias qq-libreoffice-fs-structure-convertALL-to-pdf='find . -type f \( -name "*.docx" -o -name "*.doc" -o -name "*.rtf" -o -name "*.odt" -o -name "*.pptx" -o -name "*.ppt" -o -name "*.xlsx" -o -name "*.xls" -o -name "*.txt" -o -name "*.png" -o -name "*.jpg" -o -name "*.jpeg" -o -name "*.djvu" \) -execdir soffice --headless --convert-to pdf "{}" \;'
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
alias qq-libreoffice-convert-djvu-to-pdf='soffice --headless --convert-to pdf --outdir ./ *.djvu'
alias qq-fs-structure-export-xlsx='find -printf "%P\n" > listing.xlsx'

## GIT - Global
alias qq-git-full='qq-git-status && qq-git-add && qq-git-commit && qq-git-push && qq-git-status'
alias qq-git-status='git status'
alias qq-git-add='git add .'
alias qq-git-commit='git commit -m "Commit: `date`"'
alias qq-git-push='git push'
alias qq-git-tree='git ls-tree -r --name-only HEAD | tree --fromfile'

## GIT - htdocs
alias qq-git-htdocs-status='cd ~/STORAGE_ASUS/01_Apps/Servers_Local/htdocs; git status'
alias qq-git-htdocs-add='cd ~/STORAGE_ASUS/01_Apps/Servers_Local/htdocs; git add .'
alias qq-git-htdocs-commit='cd ~/STORAGE_ASUS/01_Apps/Servers_Local/htdocs; git commit -m commit'
alias qq-git-htdocs-push='cd ~/STORAGE_ASUS/01_Apps/Servers_Local/htdocs; git push --force https://oxyblade:TOKEN@github.com/oxyblade/www.git'

## GIT - oxyblade.github.io
alias qq-git-oxyblade_github_io-status='cd ~/STORAGE_ASUS/03_JetBrainsProjects/oxyblade.github.io; git status'
alias qq-git-oxyblade_github_io-add='cd ~/STORAGE_ASUS/03_JetBrainsProjects/oxyblade.github.io; git add .'
alias qq-git-oxyblade_github_io-commit='cd ~/STORAGE_ASUSD/03_JetBrainsProjects/oxyblade.github.io; git commit -m commit'
alias qq-git-oxyblade_github_io-push='cd ~/STORAGE_ASUS/03_JetBrainsProjects/oxyblade.github.io; git push --force https://oxyblade:TOKEN@github.com/oxyblade/oxyblade.github.io.git'

## Work — Scripts
alias qq-work-script-php-domains-ping='php ~/STORAGE_ASUS/02_Docs/WORK/003_Stuff/Scripts/script-php-domains-ping/script-php-domains-ping.php'
alias qq-work-script-php-domains-ssl='php ~/STORAGE_ASUS/02_Docs/WORK/003_Stuff/Scripts/script-php-domains-ssl/script-php-domains-ssl.php'
alias qq-work-script-php-domains-unavailable='php ~/STORAGE_ASUS/02_Docs/WORK/003_Stuff/Scripts/script-php-domains-unavailable/script-php-domains-unavailable.php'

## NodeJS
export NODEJS_HOME=/home/andrew/STORAGE_ASUS/01_Apps/Apps_Portable/002/node/bin
export PATH=$NODEJS_HOME:$PATH
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
####### alias qq-git-projects-status='cd /mnt/SEAGATE/GitHub/projects; git status'
####### alias qq-git-projects-add='cd /mnt/SEAGATE/GitHub/projects; git add .'
####### alias qq-git-projects-commit='cd /mnt/SEAGATE/GitHub/projects; git commit -m commit'
####### alias qq-git-projects-push='cd /mnt/SEAGATE/GitHub/projects; git push --force https://oxyblade:TOKEN@github.com/oxyblade/projects.git'

## GIT - projects-custom-01
####### alias qq-git-custom_projects_01-status='cd /mnt/SEAGATE/GitHub/projects-custom-01; git status'
####### alias qq-git-custom_projects_01-add='cd /mnt/SEAGATE/GitHub/projects-custom-01; git add .'
####### alias qq-git-custom_projects_01-commit='cd /mnt/SEAGATE/GitHub/projects-custom-01; git commit -m commit'
####### alias qq-git-custom_projects_01-push='cd /mnt/SEAGATE/GitHub/projects-custom-01; git push --force https://oxyblade:TOKEN@github.com/oxyblade/projects-custom-01.git'

## VPS Instances
####### alias vps-oracle-1='ssh ubuntu@158.101.203.99'
####### alias vps-oracle-2='ssh ubuntu@141.144.206.42'
####### alias vps-aws-1='ssh -i ~/.ssh/aws-vps-1.pem ubuntu@3.135.117.225'
```
