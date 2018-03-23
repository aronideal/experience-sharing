
# 使用 Apache Shiro Java 安全框架实现

## Apache Shiro 能做的事情

* 验证用户身份信息
* 检查用户是否被分配了安全角色
* 检查用户是否可做某事
* 验证身份、访问控制、会话期间对事件作出反馈

## Apache Shiro 特性

认证（主体访问）、授权（访问控制）、会话管理和密码学

![](http://shiro.apache.org/assets/images/ShiroFeatures.png)

## Apache Shiro 集成

#### 增加 Apache Shiro 配置文件 src/main/resources/shiro.ini

```ini
# =============================================================================
# Apache Shiro INI configuration
#
# Usernames/passwords are based on the classic Mel Brooks' film "Spaceballs" :)
# =============================================================================

# -----------------------------------------------------------------------------
# Users and their (optional) assigned roles
# username = password, role1, role2, ..., roleN
# -----------------------------------------------------------------------------
[users]
root = Hhuhuf32, admin
guest = guest, guest
user1 = nH&@HUdfs, user_role1
user2 = ud3JA#KHFj, user_role1, user_role2

# -----------------------------------------------------------------------------
# Roles with assigned permissions
# roleName = perm1, perm2, ..., permN
# -----------------------------------------------------------------------------
[roles]
admin = *
user_role1 = edit:*
user_role2 = edit:del
```

