systemctl list-unit-files --state=enabled
systemctl --state=failed
systemctl --state=masked
systemctl --state=not-found
systemctl --state=active
systemctl --state=inactive
systemctl list-timers
systemctl list-units --type=target
systemctl list-units --type=service
systemctl show remote-fs.target
systemctl cat remote-fs.target
systemctl status/(re)start/stop/enable/disable/mask/is-failed dbus.service
systemctl get-default
systemctl list-dependencies graphical.target
systemctl status
systemctl show

psensor - tray utility
htop Процессы системы в реальном времени
top или top -SH Процессы системы в реальном времени
nmon Системный мониторинг
xrestop Монитор потребления ресурсов X-сервера разными приложениями
atop Мониторинг производительности
dstat Мониторинг процессора, дисковой нагрузки, сетевой нагрузки, памяти и т.п.
systemctl list-units -t service Запущенные сервисы (текущие)

ps auxwww | grep 'Z' Zombie processes
ps aux | awk '{ print $8 " " $2 }' | grep -w Z Zombie processes
ps afuwwx | less +u -p'^(\S+\s+){7}Z.*' Zombie processes
ps -eo pmem,ppid,comm | sort -k 1 -r | head -21 | tail -20

ll /proc/2043805/exe Check path of process
watch grep MHz /proc/cpuinfo Частота ядер процессора в реальном времени
grep MHz /proc/cpuinfo Частота ядер процессора
cpufreq-info Набор утилит для масштабирования частоты процессора
lscpu Архитектура процессора
cat /proc/cpuinfo Архитектура процессора
hwloc-ls Структура процессора
ifconfig Определение Ethernet интерфейсов
sudo lshw -class network Определение Ethernet интерфейсов (подробнее)

sudo powertop Мониторинг потребления мощности (электрической мощности) разными процессами

sudo smartctl -a /dev/sda S.M.A.R.T. дисков
