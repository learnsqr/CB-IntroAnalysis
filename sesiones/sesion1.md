# Introducción a MySQL

## Repaso MySQL  

### Ejercicio 1.
Crear un fichero .sql que cree tres tablas: usuarios (id, user, name, email, password), proyectos(id, name, descripcion), users_con_proyectos ( idUser, idProject)

1. Nameing convention  
1.0. __TODO EN INGLES__  
1.1. snake_case  
1.2. tablas en plural  
1.3. atributos en singular  
1.4. minusculas  
1.5. palabras reservadas en MAYUSCULAS  
1.6. tipos de datos (varchar, INT, text, blob)
1.7. tratamiento de password  
1.8. utf-8 y ordenamiento  
1.9. desambiaguación de id's (por nombre)  
1.10. UNIQUE para índices  
1.11. Tamaño de visualización de INT  
1.12. id vs. uid (INT vs. varchar)  
1.13. Ventajas de INNODB (transaccional, integridad referencial, bloqueo a nivel de fila, backup incremental) 

## Instalación de MySQL SERVER y CLIENT
(segun script)

1. mysql (funciona sin usuario y sin password)  
2. crear usuario user1 en localhost con password 1234  
3. dar acceso a user1 a la DB test (GRANT...)
4. Asegurar el servidor (/usr/bin/mysql_secure_installation)
5. acceso desde consola a mysql (.bash_history)
6. inicio, reinicio y parada del server (/etc/init.d/mysqld)
7. show status
8. show variables
9. SET GLOBAL slow_query_log
10. localizacion de archivo de configuracion (my.cnf) para verlo usar mysqladmin (como root)
11. persistencia de variable global (agregar al grupo del .ini)

## Estructura de directorio DATADIR
1. Para MYISAM son tres ficheros (estructura, indices, datos)
2. Para INNODB es ibdata y sus binary logs.
3. INFORMATION_SCHEMA es una vista

## Backup
1. mysqldump usarlo con MYISAM
2. mysql-hotcopy uasarlo con INNODB
