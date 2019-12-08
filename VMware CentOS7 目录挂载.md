VMware CentOS7 目录挂载
===============

## 首先查看设置的共享文件夹
~~~
[root@localhost mnt]# vmware-hgfsclient
webroot
~~~

## 只使用一次共享文件夹
~~~
[root@localhost mnt]# sudo mount -t fuse.vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other
~~~

## 每次使用都要挂载共享文件夹
#### 编辑 /etc/fstab 文件
~~~
[root@localhost mnt]# vi /etc/fstab
~~~
#### 最后一行添加
~~~
.host:/ /mnt/hgfs fuse.vmhgfs-fuse allow_other 0 0
~~~
