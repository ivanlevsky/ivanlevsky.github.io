## mariadb(mysql)  

##### create user and set privilege  
```sql
CREATE USER 'username'@'host' IDENTIFIED BY 'password';
GRANT privileges ON databasename.tablename TO 'username'@'host' FLUSH PRIVILEGES;
```  
##### examples  
```sql
CREATE USER 'debianmysql1'@'%' IDENTIFIED BY 'debianmysqlpasswd1';
CREATE USER 'debianmysql2'@'localhost' IDENTIFIED BY 'debianmysqlpasswd2';
CREATE USER 'debianmysql3'@'192.168.129.222' IDENTIFIED BY 'debianmysqlpasswd3';
GRANT ALL ON *.* TO 'debianmysql'@'%';
GRANT SELECT,INSERT ON *.* TO 'debianmysql'@'%';
```
##### error
ERROR 1396 (HY000) Operation CREATE USER failed for 'debianmysql'@'%'
```sql
FLUSH PRIVILEGES;
```
jdbc connect error: Connection refused: connect
```shell
use root
cd /etc/mysql/mariadb.conf.d
vi 50-server.cnf

#comment line 
#bind-address            =127.0.0.1"

#add line
bind-address            =0.0.0.0
```

## postgresql  

##### start server   
```shell
pg_ctlcluster 11 main start
```
##### change password   
```shell
sudo -u postgres psql
ALTER USER postgres PASSWORD 'postgres';
```
##### search config file   
```shell 
sudo -u postgres psql -c 'SHOW config_file'
sudo more /etc/postgresql/11/main/pg_hba.conf
```
##### remote access
```shell
vi /etc/postgresql/11/main/postgresql.conf
#add `set listen_addresses = '*'`
vi /etc/postgresql/11/main/pg_hba.conf
#add lines below
host    all             all              0.0.0.0/0                       md5
host    all             all              ::/0                            md5
#restart pgsql service
sudo systemctl restart postgresql
```
##### connect database  
```shell
psql -h host -p port -U username -d databasename
psql postgresql://username:password@myhost:port/databasename
```
##### create database use default template  
```sql
create database pgtest with template template1;
```
##### pgsql shell command  
```shell
#search postgres help
\h
#search psql command
\?
#check user privilege
\du
```
##### pgsql create user and set privilege
```sql
--create user
CREATE USER username WITH PASSWORD 'password';
--user priviege:
grant all privileges on database database_name to user;
grant all privileges on all tables in schema public to user;
```

##### mysql command in postgresql
  
mariadb(mysql) | postgresql
---|---
show databases|`\l` or `select * from pg_database`
use mysql|`\c database_name`
show tables|`\d` or `\dt` or `select table_name from information_schema.tables where table_schema = 'public';`
use mysql|`\d table_name` or `select column_name,data_type from information_schema.columns where table_name = 'table_name';`


