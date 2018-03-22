
## pom.xml 定义不同环境的配置

```xml
<project>
    ...
    <profiles>
        <!-- 开发环境配置 -->
        <profile>
            <id>develop</id>
            <properties>
                <zookeeper.host>192.168.1.2:2181</zookeeper.host>
                <zookeeper.project>/comm/proj0</zookeeper.project>
            </properties>
        </profile>
        <!-- 测试环境配置 -->
        <profile>
            <id>test</id>
            <properties>
                <zookeeper.host>192.168.1.3:2181</zookeeper.host>
                <zookeeper.project>/comm/proj0</zookeeper.project>
            </properties>
        </profile>
    </profiles>
</project>
```

## 定义 resources 资源引用

src/main/resources 里增加配置文件，如 config.properties。

```properties
zookeeper.host=${zookeeper.host}

zookeeper.project=${zookeeper.project}

...
```

## 通过 filtering 配置成动态配置

```xml
<project>
    ...
    <build>
        <resources>
            <resource>
                <!-- 对目录下所有文件过滤，但二进制文件会出问题。 -->
                <directory>src/main/resources</directory>
                <filtering>true<filtering>
            </resource>
            ...
            <resource>
                <!-- 对目录下所有文件过滤，二进制文件不过滤。 -->
                <directory>src/main/resources</directory>
                <includes>
                    <include>a/b/*.properties</include>
                </includes>
                <filtering>true<filtering>
            </resource>
            <resource>
                <!-- 对目录下所有文件过滤，二进制文件不过滤。 -->
                <directory>src/main/resources</directory>
                <excludes>
                    <exclude>a/b/*.properties</exclude>
                </excludes>
                <filtering>false<filtering>
            </resource>
        </resources>
    </build>
</project>
```


