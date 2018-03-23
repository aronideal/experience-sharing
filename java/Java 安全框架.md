
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

#### 权限操作

```java
// 初始化本地配置 shiro.ini，构建安全管理器
Factory<SecurityManager> factory = new IniSecurityManagerFactory("classpath:shiro.ini");
SecurityManager securityManager = factory.getInstance();
SecurityUtils.setSecurityManager(securityManager);

// 获取当前用户主体对象
Subject currentUser = SecurityUtils.getSubject();
String username = "";

// 检查是否登录或登录操作
if ( !currentUser.isAuthenticated() ) {
    UsernamePasswordToken token = new UsernamePasswordToken("user1", "nH&@HUdfs");
    
    token.setRememberMe(true);

    currentUser.login(token);
    username = (String) currentUser.getPrincipal();
    logger.info("用户 {} 登录成功", username);
} else {
    logger.info("用户 {} 已登录", username);
}

// 检查登录用户是否具有某种角色
if (currentUser.hasRole("user_role1")) {
    logger.info("用户 {} 有 {} 角色", username, "user_role1");
} else {
    logger.info("用户 {} 无 {} 角色", username, "user_role1");
}

// 检查登录用户是否具有某种权限
if (currentUser.isPermitted("edit:del")) {
    logger.info("用户 {} 有 {} 权限 ", username, "edit:del");
} else {
    logger.info("用户 {} 无 {} 权限 ", username, "edit:del");
}

// 注销
currentUser.logout();
logger.info("用户 {} 注销", username);
```
