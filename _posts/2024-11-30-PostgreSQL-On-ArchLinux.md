# Instalando y e iniciando PostgreSQL en Arch Linux

### 1.- Instalar PostgreSQL via pacman.

```
 sudo pacman -S postgresql 

```

### 2.- Ingresar como administrador de PotgreSQL e iniciar el motor de base de datos

```
  $ sudo su - postgres
   [sudo] password for ficovh:

   [postgres@devel ~]$ initdb -D /var/lib/postgres/data
```
### 3.- configurar el servicio de PostgreSQL para iniciar automaticamente.

```
	$ sudo systemctl enable postgresql
	$ sudo systemctl start  postgresql
```

```
  $ sudo su - postgres
   [sudo] password for ficovh:

  [postgres@devel ~]$ psql
  psql (16.3)
  Type "help" for help.
```

### 4.- Tareas de administracion, creacion de base de datos, roles, schema (>15)
```

 postgres=# create database customers ;
 CREATE DATABASE
 postgres=# \c customers ;
 You are now connected to database "customers" as user "postgres".
 customers=# create schema admindb authorization admindb ;
 CREATE SCHEMA
 customers=# \q
 [postgres@devel ~]$ exit
 logout
```

### Creando tablas en la base de datos customers y el usuario admindb

```
 $ psql -U admindb customers
 psql (16.3)
 Type "help" for help.

 customers=> create table nombres (id serial, nombre varchar(30), email varchar(80));
 CREATE TABLE

 customers=> \d nombres;
                                   Table "admindb.nombres"
 Column |         Type          | Collation | Nullable |               Default
--------+-----------------------+-----------+----------+-------------------------------------
 id     | integer               |           | not null | nextval('nombres_id_seq'::regclass)
 nombre | character varying(80) |           |          |
 email  | character varying(80) |           |          |
  
```

### Referencias.

* [Learn PostgreSQL - Ferrari](https://www.packtpub.com/en-us/product/learn-postgresql-9781838985288)
* [Sitio oficial de PostgreSQL](https://www.postgresql.org)

