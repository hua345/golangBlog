mariadb是mysql的一个分支,主要由开源社区在维护，采用GPL授权许可 MariaDB的目的是完全兼容MySQL，包括API和命令行，使之能轻松成为MySQL的代替品。在存储引擎方面，使用XtraDB（英语：XtraDB）来代替MySQL的InnoDB。
```
#yum install mysql或mariadb后，无法连接数据库
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)
```
```
yum -y install mariadb*
正在安装:
 mariadb-bench              x86_64     1:5.5.44-1.el7_1       updates     385 k
 mariadb-embedded           x86_64     1:5.5.44-1.el7_1       updates     3.6 M
 mariadb-embedded-devel     x86_64     1:5.5.44-1.el7_1       updates     7.4 M
 mariadb-server             x86_64     1:5.5.44-1.el7_1       updates      11 M
 mariadb-test               x86_64     1:5.5.44-1.el7_1       updates     8.0 M
```
### 启动mariadb
```
systemctl start mariadb.service  
#开机自启动
systemctl enable mariadb.service 
```
### 设置root密码 
```
mysql_secure_installation
#连接mysql
mysql -u root -p
```

### ubuntu启动mariadb
```
sudo service mysql start 
Failed to start mysql.service: Unit mysql.service is masked.

sudo rm -r /var/lib/mysql*     # Remove any old database setup
sudo mysql_install_db -u mysql # Install new database
sudo systemctl unmask mysql.service # Emables the service for systemd
sudo service mysql start       # start the service.

#设置新的密码
/usr/bin/mysqladmin -u root password 'new-password'
```

### 参照

- [centos7 安装 mariadb 的正确命令 ](http://blog.csdn.net/default7/article/details/39138139)
- [compiling-mariadb-from-source](https://mariadb.com/kb/en/mariadb/compiling-mariadb-from-source/)
