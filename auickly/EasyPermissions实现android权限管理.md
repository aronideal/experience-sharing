
## 通过 EasyPermissions 实现Android权限管理

#### 添加 EasyPermissions 工具包引用

```
dependencies {
    implementation 'pub.devrel:easypermissions:1.1.1'
}
```

#### 以更新app功能为例，定义请求码和需求权限

```java
private static final int PERMISSION_UPGRADEAPP_REQUESTCODE = 1;
private static final String[] PERMISSION_UPGRADEAPP_USES = {
Manifest.permission.READ_EXTERNAL_STORAGE, 
Manifest.permission.WRITE_EXTERNAL_STORAGE, 
Manifest.permission.INTERNET, 
Manifest.permission.REQUEST_INSTALL_PACKAGES
};
```

#### 定义权限请求回调，传递权限申请给 EasyPermissions 工具包

```java
@Override
public void onRequestPermissionsResult(int requestCode, @NonNull String[] permissions, @NonNull int[] grantResults) {
    super.onRequestPermissionsResult(requestCode, permissions, grantResults);

    EasyPermissions.onRequestPermissionsResult(requestCode, permissions, grantResults, this);
}
```

#### 定义 EasyPermissions 工具包回调，前提是需要实现 EasyPermissions 提供的 EasyPermissions.PermissionCallbacks 接口

```java
@Override
public void onPermissionsGranted(int requestCode, @NonNull List<String> perms) {
}

@Override
public void onPermissionsDenied(int requestCode, @NonNull List<String> perms) {
    if (PERMISSION_UPGRADEAPP_REQUESTCODE == requestCode) {
        if (EasyPermissions.somePermissionPermanentlyDenied(this, perms)) {
            new AppSettingsDialog.Builder(this)
                        .setTitle("必需的权限")
                        .setRationale("检查新版本需要访问您的SD权限。接受后将进入系统设置，请修改SD权限为可用。")
                        .setPositiveButton("接受")
                        .setNegativeButton("拒绝")
                        .build().show();
        }
    }
}
```

#### 定义授权后业务逻辑部分，@AfterPermissionGranted 的参数对应请求码，用户全部接受后才能进入这里

```java
@AfterPermissionGranted(PERMISSION_UPGRADEAPP_REQUESTCODE)
private void permissionUpgradeApp() {
    AppUtils.upgradeLatestApp(this, true, LOG_TAG);
}
```

#### 判断并调用业务逻辑，已有权限直接调用业务代码。否则，申请权限

```java
if (EasyPermissions.hasPermissions(this, PERMISSION_UPGRADEAPP_USES)) {
    permissionUpgradeApp();
} else {
    ActivityCompat.requestPermissions(this, PERMISSION_UPGRADEAPP_USES, PERMISSION_UPGRADEAPP_REQUESTCODE);
}
```

