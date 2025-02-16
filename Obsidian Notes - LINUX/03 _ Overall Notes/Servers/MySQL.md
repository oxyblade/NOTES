MySQL LOGS optimize (binlog files):
/etc/mysql/my.cnf (MySQL config)
/var/lib/mysql (binlog files)

binlog-expire-logs-seconds = 86400
max-binlog-size = 104857600

restart mysql

___

Disable binlog files:
/etc/mysql/my.cnf
Add these lines at the bottom of the file:

[mysqld]
skip-log-bin

restart mysql