sudo nano /etc/apt/sources.list
Удалить содержимое, всавить следующее:

deb http://deb.debian.org/debian bullseye-updates main contrib non-free
deb-src http://deb.debian.org/debian bullseye-updates main contrib non-free

deb http://mirror.corbina.net/debian bullseye main contrib non-free
deb-src http://mirror.corbina.net/debian bullseye main contrib non-free

deb http://security.debian.org/debian-security bullseye-security main contrib non-free
deb-src http://security.debian.org/debian-security bullseye-security main contrib non-free

-----------------------

Прочтем репозитории
sudo apt-get update

Исправим ошибку времени (если пользуетесь Windows)
timedatectl set-local-rtc 1 --adjust-system-clock

Подключить 32 битную архитектуру
sudo dpkg --add-architecture i386

После этого выполняем
sudo apt-get update

Добавляем репозиторий "мультимедия"
sudo apt-get install wget

sudo nano /etc/apt/sources.list
Вставить следующее
deb https://www.deb-multimedia.org bullseye main non-free

И выполняем после сохранения (одна команда)
wget http://www.deb-multimedia.org/pool/main/d/deb-multimedia-keyring/deb-multimedia-keyring_2016.8.1_all.deb
sudo dpkg -i deb-multimedia-keyring_2016.8.1_all.deb

После этого выполняем
sudo apt-get update
sudo apt dist-upgrade

Устанавливаем FFMPEG
sudo apt-get install ffmpeg

Устанвливаем мисрокод (драйвера)
sudo apt-get install firmware-linux

--------------------------

Устанавливаем видео драйвер NVIDIA
sudo apt-get update
sudo apt-get install nvidia-driver

Synapitic быстрый фильтр:
sudo apt-get install apt-xapian-index
sudo update-apt-xapian-index -vf

Автологин (для Cinnamon)
nano /etc/lightdm/lightdm.conf
Ищем строку #autologin-user=
И меняем ее на   autologin-user=[ВАШ НИК]
sudo reboot