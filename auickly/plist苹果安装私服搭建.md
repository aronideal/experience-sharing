
## 通过MAC导出ipa操作

得到ipa和plist

## 配置plist

string修改ipa地址，如：

http://x.x.x.x/.../应用名字.ipa

bundle-identifier就是你申请证书时的名字，格式一般是somebody.app名字

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>items</key>
    <array>
        <dict>
            <key>assets</key>
            <array>
                <dict>
                    <key>kind</key>
                    <string>software-package</string>
                    <key>url</key>
                    <string>请填上你的ipa下载地址(比如:http://127.0.0.1/app.ipa)</string>
                </dict>
            </array>
            <key>metadata</key>
            <dict>
                <key>bundle-identifier</key>
    <string>请填上你的开发者证书用户名</string>
                <key>bundle-version</key>
                <string>1.0</string>
                <key>kind</key>
                <string>software</string>
                <key>title</key>
                <string>请填上标题</string>
            </dict>
        </dict>
    </array>
</dict>
</plist>
```



## 了解plist文件的服务地址

http://x.x.x.x/.../应用名字.plist

## 链接方式

<a title="iPhone" href="itms-services://?action=download-manifest&url=https://dn-你的空间名字.qbox.me/你的Plist存放位置/你的plist名字.plist">
