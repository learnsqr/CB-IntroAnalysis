# Comandos y Paramaetros para DBA's

## SysConfig

## Comando basicos

1. shell> mysqld start|stop|restart|status
2. shell> mysql_secure_installation
3. shell> mysql_upgrade (actualiza tablas de versiones anteriores de mysql)
4. shell> mysqlcheck (repara tablas) 
5. shell> my_print_defaults mysql client
6. shell> mysql --print-defaults mysql client

## Logs
1. mysql> show binary logs;
2. mysql> show master satus;
3. shell> mysqlbinlog binlog.00001
4. mysql> purge binaryu logs before now();

## Clients
1. mysql> help <option>
2. mysql> tee my_tee_file.sql

## MysqlADMIN

1. mysqladmin -u root -p status variables;
2. mysqladmin -u root -p processlist;
3. mysqladmin -u root -p shutdown;

## Metadata
1. Consultar la cantidad de tipos de columnas definidas en tipo SET
SELECT TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME
-> FROM INFORMATION_SCHEMA.COLUMNS
-> WHERE DATA_TYPE='set';

2. Cuando fue el ultimo create table
   - Cambiar log_output a TABLE
   - Reiniciar el servicio
   - Generarl unos script de creación
   - Consultar la tabla general_log 
   SELECT event_time,argument FROM general_log 
   -> WHERE argument LIKE 'CREATE TABLE%' 
   -> ORDER BY event_time DESC
   -> LIMIT 0,1\G;
   
   SELECT table_schema, table_name, create_time
   -> FROM tables WHERE table_schema 
   -> NOT IN ('information_schema','performance_schema','mysql')
   -> ORDER BY create_time DESC LIMIT 0.100;

## INNODB
1. show engine innodb status;
