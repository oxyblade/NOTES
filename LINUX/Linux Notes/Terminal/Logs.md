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
journalctl --since "2026-01-15"
```
```
journalctl --since "2026-01-15 10:00:00"
```
```
journalctl -u mysql --since "2026-01-15 03:00" --until "2026-01-15 06:00"
```

___

```
less /var/www/httpd-logs/otlichnici.ru.access.log
```
```
less /var/www/httpd-logs/otlichnici.ru.error.log
```

## *otlichnici.ru*
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
cat /var/www/httpd-logs/otlichnici.ru.error.log | grep -inE 'Out of memory'
```
```
cat /var/www/httpd-logs/otlichnici.ru.error.log | grep -inE 'Out of memory' | wc -l
```

## *kursar.su*
```
cat /var/www/httpd-logs/kursar.su.access.log | grep -inE 'bot/'
```
```
cat /var/www/httpd-logs/kursar.su.access.log | grep -inE 'bot/' | wc -l
```
```
cat /var/www/httpd-logs/kursar.su.error.log | grep -inE 'Out of memory'
```

___

less /var/log/dnf.log
tail -f -n100 /var/log/dnf.log
tail -f -n1000 /var/log/dnf.log