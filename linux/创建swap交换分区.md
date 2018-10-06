
设置规则
=======

建议将初始大小和最大值同时设置为你物理内存的1-2倍，

比如

1G设置为2048MB（1G内存是2倍），

2G设置为4096MB（2G内存是2倍），

3G设置为4608MB（3G内存是1.5倍），

4G内存先设置为4096MB（4G的1倍不够在加），

如果你的物理内存小于2G或是2G，建议升级一下你的物理内存（初始大小和最大值设置要一致）；

4G～16G物理内存的系统，至少设置4GB的交换分区

16G～64G物理内存的系统，至少设置8GB的交换分区

64G～256G物理内存的系统，至少设置16GB的交换分区

命令（假如创建2G交换分区）
====

创建2G分区文件

  fallocate -l 2G /swapfile

查看/swapfile状态

ls -lh /swapfile

授权/swapfile只能root查看和写入

chmod 600 /swapfile

通知系统

mkswap /swapfile

swapon /swapfile

free -m

vim /etc/fstab

/swapfile   swap    swap    sw  0   0
