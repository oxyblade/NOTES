## LOGS

#### MySQL LOGS optimize (binlog files)
/etc/mysql/my.cnf (MySQL config)
/var/lib/mysql (binlog files)

binlog-expire-logs-seconds = 86400
max-binlog-size = 104857600 (100M)

restart mysql

#### Disable binlog files
/etc/mysql/my.cnf
Add these lines at the bottom of the file:

[mysqld]
skip-log-bin

restart mysql

___
## MISC Options

[mysqld]
character-set-server = utf8
collation-server = utf8_general_ci
init-connect = "SET NAMES utf8"

bind-address = localhost
symbolic-links = 0
interactive_timeout = 60
wait_timeout = 60

####### key_buffer_size = 16M
key_buffer_size = 256M
sort_buffer_size = 32M
####### max_allowed_packet = 64M
####### thread_stack = 256K

####### thread_cache_size = -1
thread_cache_size = 16

max_heap_table_size = 128M
tmp_table_size = 128M
innodb_buffer_pool_size = 10G
innodb_buffer_pool_instances = 4
innodb_log_file_size = 256M
innodb_log_buffer_size = 32M
innodb_flush_log_at_trx_commit = 0
innodb_read_io_threads = 16
innodb_write_io_threads = 16
innodb_thread_concurrency = 12
innodb_stats_on_metadata = 0
performance_schema = OFF
skip-log-bin
sync_binlog = 0

myisam-recover-options = BACKUP
max_connections = 250

####### table_open_cache = 4000
table_open_cache = 4096

innodb_file_per_table = 1
innodb_open_files = 4096

####### binlog_expire_logs_seconds	= 86400 - 259200
binlog_expire_logs_seconds	= 86400
max_binlog_size = 100M (104857600)
####### binlog_do_db = include_database_name
####### binlog_ignore_db = include_database_name

restart mysql