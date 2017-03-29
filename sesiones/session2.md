# Configuracion del Servidor

# configuraciones "Cascada"

El punto 4 __DEPENDE DEL USUARIO QUE LANZA EL SERVICIO__

1. Lectura principal /etc/my.cnf  
2. /etc/mysql/my.cnf  
3. /usr/mysql/my.cnf  
4. ~/my.cnf (root o mysql)

## Diferentes secciones de configuracion

1.  mysqld
2. client
3. mysql_safeç
4. mysqldump
5. Hay una configuracion para cada programa cliente


## Levartar multiples instancia

1. Copiar datadir
2. Modificar permisos del datadir a mysql:mysql recursivo
3. Usar mysql_safe --socket=/some/path --pid-file=/some/path --datadir=/created/datadir
4. Usar mysql_safe --socket=/var/lib/mysql/mysql2.sock --pid-file=/var/run/mysqld/mysql2.pid --datadir=/var/lib/mysql2 --port=3308 &
5. Usar mysql_safe --socket=/var/lib/mysql/mysql3.sock --pid-file=/var/run/mysqld/mysql3.pid --datadir=/var/lib/mysql3 --port=3310 &



## Logs

1. General Log 
2. Slow query Log
3. Binary Log
4. Error log

## Log Outpyut

1. file
2. table


## Arquitectura de Master/Slave

1. Master
2. Master y un slave
3. Master y varios slaves
4. Master y replicacion de Master






