
# Linux History 格式化显示配置

## 添加环境变量
vi /etc/profile

	WHO_IP=`who -u am i 2 > /dev/null| awk '{print $NF}' | sed -e 's/[()]//g'`
	export HISTTIMEFORMAT="[%F %T]  `whoami`  ${WHO_IP}  "

### 重要参数介绍

%F %T -> 时间日期显示格式化，也可使用%Y-%m-%d %H:%M:%S替代

`whoami` -> 操作命令使用的登录用户

${USER_IP} -> 顾名思义，执行命令的客户端IP地址

## 使变量生效
source /etc/profile

## 测试
history
