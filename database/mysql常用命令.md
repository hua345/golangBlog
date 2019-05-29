### 1.连接数据库
```
mysql -u root -p
```
### 2. 数据库操作
```js
//查看所有数据库
SHOW DATABASES;
//创建数据库
CREATE DATABASE db_example;
//删除数据库
DROP DATABASE db_example;
//选择数据库
USE db_example;
```
## 3. 数据库用户
#### 3.1 新建新的数据库用户
```
# 创建名为`springuser`用户，密码为`123456`，'%'表示允许远程登陆
CREATE USER 'springuser'@'%' IDENTIFIED BY '123456';
# 修改密码
set password for 'springuser'@'%' = password('123456');
```

#### 3.2 授权用户
```
# 将数据库`db_example`下的所有权限授权给用户`springuser`
GRANT ALL PRIVILEGES ON db_example.* TO 'springuser'@'%';

# select,delete,update,create,drop
# 将数据库`db_example`下的部分权限授权给用户`springuser`
GRANT SELECT,UPDATE, INSERT PRIVILEGES ON db_example.* TO 'springuser'@'%';
```

#### 3.3 刷新权限表
```
flush privileges;
```
需要将新加入的用户写入到权限表中，即更新`grant table`
#### 3.4 查看数据库用户信息
```
MariaDB [(none)]> select host,user,password from mysql.user;
+-----------+------------+-------------------------------------------+
| host      | user       | password                                  |
+-----------+------------+-------------------------------------------+
| localhost | root       | *A6C46E51594E7F8C9D1A310002577ADCA7E6B2A0 |
| docker01  | root       | *A6C46E51594E7F8C9D1A310002577ADCA7E6B2A0 |
| 127.0.0.1 | root       | *A6C46E51594E7F8C9D1A310002577ADCA7E6B2A0 |
| ::1       | root       | *A6C46E51594E7F8C9D1A310002577ADCA7E6B2A0 |
| %         | springuser | *6BB4837EB74329105EE4568DDA7DC67ED2CA2AD9 |
+-----------+------------+-------------------------------------------+
5 rows in set (0.00 sec)
```
### 3.表操作
```
//查看数据库所有表
show tables
//创建数据库表
create TABLE Books (
bookId int not null primary key auto_increment,
bookName varchar(20) not null,
bookDate timestamp default current_timestamp()
);
//显示表的结构
describe Books;
//删除表
drop table Books;
//清空表
delete from Books;
```
#### 4. CURD
```
//create
insert into Books (bookName) values("Primer C++"),("深入浅出Nodejs");
//update
update Books set bookName='Primer C++ 5th' where bookName="Primer C++";
//read
select * from Books where bookId <= 10  order by bookDate asc;
//delete
delete from Books where bookName='Primer C++ 5th';
```
### 5. 备份数据库
```
//备份整个数据库
mysqldump -u user_name -p database_name > outfile_name.sql
mysqldump -u root -p mydb > ~/mydb.bk.sql
//备份一个表
mysqldump -u user_name -p database_name table_name > ~/outfile_name.sql
```

参考:
[Mysql命令大全](http://www.cnblogs.com/zhangzhu/archive/2013/07/04/3172486.html)
