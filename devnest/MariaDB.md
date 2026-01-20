create user: `create user 'username'@'localhost' identified by 'psw_here';`
login: `mariadb -u username -p`
check curr user: `select current_user();`
run external file: `sudo mariadb -u username -p < file.sql`
grant privileges on:
```sql
grant all privileges on `unwanteddb`.* to 'unwanted'@'localhost';
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
