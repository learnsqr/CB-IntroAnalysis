#Configuración máster master
Configurar 2 servidores Máster-Máster para que se actualicen entre ellos.

##Situación previa
Antes de esta práctica cada Máster se ha configurado con un Slave usando máquinas virtuales.  
Se han clonado las máquinas virtuales. La interfície de red se establece en "bridget".

##Ip de servidores master
Mi máster (1): 192.168.30.187 usuari mastermac pwd mastermac   
Otro máster (3): 192.168.30.209 usuari masterjoan pwd masterjoan

##Cambios de configuración

Según las prácticas hechas los dos máster tienen el mismo __server-id__ (1). Por tanto uno de los dos lo cambiamos a __3__ y tendremos __Máster 1__ y __Máster 3__. Cada uno a su vez tiene su __slave__ local con server-id 2 que también se debería actualizar al acabar el ejercicio.

##Usuarios

Creamos usuarios de configuración (simétrico en cada máster)  

###Master 1
mysql> CREATE USER 'masterjoan'@'192.168.30.209' IDENTIFIED BY 'masterjoan';  

Query OK, 0 rows affected (0.05 sec) 

mysql> GRANT REPLICATION SLAVE ON *.* TO 'masterjoan'@'192.168.30.209';

###Master 3
mysql> CREATE USER 'mastermac'@'192.168.30.187' IDENTIFIED BY 'mastermac';  

Query OK, 0 rows affected (0.05 sec) 

mysql> GRANT REPLICATION SLAVE ON *.* TO 'mastermac'@'192.168.30.187';


##Estado inicial de la BD

En uno de los dos masters se clona la BD del otro mediante __mysqldump__.  

##Activación de cada máster como slave
La idea es hacer en cada máster lo mismo que se hizo entre máster-slave.

###En Máster1
mysql> change master to master_host='192.168.30.209', master_user='mastermac', master_password='mastermac', master_port=3306, master_log_file='ON.000001', master_log_pos=107, master_connect_retry=10;  
mysql> start slave;

Los master_log se obtienen del "show master status" del máster 3.

###En Máster3
mysql> change master to master_host='192.168.30.187', master_user='masterjoan', master_password='masterjoan', master_port=3306, master_log_file='xxxxxxxx', master_log_pos=xxxx, master_connect_retry=10;  
mysql> start slave;

Los xxxxxxxx los encontrará en el fichero de dump que se cargó o si se consulta el "show master status;" del servidor máster 1.


##Situación actual
En este momento lo que actualizamos en un máster pasa a otro (PROBADO) y también al slave unido directamente al máster que hace el cambio, pero __no se traspasa al slave del máster contrario__.  

##Paso final
Mirar: https://kura.io/2010/09/04/mysql-master-master-slave-slave-replication/

Solución: hay que añadir al __my.cnf__ de los que hacen de máster el parámetro __log_slave_updates__ !!! Esto hace que el máster replique en su logs binarios las entradas que le provienen del otro máster, con lo que su slave lo podrá leer.

Ahora sí que se arrastra al slave del master "cliente" lo que el otro máster actualiza. ;-)




