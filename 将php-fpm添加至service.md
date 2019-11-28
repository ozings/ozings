## 编辑 php-fpm.conf 文件
~~~
[root@localhost /]# vi /usr/local/php/etc/php-fpm.conf
~~~

#### 将 ;pid = run/php-fpm.pid  前面的分号去掉
~~~
pid = run/php-fpm.pid
~~~

## 重启php-fpm
~~~
[root@localhost /]# ps aux | grep php-fpm
[root@localhost /]# kill -9 pid
[root@localhost /]# cd /usr/local/php/sbin/
[root@localhost /]# ./php-fpm
~~~

### 进入php源码包目录 sapi/fpm
~~~
[root@localhost /]# cd /root/php-7.2.25/sapi/fpm
~~~

### 将 init.d.php-fpm 文件复制到 /etc/init.d 目录下并改名为 php-fpm
~~~
[root@localhost fpm]# cp init.d.php-fpm /etc/init.d/php-fpm
~~~

## 赋予脚本可执行命令，添加开机自启动
~~~
[root@localhost fpm]# chmod +x /etc/init.d/php-fpm
[root@localhost fpm]# chkconfig --add php-fpm
[root@localhost fpm]# chkconfig php-fpm on
~~~

## php-fpm service 相关命令

#### 启动
~~~
[root@localhost /]# service php-fpm start
~~~
#### 关闭
~~~
[root@localhost /]# service php-fpm stop
~~~

#### 重启
~~~
[root@localhost /]# service php-fpm restart
~~~
