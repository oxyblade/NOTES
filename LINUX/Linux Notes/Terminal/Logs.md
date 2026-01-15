```
journalctl | grep -inE 'Out of memory'
```
```
journalctl | grep -inE oom
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

less /var/log/dnf.log
tail -f -n100 /var/log/dnf.log
tail -f -n1000 /var/log/dnf.log