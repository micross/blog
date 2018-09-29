---
title: "Docker安装MySQL"
date: 2018-08-08T23:30:42+08:00
draft: false
---


```
#启动
docker run --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=mypassword -d mysql

#进入容器
docker exec -it mysql bash

#登录mysql
mysql -u root -p
ALTER USER 'root'@'localhost' IDENTIFIED BY 'mypassword';

#添加远程登录用户
CREATE USER 'remoteuser'@'%' IDENTIFIED WITH mysql_native_password BY 'mypassword';
GRANT ALL PRIVILEGES ON *.* TO 'remoteuser'@'%';
```