journalctl | grep -i oom
journalctl -u mysql --since "2025-12-18 03:00" --until "2025-12-18 06:00"

tail -f -n100 /var/log/mysql/error.log
tail -f -n1000 /var/log/mysql/error.log