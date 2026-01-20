### systemctl
systemctl list-units --type=service --state=running
systemctl list-unit-files --state=enabled
systemctl list-units --type=target
systemctl --state=failed
systemctl --state=masked
systemctl --state=not-found
systemctl --state=active
systemctl --state=inactive
systemctl list-timers
systemctl show remote-fs.target
systemctl cat remote-fs.target
systemctl status/(re)start/stop/enable/disable/mask/is-failed dbus.service
systemctl get-default
systemctl list-dependencies graphical.target
systemctl status
systemctl show

systemctl list-units --type=service
dmesg -T
free -m
df -h

___
### Processes & Services
ls -l /proc/9600/exe (9600 — process ID, Check path of process)
lsof -p 1111,2222 | grep cwd
ps auxwww | grep 'Z' Zombie processes
ps aux | awk '{ print $8 " " $2 }' | grep -w Z Zombie processes
ps afuwwx | less +u -p'^(\S+\s+){7}Z.*' Zombie processes
ps -eo pmem,ppid,comm | sort -k 1 -r | head -21 | tail -20

___
### Hardware
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

___
### Packages & Utils
psensor - tray utility
htop Процессы системы в реальном времени
top или top -SH Процессы системы в реальном времени
nmon Системный мониторинг
xrestop Монитор потребления ресурсов X-сервера разными приложениями
dstat Мониторинг процессора, дисковой нагрузки, сетевой нагрузки, памяти и т.п.

___
### atop
Мониторинг производительности

```
apt install atop
systemctl enable atop && systemctl status atop
```

```
sudo nano /etc/default/atop
```
```
sudo systemctl restart atop && systemctl status atop
```

LOGOPTS="-R"
LOGINTERVAL=60 (600)
LOGGENERATIONS=14 (28)
LOGPATH=/var/log/atop

```
atopsar -r /var/log/atop/atop_20260114
```
```
atopsar -r /var/log/atop/atop_20260114 -O
```
```
atopsar -r /var/log/atop/atop_20260114 -G
```

___

### nvidia-smi

```
nvidia-smi
```

View the current performance state, power limit of the GPU
```
watch -n 1 nvidia-smi -q -d PERFORMANCE
watch -n 1 nvidia-smi -q -d POWER
```

To set a preferred power management mode *(Optional: sudo nvidia-smi -pm ENABLED)*
```
sudo nvidia-smi -pm 1
```

To force maximum performance mode *(OPTIONAL)*
```
sudo nvidia-smi -acp 0
```

Set power limit
```
sudo nvidia-smi -pl 30
```

> To create the script run the command: `nano ~/nvidia-performance.sh`. Here is the exact script that I wrote:
> 
> `#!/bin/bash`
> `# Enable persistence mode`
> `sudo nvidia-smi -pm 1`
> `# Set power limit to 30 Watts`
> `sudo nvidia-smi -pl 30`
> 
>  File permission:
> `sudo chmod +x nvidia-performance.sh`
> 
> Now that we have a shell script created and have given it the execute permission we need to make it run every time the system boots. To do this, run the command:
> ```
> crontab -e
> ```
> 
> and add the line:
> ```
> @reboot sh /home/andrew/nvidia-performance.sh
> ```
> 
> Save the file. Next, to confirm the crontab job was added you can run the command `crontab -l` and it will list all the currently saved crontab jobs.
> 