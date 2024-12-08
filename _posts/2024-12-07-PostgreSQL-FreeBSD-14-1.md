# PostgreSQL en FreeBSD 14.1

### Actualizando paquetes e instalando PostgreSQL 17 server

 ```
  $ doas pkg update
  $ doas pkg install postgresql17-server
 ```

### Cargando el servicio de PostgreSQL automaticamente
 
  ```
   $ doas sysrc postgresql_enable=yes
  ```

### Iniciando el cluster de PostgreSQL
 

 ```
  $ doas service postgresql initdb 
 ```

### Labores de administracion inicial.

 ```
  $ doas su - postgres
  $ psql
  psql (17.2)
  Type "help" for help.

  postgres=#
```
### Tareas de administracion, creacion de base de datos, roles, schema (>15)

```
  $ doas su - postgres
  Password:
  $ psql 
  psql (17.2)
  Type "help" for help.

  postgres=# CREATE DATABASE customers ;
  CREATE DATABASE
  postgres=# \c customers;
  You are now connected to database "customers" as user "postgres".
  customers=# create schema admindb authorization admindb ;
  ERROR:  role "admindb" does not exist
  customers=# CREATE ROLE admindb ;
  CREATE ROLE
  postgres=# ALTER ROLE admindb LOGIN ;
  ALTER ROLE
  customers=# create schema admindb authorization admindb ;
  CREATE SCHEMA
  customers=# \q
  $ exit

```
### Accediendo a la base de datos customers con el usuario admindb

```
  user@freebsd14-server:~ $ psql -U admindb customers
  psql (17.2)
  Type "help" for help.

  customers=> 
 ```
