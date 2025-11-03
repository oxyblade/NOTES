#### Fix 1:
Disable sssd from starting on systems where it's not needed.
sudo systemctl stop sssd
sudo systemctl disable sssd

#### Fix 2:
sudo cp /usr/lib/x86_64-linux-gnu/sssd/conf/sssd.conf /etc/sssd/.
sudo chmod 600 /etc/sssd/sssd.conf 
sudo systemctl enable sssd
sudo systemctl start sssd

#### Fix 3:
Properly configure sssd, using /etc/sssd/sssd.conf, to your site's specific needs. See man sssd.conf for more information.