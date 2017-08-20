
# maven-compiler-plugin
## [http://maven.apache.org/components/plugins/maven-compiler-plugin/](http://maven.apache.org/components/plugins/maven-compiler-plugin/)
``` xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-compiler-plugin</artifactId>
    <configuration>
    <source>1.6</source>
    <target>1.6</target>
    <encoding>${project.build.sourceEncoding}</encoding>
    </configuration>
</plugin>
```

# maven-surefire-plugin
## [http://maven.apache.org/components/surefire/maven-surefire-plugin/](http://maven.apache.org/components/surefire/maven-surefire-plugin/)
``` xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <configuration>
    <skip>true</skip>
    </configuration>
</plugin>
```

# maven-dependency-plugin
## [http://maven.apache.org/components/plugins/maven-dependency-plugin/](http://maven.apache.org/components/plugins/maven-dependency-plugin/)
``` xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-dependency-plugin</artifactId>
    <executions>
        <execution>
            <id>copy</id>
            <phase>package</phase>
            <goals>
                <goal>copy-dependencies</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

# maven-javadoc-plugin
## [http://maven.apache.org/components/plugins/maven-javadoc-plugin/](http://maven.apache.org/components/plugins/maven-javadoc-plugin/)
``` xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-javadoc-plugin</artifactId>
    <configuration>
        <encoding>${project.build.sourceEncoding}</encoding>
        <docfilessubdirs>true</docfilessubdirs>
    </configuration>
    <executions>
        <execution>
            <phase>package</phase>
            <goals>
                <goal>jar</goal>
                <goal>javadoc</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

