# 修改apt-get源  
1.阿里源  
>把/etc/apt目录下的sources.list文件先备份，然后用下面的内容替换掉sources.list文件里原有的内容
```
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse

deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse

deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse

deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse

deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse

deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
```
2.清华源  
#默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释  
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial main restricted universe multiverse  
#deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial main restricted universe multiverse  
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-updates main restricted universe multiverse  
#deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-updates main restricted universe multiverse  
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-backports main restricted universe multiverse  
#deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-backports main restricted universe multiverse  
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-security main restricted universe multiverse  
#deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-security main restricted universe multiverse  

#预发布软件源，不建议启用  
#deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-proposed main restricted universe multiverse  
#deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-proposed main restricted universe multiverse  

3.使用sudo apt-get update更新源的链接  

# 使用ppa源安装指定版本的程序  
1.添加ppa源到系统中  (其他程序的PPA可以在https://launchpad.net 中搜索) , 也可以使用add-apt-repository + 程序名搜索  
sudo add-apt-repository ppa:deadsnakes/ppa     （这里是添加python的PPA）  
2.更新源  
sudo apt-get update  
3.安装工具  
sudo apt-get install python3.6 -y  
4.删除ppa源  
在/etc/apt/sources.list.d目录下，找到对应的源的list文件，删除即可  


# 安装pythonx.x对应的pip  
pythonx.x -m pip install --upgrade requests  

# pip安装指定版本的库 
1.更改为国内的pip下载源  
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple  
2.安装库  
pip install 库名==版本号  
比如:  
pip pyclibrary==0.1.4
pip pyserial==3.4
pip PyYAML==5.3
pip robotframework==3.1.2
pip six==1.14.0

