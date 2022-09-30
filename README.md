# How to create mariadb in containter docker


- run comand in docker

```sql
# create volume to persist
docker volume create mariadb_data

docker run --name mariadb -d \
  -h mariadb \
  -p 3307:3306 \
  -e MARIADB_ROOT_PASSWORD=Password123! \
  -v ~/mariadb_data:/var/lib/mysql \
  mariadb:latest
```

- Access into mariadb in docker

```shell
docker exec -it mariadb mysql -u root -pPassword123! 

# MariaDB [(none)]> 
```

- Access into mariadb in host

```shell
# in host to port 3307
mysql -u root -pPassword123! -h 127.0.0.1 -P3307 

# MariaDB [(none)]> 
```

___

## into mariadb

- create database

```sql
MariaDB [(none)]> CREATE DATABASE databasename;
```


- import database

```sql
docker exec -i mysql-container mysql -uuser -ppassword name_db < data.sql
```

- show databases

```sql
MariaDB [(none)]> SHOW DATABASES;

+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
```

## Bibliografia

- [mariadb docs](https://mariadb.com/resources/blog/get-started-with-mariadb-using-docker-in-3-steps/)

- [comandos mysql](https://www.w3schools.com/sql/sql_create_db.asp)
