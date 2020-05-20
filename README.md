# EAIDK310 本地RPM安装软件的方式
###  一招学会RPM来安装软件

1. 可以通过命令 wget 直接从软件仓库中下载 XXXX.rpm
```
软件仓库地址：
https://download1.rpmfusion.org/
找到对应的软件，注意EAIDK-310是系统是 Fedora28
```
![8977de9050ea789f68443a0a3048743e.png](evernotecid://B0E0E058-55A2-4A8F-8BA6-60CFDEA6A9F4/appyinxiangcom/16257511/ENResource/p1195)

例如
```
下载
wget https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-28.noarch.rpm
```
执行结果如下图
![34499fd5a7f24f5e296fff58db7d7dfd.png](evernotecid://B0E0E058-55A2-4A8F-8BA6-60CFDEA6A9F4/appyinxiangcom/16257511/ENResource/p1193)


2. Fedora 在本地系统中可以直接使用 rpm 工具来安装单个的 .rpm 软件
常用的rpm命令有
```
rpm -ivh    package.rpm      #安装软件包
rpm -Uvh    package.rpm      #升级软件包
rpm -e      package.rpm      #卸载软件包
rpm -qa     package.rpm      #查询已安装软件包的信息
```

例如安装上面下载好的软件
```
 本地安装
 sudo rpm -ivh rpmfusion-free-release-28.noarch.rpm 
 
 查询
 sudo rpm -qa | grep rpmfusion-free-release-28
```
执行结果如下图
![94e694afeb2210f6e445577214dbea66.png](evernotecid://B0E0E058-55A2-4A8F-8BA6-60CFDEA6A9F4/appyinxiangcom/16257511/ENResource/p1194)

3. RPM 卸载
```
sudo rpm -e rpmfusion-free-release-28
```


#### 知识扩展：
```
软件通常都是存放在存储库中，并通过包的形式进行分发。
Red Hat系的，Fedora、CentOS 和其它 Red Hat 家族成员使用的都是 rpm文件（类似windows的 .exe 后缀安装包）。

RPM软件的3种安装方式：
1. yum 安装

YUM是rpm的前端程序，YUM的诞生因rpm软件包形式的管理虽然方便，但仍需要自己解决依赖关系，主要目的是设计用来自动解决rpm的依赖关系， yum仓库用来存放所有的现有的.rpm包，当使用yum安装一个rpm包时，需要依赖关系，会自动在仓库中查找依赖软件并安装。仓库可以是本地的，也可以是HTTP、FTP、nfs形式使用的集中地、统一的网络仓库。
常用的YUM命令
yum info        package     #查看软件包信息
yum install     package     #安装软件
yum remove      package     #卸载软件
yum check-update            #检查是否有可更新的软件包

2. dnf安装
在Fedora中采用一种新的DNF包管理，是新一代的yum，欲以代替yum。DNF包管理器克服了YUM包管理器的一些瓶颈，提升了包括用户体验，内存占用，依赖分析，运行速度等多方面的内容。DNF使用 RPM, libsolv 和 hawkey 库进行包管理操作。在Fedora22中代替了yum。
常用的DNF命令
dnf info        package     #查看软件包信息
dnf install     package     #安装软件
dnf remove      package     #卸载软件
dnf list        installed   #列出所有安装了的 RPM 包


3. rpm安装
rpm 包的管理
一种用于互联网下载包的打包及安装工具，它包含在某些 Linux 分发版中。它生成具有.RPM 扩展名的文件。RPM 是 RedHat Package Manager（RedHat 软件包管理工具）的缩写，类似 windows 的 setup.exe，这一文件格式名称虽然打上了 RedHat 的标志，但理念是通用的。
常用的rpm命令
rpm -ivh    package.rpm      #安装软件包
rpm -Uvh    package.rpm      #升级软件包
rpm -e      package.rpm      #卸载软件包
rpm -qpi    package.rpm      #查询软件包的信息
```
