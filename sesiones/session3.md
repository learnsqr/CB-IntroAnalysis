# MASTER - SLAVE

# Servidor Master 

## MASTER

### My.cnf

1. server-id = Diferente en entorno  
2. log-bin = nombreDelLog  
3. bin-log-format = mixed  
4. innodb configuration activada  

### Reiniciar el servicio

### Cliente MySQL

1. Crear un usuario con acceso desde la IP del slave
2. Grant REPLICATION SLAVE para el usario anterior
3. Generar copia de la base de datos y copiarla al SLAVE (master-data activo si hay binary log)
4. Show master status; para obtener el log-bin (nombre y posicion)


## SLAVE

### My.cnf

1. Server-id = Diferente en entorno
2. Desactivar Bin-log
3. Desactivar bin-log-format
4. Activar configuraciones innoDB

### Reinicial el servicio

### Cliente MySQL

  CHANGE MASTER TO
  MASTER_HOST = '10.150.21.227',
  MASTER_USER = 'slave',
  MASTER_PASSWORD = 'opensaysame',
  MASTER_PORT = 3306,
  MASTER_LOG_FILE = 'myreplication.000002',
  MASTER_LOG_POS = 107,
  MASTER_CONNECT_RETRY=10;
  
1. Cambiar HOST
2. Cambiar USER por el creado en el MASTER
3. Cambiar PASSWORD por el creado en el MASTER
4. Cambiar PORT pr el port del MASTER
5. Cambiar LOG_FILE segun master
6. Cambiar LOG_POS segun master
7. START SLAVE
8. Monitorizar con Show slave status;
9. Para detener el slave usar STOP SLAVE

## Insertar datos en el MASTER

1. Insertar datos en el MASTER
2. Ver datos en el MASTER
3. Ver datos en el SLAVE




  




