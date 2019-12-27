# 需求
在ubuntu上安装一个FTP服务器，作为windows和其它Linux能够作为匿名用户，无密码登陆，进行文件的上传和下载

# 环境安装
1、服务器端：sudo apt-get install vsftpd

# 环境配置
1、配置文件[/etc/vsftpd.conf](https://github.com/CQ-HC/KylinHome/blob/master/codebase/vsftpd.conf)

# 设置共享目录
## 1、需要根据vsftpd.conf文件中的anon_root字段创建目录，改目录名字可以自己随意定
```bash
sudo mkdir -p /var/ftp
sudo chown ftp /var/ftp #把该目录的 owner 改为 ftp 这个 user
sudo chgrp ftp /var/ftp #把该目录的 group owner 改为 ftp
```

## 2、修改目录权限
1）这个时候匿名登录 ftp 是能够成功的，但是服务器会报错**500 OOPS: vsftpd: refusing to run with writable root inside chroot()**.

2）根据报错信息，我们需要把/var/ftp这个目录的写权限给去掉chmod 755 /var/ftp

3）但是这样用户在/var/ftp目录下就无法上传文件了，解决方法是在/var/ftp目录下再建一个upload文件夹，
把这个文件夹的权限设置为777, 这样匿名用户就可以在upload文件夹下任意的上传、修改、删除文件了。

# 把FTP服务设置为开机自启动
修改/etc/rc.local,加入/etc/rc.d/init.d/vsftpd  start

# python 的ftplib库
[ftplib要点](https://blog.csdn.net/u010005987/article/details/89636420)
