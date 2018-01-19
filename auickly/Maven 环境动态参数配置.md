
## pom.xml 定义不同环境的配置

```
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
