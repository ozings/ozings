mysql授权以及权限管理
===============

## 创建用户

~~~
create user '用户名'@'IP地址' identified by '密码';    # 语法
create user '用户名'@'localhost' identified by '密码';   # 本地可用账号
create user '用户名'@'192.168.12.1' identified by '密码'; # 具体哪个ip可用账号
create user '用户名'@'192.168.12.%' identified by '密码'; # 具体哪个网段可用账号
create user '用户名'@'%' identified by '密码';      # 所有ip都可用账号
~~~

## 删除用户

~~~
drop user '用户名'@'IP地址';
~~~

## 修改用户

~~~
rename user '用户名'@'IP地址' to '新用户名'@'IP地址';
~~~

## 修改密码

~~~
set password for '用户名'@'IP地址' = password('新密码');
~~~

## 授权

~~~
grant 权限 on 数据库.表 to '用户'@'IP地址'    # 授权语法

grant select on db1.* to 'zekai'@'%';   # db1下所有表授予select权限
grant select on *.* to 'zekai'@'%';     # 所有数据库都授予select权限
grant select,insert on *.* to 'zekai'@'%';  # 授予多个权限
grant all privileges on *.* to 'zekai'@'%';            # 授予全部权限，除了创建用户
~~~

## 创建与授权联合使用

~~~
grant all privileges on *.* to "账号名"@"%" identified by "密码" with grant option;
~~~

注意：

> 每次授权完之后，一定要刷新授权

~~~
flush privileges;
~~~
