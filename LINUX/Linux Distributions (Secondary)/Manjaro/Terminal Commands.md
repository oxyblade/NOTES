sudo pacman -Sy		-- Synchronizing package databases
sudo pacman -Syu 	-- Synchronizing & Full system upgrade (packages)
sudo pacman -Ss 		-- Search packages or list (+ description)
sudo pacman -Ssq	-- Search packages or list (- description)
sudo pacman -S 		-- Install packages
sudo pacman -R 		-- Remove packages
sudo pacman -Rs 		-- Remove packages, unrequired dependencies
sudo pacman -Rsn 	-- Remove packages, unrequired dependencies, configs

sudo pacman -Sc		-- Remove packages that are no longer installed from the cache
sudo pacman -Scc		-- Remove ALL packages from the cache
sudo pacman -Qdtq				-- Check unrequired dependencies
sudo pacman -R $(pacman -Qdtq) 	-- Remove unrequired dependencies

pacman -Ssq | wc -l - Count of packages

___

mhwd
mhwd-gpu
mhwd-kernel

Switch to the newer linux66 (KERNEL) series:
sudo mhwd-kernel -i linux66

___

~/.zshrc
Aliases:
alias qq-pacman-update-upgrade-full='sudo pacman -Sy && sudo pacman -Syu && sudo pacman -Sc && flatpak update -y && flatpak uninstall --unused -y'

___

GRUB_CMDLINE_LINUX_DEFAULT="verbose apparmor=1 security=apparmor udev.log_priority=3"
cat /var/log/pacman.log -- Packages updates log
