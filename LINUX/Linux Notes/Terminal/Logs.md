`journalctl | grep -i oom`
`journalctl --since "10:00"` (today at a specific time)
`journalctl --since "2025-12-18"` (specific date, time defaults to 00:00:00)
`journalctl --since "2025-12-18 10:00:00"` (specific date and time)
`journalctl -u mysql --since "2025-12-18 03:00" --until "2025-12-18 06:00"`

`less /var/log/dnf.log`
`tail -f -n100 /var/log/dnf.log`
`tail -f -n1000 /var/log/dnf.log`