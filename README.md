# YuGer26.github.io

0.虚拟机-》设置-》选项-》客户机隔离-》取消勾选启用拖放
1.解锁自适应屏幕

sudo cp /etc/vmware-tools/tools.conf.example /etc/vmware-tools/tools.conf
sudo nano /etc/vmware-tools/tools.conf

[resolutionKMS]
# Default is true if tools finds an xf86-video-vmware driver with*
# version >= 13.2.0. If you don't have X installed, set this to true manually.
# This only affects tools for Linux.
enable=true

systemctl restart vmtoolsd.service

2.安装 vm tools  挂载ISO 路径在vmwarm安装根目录里的 linux.iso  复制出压缩包 VMwareTools-10.3.22-15902021.tar.gz至 桌面解压 
sudo ./vmware-install.pl 全程回车

3.sudo yum update

4.挂载硬盘
虚拟机-》设置-》选项-》共享文件夹-》总是启用
vmware-hgfsclient 
Desktop
work
cd /mnt/hgfs/
sudo mkdir Desktop
sudo chmod -R 777 Desktop/
vmhgfs-fuse  .host:/Desktop  /mnt/hgfs/Desktop/
sudo mkdir work
sudo chmod -R 777 work/
vmhgfs-fuse  .host:/work  /mnt/hgfs/work/
sudo nano /etc/fstab
.host:/Desktop /mnt/hgfs/Desktop fuse.vmhgfs-fuse allow_other 0 0
.host:/work /mnt/hgfs/work fuse.vmhgfs-fuse allow_other 0 0
