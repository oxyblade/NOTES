sudo nethogs Просмотр загрузки сетевых интерфейсов
nload - Мониторинг трафика
bwm-ng Мониторинг трафика
bmon Мониторинг трафика нескольких сетевых интерфейсов
cbm Мониторинг трафика (GUI)
slurm -i wlp3s0 enp2s0 Мониторинг загруженности сетевых интерфейсов
nload enp2s0 (wlp3s0) Пропускная способность каналов

sudo iftop Трафик в реальном времени
sudo jnettop - Трафик в реальном времени

sudo iptraf-ng Мониторинг сетевого трафика
sudo iwlist scan Сканирование доступных Wi-Fi сетей
sudo iwconfig Определение беспроводного интерфейса
iwlist scan Информация и каналы беспроводных WI-FI точек
netstat -ntpl
netstat -a Активные соединения с Интернетом
netstat -tulpn - LISTEN ports
netstat -tulpn | grep LISTEN
ss -t -a - TCP sockets
ss -u -a - UDP sockets
ss, ss -l - show opened network and local sockets
ifconfig Посмотреть конфигурацию сети, сетевого адаптера, transmit (ТХ) или receive (RX) ошибки

===========================================================================================================================

speedtest - Network Speed

ping -c 5 192.168.1.1
mtr Traceroute and Ping
traceroute Определение маршрутов следования данных в сетях TCP/IP
nslookup Определить IP-адреса для доменного имени и обратно
host Определить IP-адреса
wget -E -H -k -K -p https://www.slashdot.org Тест Интернета (сети)
netstat -an --inet | grep LISTEN | grep -v 127.0.0.1 (Check Opened Ports)
curl --head cnn.com

python3 -m http.server
