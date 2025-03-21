---
title: Usando MySQL
published: true
---

### En este tutorial asumimos que el servidor de MySQL está instalado, corriendo y que la cuenta del root ha sido configurada y se conoce el password.

El usuario root (administrador) debe usarse exclusivamente para tareas de administracion, para aprender SQL es necesario configurar un usuario y darle privilegios sobre una base dedatos determinada.

### Iniciando mysql (client)

La forma de iniciar el cliente del MySQL server es atravès del programa cliente llamado *mysql*
es un programa binario escrito en C que se comunica con el servidor de MySQL previamente configurado.
existen otros clientes no oficiales como *PHPMyAdmin* *mysql explorer* que hacen la misma funcion.
En este documento nos centraremos en el cliente standard *mysql* basado en el fork de *mysql* *mariadb* 

1.- Iniciando mysql client con el usuario root, asumimos que mysql esta en el PATH, sino, 
es necesario escribir la ruta completa, Ej. */usr/local/mysql-9.0....* (para Mac M1), en 
mi caso (Linux) ya tengo la ruta agregada.

 ```
  $ mysql -u root -p 

  Enter password:
  Welcome to the MariaDB monitor.  Commands end with ; or \g.
  Your MariaDB connection id is 38
  Server version: 10.11.11-MariaDB-0+deb12u1 Debian 12

  Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

  Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

  MariaDB [(none)]>

 ```

2.- Crear una base de datos.
 
 ```
   MariaDB [(none)]> CREATE DATABASE clientes ;
   Query OK, 1 row affected (0.052 sec)

   MariaDB [(none)]>
  ```
 Puedes usar tambien la sentencia **CREATE DATABASE IF NOT EXISTS clientes** para 
 evitar errores si es que la BD ya existe.

3.- Crea el usuario *isabel* y asigna privilegios a un usuario determinado sobre una base de datos determinada.

 ```
  MariaDB [(none)]> CREATE USER isabel IDENTIFIED by 'Passw123';
  MariaDB [(none)]> GRANT ALL PRIVILEGES ON clientes.* TO 'isabel'@'localhost' IDENTIFIED by 'Passw123';
 ```
 La linea dice: 

 Crea un usuario llamado *isabel* con el password *Passw123*
 Asigna todos los privilegios sobre la base de datos **clientes** y sus tablas al usuario
 isabel identificada con el password Passw123

4.- Probando el nuevo usuario.

 ```
 $ mysql -u isabel -p
  Enter password:  
  Welcome to the MariaDB monitor.  Commands end with ; or \g.
  Your MariaDB connection id is 44
  Server version: 10.11.11-MariaDB-0+deb12u1 Debian 12

  Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

  Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

  MariaDB [(none)]>
  
 ```

5.- Listando las base de datos del usuario *isabel*
 ```
  MariaDB [(none)]> show databases ;
  +--------------------+
  | Database           |
  +--------------------+
  | clientes           |
  | information_schema |
  +--------------------+
  2 rows in set (0.002 sec)

  MariaDB [(none)]>
 ```
 Como puedes notar, la base de datos *clientes* previamente creada y asignada al usuario isabel
 esta asignada correctamente, en este momento el usuario puede hacer operaciones sobre la base de datos
 en cuestion, primeramente, seleccionando la base de datos con la sentencia **USE** de la siguiente manera.

 ```
 MariaDB [(none)]> USE clientes ;
 Database changed
 MariaDB [clientes]>
 ```
**USE** nos permite seleccionar la base de datos para trabajar con ella, si notas, el prompt de MariaDB (mysql) ha cambiado, ahora apunta a la base de datos *cliente* en este momento podemos crear tablas, alterar o actualizar contenido de la base de datos enSQL. 

Una tabla sencilla sería.

```
  MariaDB [clientes]> CREATE TABLE nombres (id INT not null auto_increment, nombre char(80), email char(80), telefono char(10), PRIMARY KEY (id));
  Query OK, 0 rows affected (0.768 sec)
```
 Es buena practica, escribir las sentencias de SQL en mayusculas y los tipos de datos y nombre de tablas en minusculas.

6.- Insertando datos en la tabla *clientes*

```
  MariaDB [clientes]> INSERT INTO nombres (nombre, email, telefono) values ('Isabel Valladolid', 'isa@icloud.com', '8112879087');
  Query OK, 1 row affected (0.107 sec)
```
 Si notas, solo estoy seleccionando los campos *nombre, email y telefono* menos id, dado que este campo usa una sentencia
 especial de mysql llamada **AUTO_INCREMENT** que incrementa su valor en 1, automaticamente con cada registro insertado.

```
  MariaDB [clientes]> SELECT * from nombres ;
  +----+-------------------+----------------+------------+
  | id | nombre            | email          | telefono   |
  +----+-------------------+----------------+------------+
  |  1 | Isabel Valladolid | isa@icloud.com | 8112879087 |
  +----+-------------------+----------------+------------+
  1 row in set (0.001 sec)
```

 La  instruccion **SELECT** ejecuta una consulta a la base de datos via la tabla nombres y despliega todo el contenido.

7.- Actualizando **UPDATE** registros en la base de datos.

 ```
 MariaDB [clientes]> UPDATE nombres SET telefono=9996789030 WHERE id=1;
 Query OK, 1 row affected (0.057 sec)
 Rows matched: 1  Changed: 1  Warnings: 0

 MariaDB [clientes]>

```

La consulta (query) hace lo siguiente: 
Actualiza el registro con id=1 y sustituye el campo telefono por un numero nuevo. 
El resultado fue, Query OK y 1 renglon afectado, 0 warnings (alertas)


Continua....



 


