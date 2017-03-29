# Binary Log

### Edit the my.cnf file (located in the /etc directory) in the [mysqld] section to turn on binary logging.
[mysqld]
log-bin = mysql-bin

SHOW GLOBAL VARIABLES LIKE 'log_bin';

### Erase all logs. 
RESET MASTER;

###  Perform a data changing operation and list it from the binary log.
CREATE DATABASE foo;
DROP DATABASE foo;

### And list it from the binary log
SHOW BINLOG EVENTS;

###  Rotate the binary logs explicitly using FLUSH LOGS 
FLUSH LOGS;

### List all your binary logs (for mysql-bin.000002),
SHOW MASTER LOGS;

### List changes. 
SHOW BINLOG EVENTS IN 'mysql-bin.000002';

### Delete the first binary log. 
PURGE MASTER LOGS TO 'mysql-bin.000002'; 

###  Perform a data changing operation.
CREATE DATABASE foo_2
DROP DATABASE foo_2;

### Use mysqlbinlog to display all entries in the binary log
mysqlbinlog /var/lib/mysql/mysql-bin.000002

###ÊLook in the mysql-bin.000002 binary log file. What was the event number for the drop of the foo_2 database? 
352



