

Centos校园网客户端 Linux版安装教程

查看linux系统版本

```shell
 cat /proc/version
```

1、下载DrClient上传到Centos服务器

2、修改privillege.sh、DrClientLinux权限777

```shell
chmod 777 privillege.sh
chmod 777 DrClientLinux
```

3、执行privillege.sh脚本

4、查找DrClientLinux缺失的动态链接库，并补充完全

```shell
ldd DrClientLinux#查看缺少的动态链接库
yum whatprovides libSM.so.6 #查看缺少的共享库（依据缺少的动态链接库依次查找对应的共享库）
#example：以下都是我缺少的动态链接库
yum install libSM—1.2-2.el7.x86_64 --setopt=protected_multilib=false
yum install libXi-1.7.9-1.el7.i686
yum install libXrender-0.9.10-1.el7.i686
yum install libXrandr-1.5.1-2.el7.i686
yum install libXcursor-1.1.15-1.el7.i686
yum install libXinerama-1.1.3-2.1.el7.i686
yum install freetype-2.8-14.el7_9.1.i686
yum install fontconfig-2.13.0-4.3.el7.i686
```

4、运行DrClientLinux,完成安装

**校园网客户端 Linux版安装教程**

1、 提供32位支持

```shell
sudo -i
dpkg --add-architecture i386
dpkg --add-architecture i386
apt-get install build-essential
apt-get install libgcc1:i386
apt-get install libstdc++6:i386
```

2、查找DrClientLinux缺失的动态链接库，并补充完全

```shell
#文件权限修改
chmod 777 privillege.sh
chmod 777 DrClientLinux
#查看缺少的动态链接库
ldd DrClientLinux
#逐个安装“not found”的动态库文件
#安装过程中，将“=>”左侧字符串中所有字母转换为小写，去掉间的 “.so.”，并加上末尾的数字。然后利用apt  get命令完成安装。
example:
apt-get install libxcursor1:i386
apt-get install libxinerama1:i386
apt-get install libx11.6:i386
apt-get install libz1:i386
apt-get install libxrandr2:i386
#.....
```

4、运行DrClientLinux,完成安装