
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

// 获取当前用户对象
Subject currentUser = SecurityUtils.getSubject();

// 检查是否登录或登录操作
if ( !currentUser.isAuthenticated() ) {
    //collect user principals and credentials in a gui specific manner
    //such as username/password html form, X509 certificate, OpenID, etc.
    //We'll use the username/password example here since it is the most common.
    UsernamePasswordToken token = new UsernamePasswordToken("lonestarr", "vespa");

    //this is all you have to do to support 'remember me' (no config - built in!):
    token.setRememberMe(true);

    currentUser.login(token);
    logger.info("用户 {} 登录成功", currentUser.getPrincipal());
} else {
    logger.info("用户 {} 已登录", currentUser.getPrincipal());
}

// 检查登录用户是否具有某种角色
if (currentUser.hasRole("schwartz")) {
    logger.info("用户 {} 拥有 {} 角色", currentUser.getPrincipal(), "schwartz");
} else {
    logger.info("用户 {} 非 {} 角色", currentUser.getPrincipal(), "schwartz");
}

// 检查登录用户是否具有某种权限
if (currentUser.isPermitted("lightsaber:wield")) {
    logger.info("用户 {} 有 {} 权限 ", currentUser.getPrincipal(), "lightsaber:wield");
} else {
    logger.info("用户 {} 无 {} 权限 ", currentUser.getPrincipal(), "lightsaber:wield");
}

// 注销
currentUser.logout();
logger.info("用户 {} 注销", currentUser.getPrincipal());
```
