裸机篇
****************

4.1  Ubuntu 和 Windows 文件互传
1、==ubuntu下安装ftp ====
sudo apt-get install vsftpd
sudo vi /etc/vsftpd.conf
local_enable=YES
write_enable=YES
sync
sudo /etc/init.d/vsftpd restart   //重启ftp服务
2、Windows 下 FTP 客户端安装
Windows 下 FTP 客户端我们使用 FileZilla


4.2 Ubuntu 下 NFS 和 SSH 服务开启
1、NFS
sudo apt-get install nfs-kernel-server rpcbind
sudo vi /etc/exports
/home/zuozhongkai/linux/nfs *(rw,sync,no_root_squash)     //最后一行添加自己的路径
sudo /etc/init.d/nfs-kernel-server restart                //重启NFS服务
2、SSH
sudo apt-get install openssh-server

win下CH340驱动安装，安装前，先链接开发板

4.3 Ubuntu 交叉编译工具链安装
1、 交叉编译器安装
Linaro GCC 编译器下载地址如下
I.MX6U-ALPHA 开发板是一个 Cortex-A7 内核的开发板，因此选择 arm-linux-gnueabihf，点击后面的“Binaries”
文件夹位置//D:\正点原子\IMX6ULL\【正点原子】A盘 -基础资料\05、开发工具\01、交叉编译器
gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf.tar.xz
拷贝至Ubuntu位置
cp gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf.tar.xz  /usr/local/arm/ -f
tar -xvf gcc*
sudo vi /etc/profile
export PATH=$PATH:/usr/local/arm/gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf/bin
2、安装相关库
sudo apt-get install lsb-core lib32stdc++6
3、交叉编译器验证
arm-linux-gnueabihf-gcc -v
的版本号为 4.9.4

如有问题则查看确认是否删除原先的gcc :
rm /usr/bin/arm-linux-gnueabihf-gcc //修复，使用不正确的gcc，删除原先的
============================================================================
