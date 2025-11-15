The following packages have been kept back:
sudo apt-get --with-new-pkgs upgrade
( sudo apt-get install <list of packages kept back> )

dpkg -l Список установленных пакетов
dpkg -l | grep opera Поиск пакета
apt-cache show [] Описание установленного пакета
apt-cache depends [] Просмотр зависимостей пакета
whereis doublecmd

Install DEB:
cd ~/folder
sudo dpkg -i myprogramm.deb

sudo apt-get --fix-missing install
sudo apt-get --fix-broken install
sudo apt-get install -f

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
sudo apt-key adv --keyserver ha.pool.sks-keyservers.net --recv-keys 40976EAF437D05B5


sudo apt-get install build-essential automake autoconf
