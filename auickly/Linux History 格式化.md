
# Linux History 格式化显示配置

## 添加环境变量
$ sudo vi /etc/profile

	WHO_IP=`who -u am i 2> /dev/null| awk '{print $NF}' | sed -e 's/[()]//g'`
	export HISTTIMEFORMAT="[%F %T]  ${WHO_IP}  `whoami`  "

### 重要参数介绍

%F -> 日期格式，也可使用%Y-%m-%d替代

%T -> 时间格式，也可使用%H:%M:%S替代

`whoami` -> 操作命令使用的登录用户

${USER_IP} -> 顾名思义，执行命令的客户端IP地址

## 使变量生效
$ sudo source /etc/profile

## 测试
$ history
