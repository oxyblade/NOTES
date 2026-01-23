### *General commands*

```
journalctl | grep -inE 'Out of memory'
```
```
journalctl | grep -inE 'oom'
```
```
journalctl --since "00:00" | grep -inE 'Out of memory'
```
```
journalctl --since "00:00" | grep -inE 'ssh'
```
```
journalctl --since "2026-01-15"
```
```
journalctl --since "2026-01-15 10:00:00"
```
```
journalctl -u mysql --since "2026-01-15 03:00" --until "2026-01-15 06:00"
```

___

### *otlichnici.ru (Example)*

```
cat /var/www/httpd-logs/otlichnici.ru.error.log | grep -inE 'Out of memory'
```
```
cat /var/www/httpd-logs/otlichnici.ru.error.log | grep -inE 'Out of memory' | wc -l
```
```
cat /var/www/httpd-logs/otlichnici.ru.access.log | grep -inE 'bot/'
```
```
cat /var/www/httpd-logs/otlichnici.ru.access.log | grep -inE 'bot/' | wc -l
```
```
cat /var/www/httpd-logs/otlichnici.ru.access.log | grep -inE 'wp-cron.php'
```
```
cat /var/www/httpd-logs/otlichnici.ru.access.log | grep -inE 'wp-cron.php' | wc -l
```

```
less /var/www/httpd-logs/otlichnici.ru.access.log
```
```
less /var/www/httpd-logs/otlichnici.ru.error.log
```

*Top 10 active IP-addresses in access log:*
```
grep "$(date '+%d/%b/%Y')" /var/www/httpd-logs/otlichnici.ru.access.log | awk '{print $1}' | sort | uniq -c | sort -nr | head -10
```

*Top-20 Bot's log:*
```
grep -oiE '"[^"]+"' "/var/www/httpd-logs/otlichnici.ru.access.log" | grep -oiE '\b[a-zA-Z0-9./;+_-]*bot[a-zA-Z0-9./;+_-]*\b' | sort | uniq -c | sort -nr | head -n20
```

___

less /var/log/dnf.log
tail -f -n100 /var/log/dnf.log
tail -f -n1000 /var/log/dnf.log