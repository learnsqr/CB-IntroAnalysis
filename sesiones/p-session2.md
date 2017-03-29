# Logs

### Create a “clean” (original) version of the default config file by copying the existing my- small.cnf file.
cp /usr/share/mysql/my-small.cnf my.cnf

### Check to see if the general and slow query logs are turned on 

### Make sure that the logs are table-based by checking the log_output 

### Make a “clean” copy of the world_innodb database.

### Count the number of CREATE TABLE statements

SELECT COUNT(*) FROM mysql.general_log WHERE argument LIKE 'CREATE TABLE%'; 

### Create a query that makes it into the slow query log:
SELECT SLEEP(11); 

### View it from the slow_log table in the mysql database. 
SELECT * FROM mysql.slow_log \G

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





