
# 同步服务器系统时间

## 安装软件
$ sudo yum install -y ntpdate

## 同步时间
$ sudo ntpdate 202.120.2.101

# 可用的NTP服务器地址列表
ntp.sjtu.edu.cn 202.120.2.101 （上海交通大学网络中心NTP服务器地址）

	温馨提醒：由于网络原因，可能同步失败，出现 no server suitable for synchronization found 错误。遇到此问题，建议多尝试几次。
