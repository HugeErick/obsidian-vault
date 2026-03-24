# Mariadb

create user: `create user 'username'@'localhost' identified by 'psw_here';`
login: `mariadb -u username -p`
check curr user: `select current_user();`
run external file: `sudo mariadb -u username -p < file.sql`
grant privileges on:
```sql
grant all privileges on `unwanteddb`.* to 'unwanted'@'localhost';
grant all privileges on *.* to 'username'@'%';
grant create on *.* to 'unwanted'@'localhost';
flush privileges;
```
make new database: 
```sql
create database db_name
character set utf8mb4
collate utf8mb4_unicode_ci;
```
delete database: `drop database db_name;`
list users: `select User, Host from mysql.user;
clear console: `system clear;`
view structure/description of table: `describe table_name`;
`


## Docker

### Docker MySQL

```bash
sudo docker run -d \
  --name mysql \
  -p 3307:3306 \
  -e MYSQL_ROOT_PASSWORD=root \
  -e MYSQL_ROOT_HOST='%' \
  --restart=unless-stopped \
  mysql:latest \
  --max_allowed_packet=512M \
  --net_read_timeout=3600 \
  --net_write_timeout=3600 \
  --wait_timeout=28800 \
  --interactive_timeout=28800 \
  --max_connections=500 \
  --innodb_buffer_pool_size=1G \
  --innodb_flush_log_at_trx_commit=2 \
  --innodb_lock_wait_timeout=300 \
  --group_concat_max_len=1073741824 \
  --tmp_table_size=256M \
  --max_heap_table_size=256M \
  --bulk_insert_buffer_size=256M \
  --skip-name-resolve \
  --bind-address=0.0.0.0
```

```bash
sudo docker exec -it mysql mysql -uroot -proot --system-command
```

```bash
sudo docker exec -i mysql mysql -uroot -proot test < /path/to/yourfile.sql
```
