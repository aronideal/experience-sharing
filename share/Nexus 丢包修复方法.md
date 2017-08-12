
<<Nexus 丢包修复方法 >>

一、根据目录结构创建一系列目录，如

/com/xxx/conf/red_cli/0.0.5-SNAPSHOT

二、即 /com/xxx/conf 、 red_cli 、 0.0.5-SNAPSHOT 分别是以下部分的内容：


    com.xxx.conf
    red_cli
    0.0.5-SNAPSHOT


三、在 /com/xxx/conf/red_cli 下放置 maven-metadata.xml / maven-metadata.xml.md5 / maven-metadata.xml.sha1 三个文件

修改maven-metadata.xml的内容与实际的相符，lastUpdated在用户端仓库找

四、在 /com/xxx/conf/red_cli/0.0.5-SNAPSHOT 下放置 maven-metadata.xml / maven-metadata.xml.md5 / maven-metadata.xml.sha1 三个文件

注意，maven-metadata.xml.md5和maven-metadata.xml.sha1拷贝过来，maven-metadata.xml是将用户端仓库重命名maven-metadata-nexus.xml得到的文件

五、将用户端仓库的 .jar / .jar.md5 / .jar.sha1 / .pom / .pom.md5 / .pom.sha1 拷贝到 /com/xxx/conf/red_cli/0.0.5-SNAPSHOT 下

六、将 /com/xxx/conf/red_cli/0.0.5-SNAPSHOT 保持结构不变完整拷贝到nexus服务器的 .../sonatype-work/nexus/storage/ 对应的仓库里

搞定。