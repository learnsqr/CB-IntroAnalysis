# Master - Slave

### What is the IP address for the master server
/sbin/ifconfig eth0 | grep 'inet addr:'

### On the master server, create a user called slave with the host from the slave server 
CREATE USER 'slave'@'10.150.21.226' -> IDENTIFIED BY 'opensaysame';

### On the master server, grant the user created in step 2 with the REPLICATION SLAVE privileg
GRANT REPLICATION SLAVE ON *.* -> TO 'slave'@'10.150.21.226';

### On the master server, using the second terminal window from the previous practice, create a backup of the world_innodb table
mysqldump --user=root --password=oracle --master-data=2 world_innodb > master_backup.sql

### On the master server, view the output of the master_backup.sql
Locate the line that begins with --CHANGE MASTER TO
MASTER_LOG_FILE?
MASTER_LOG_POS?

### On the slave server, open a terminal window and log in as root.

###ÊOn the slave server, verify that the master_backup.sql file was transferred from the master server.

### On the slave server, overwrite the existing /etc/my.cnf file with the my-medium.cnf

### On the slave server, edit the /etc/my.cnf file and remark out the log-bin, binlog_format, and server-id lines under the Replication Master Server section.
	# Replication Master Server (default)
	# binary logging is required for replication 
	#log-bin = mysql-bin
	
	# binary logging format - mixed recommended 
	# binlog_format = mixed
	
	# required unique id between 1 and 2^32 - 1
	# defaults to 1 if master-host is not set
	# but will not function as a master if omitted 
	#server-id = 2

### On the slave server in the /etc/my.cnf file, unremark the server-id line underneath the Replication Slave section.
	# required unique id between 2 and 2^32 - 1 # (and different from the master)
	# defaults to 2 if master-host is set
	# but will not function as a slave if omitted server-id = 2

### On the slave server, edit the /etc/my.cnf file and make sure that the InnoDB options are all uncommented
	# Uncomment the following if you are using InnoDB tables
	innodb_data_home_dir = /var/lib/mysql
	innodb_data_file_path = ibdata1:10M:autoextend
	innodb_log_group_home_dir = /var/lib/mysql
	# You can set .._buffer_pool_size up to 50 - 80 %
	# of RAM but beware of setting memory usage too high
	innodb_buffer_pool_size = 16M
	innodb_additional_mem_pool_size = 2M
	# Set .._log_file_size to 25 % of buffer pool size
	innodb_log_file_size = 5M
	innodb_log_buffer_size = 10M
	innodb_flush_log_at_trx_commit = 1
	innodb_lock_wait_timeout = 50
	innodb_log_files_in_group = 2

###ÊOn the slave server, restart the MySQL server.

###ÊOn the slave server, start the mysql client.

### On the slave server, drop the world_innodb database, re-create it, and load in the master_backup.sql file to the re-created database.
	mysql> DROP DATABASE IF EXISTS world_innodb; Query OK, 11 rows affected (0.03 sec)
	mysql> CREATE DATABASE world_innodb;
	Query OK, 1 row affected (0.00 sec)
	mysql> USE world_innodb;
	Database changed
	mysql> SOURCE /tmp/master_backup.sql

### On the slave server, issue the following command
	CHANGE MASTER TO
	-> MASTER_HOST = '10.150.21.227',
	-> MASTER_USER = 'slave',
	-> MASTER_PASSWORD = 'opensaysame',
	-> MASTER_PORT = 3306,
	-> MASTER_LOG_FILE = 'myreplication.000002',
	-> MASTER_LOG_POS = 107,
	-> MASTER_CONNECT_RETRY=10;

### On the slave server, start the slave and then view the slave status.
START SLAVE;
SHOW SLAVE STATUS\G

### On the slave server, view the processes that are running.
SHOW PROCESSLIST\G
How many processes are running? 3
How many processes are handling replication? 2

### On the master server, view the processes that are running.
SHOW PROCESSLIST\G
How many processes are running? 2
How many processes are handling replication? 1

### On the master server, add a record to the City table
	USE world_innodb
	mysql> INSERT INTO City (Name, CountryCode)
	-> VALUES ('Sunland','USA');

### On the master server, view all the records from the City table with an ID greater than 4069.

### On the slave server, view all the records from the City table with an ID greater than 4069.
replicated to the slave server? Yes



































