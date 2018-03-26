
# 使用 Apache Shiro Java 安全框架实现

## Apache Shiro 能做的事情

* 验证用户身份信息
* 检查用户是否被分配了安全角色
* 检查用户是否可做某事
* 验证身份、访问控制、会话期间对事件作出反馈

## Apache Shiro 特性

认证（主体访问）、授权（访问控制）、会话管理和密码学

![](http://shiro.apache.org/assets/images/ShiroFeatures.png)

## Apache Shiro 集成（配置方式）

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

## Apache Shiro 集成（非配置方式）

#### 定义密码加密策略（登录、注册公用）

```java
public static String secretLoginPwd(char[] loginPwd, byte[] loginPwdSalt) {
    return new Sha512Hash(loginPwd, loginPwdSalt, 6).toBase64();
}
```

#### 采用自定义登录验证规则，持久层获取用户角色权限数据

```java
public class CustomAuthorizingRealm extends AuthorizingRealm {

    public CustomAuthorizingRealm() {
        HashedCredentialsMatcher credentialsMatcher = new HashedCredentialsMatcher() {
            @Override
            public boolean doCredentialsMatch(AuthenticationToken token, AuthenticationInfo info) {
                UsernamePasswordToken inputToken = (UsernamePasswordToken) token;
                String inputUsername = inputToken.getUsername();
                char[] inputLoginPwd = (char[]) inputToken.getPassword();

                SimpleAuthenticationInfo persistentInfo = (SimpleAuthenticationInfo) info;
                String persistentUsername = persistentInfo.getPrincipals().getPrimaryPrincipal().toString();
                char[] persistentLoginPwd = (char[]) persistentInfo.getCredentials();
                byte[] persistentLoginPwdSalt = persistentInfo.getCredentialsSalt().getBytes();

                if (!(persistentUsername.equalsIgnoreCase(inputUsername) && new String(persistentLoginPwd).equals(secretLoginPwd(inputLoginPwd,
                        persistentLoginPwdSalt)))) {
                    return false;
                }
                return true;
            }
        };
        setCredentialsMatcher(credentialsMatcher);
    }

    @Override
    protected AuthorizationInfo doGetAuthorizationInfo(PrincipalCollection principals) {
        SimpleAuthorizationInfo persistentInfo = new SimpleAuthorizationInfo();

        persistentInfo.addStringPermission("edit:*");// 通过 inputToken 的信息从持久层查询权限信息
        persistentInfo.addStringPermission("edit:del");
        return persistentInfo;
    }

    @Override
    protected AuthenticationInfo doGetAuthenticationInfo(AuthenticationToken token) throws AuthenticationException {
        UsernamePasswordToken inputToken = (UsernamePasswordToken) token;

        String persistentUsername = "user1";// 通过 inputToken 的信息从持久层查询用户信息
        char[] persistentLoginPwd = "NlBd0RncbR1PIRYkpOKAmxZmzN0mqJhapNRLStjCO6UiBEogz351sTtuq60gmYLmdSSAKQfRYmQDhdG3GXmCOg==".toCharArray();
        byte[] persistentLoginPwdSalt = "fjKLJ2klqNfnesmsDF><>EWM".getBytes(Charset.forName("UTF-8"));

        SimpleAuthenticationInfo persistentInfo = new SimpleAuthenticationInfo();
        persistentInfo.setPrincipals(new SimplePrincipalCollection(persistentUsername, "realm1"));
        persistentInfo.setCredentials(persistentLoginPwd);
        persistentInfo.setCredentialsSalt(new SimpleByteSource(persistentLoginPwdSalt));
        return persistentInfo;
    }
}
```

#### 直接实例化 SecurityManager，不从配置读取

```java
DefaultSecurityManager securityManager = new DefaultSecurityManager();
```

