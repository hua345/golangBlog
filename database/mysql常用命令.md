### 连接数据库
```
mysql -u root -p
```
###数据库操作
```js
//查看所有数据库
SHOW DATABASES
//创建数据库
CREATE DATABASES mydb;
//删除数据库
DROP DATABASES mydb;
//选择数据库
USE mydb;
```
### 表操作
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
#### CURD
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
### 备份数据库
```
//备份整个数据库
mysqldump -u user_name -p database_name > outfile_name.sql
mysqldump -u root -p mydb > ~/mydb.bk.sql
//备份一个表
mysqldump -u user_name -p database_name table_name > ~/outfile_name.sql
```

参考:
[Mysql命令大全](http://www.cnblogs.com/zhangzhu/archive/2013/07/04/3172486.html)
