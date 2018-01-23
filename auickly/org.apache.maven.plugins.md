
# maven-checkstyle-plugin
## [http://maven.apache.org/components/plugins/maven-checkstyle-plugin/](http://maven.apache.org/components/plugins/maven-checkstyle-plugin/)
```xml
<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE module PUBLIC
  "-//Puppy Crawl//DTD Check Configuration 1.3//EN"
  "http://www.puppycrawl.com/dtds/configuration_1_3.dtd">

<module name="Checker">

    <property name="localeLanguage" value="zh_CN" />

    <property name="charset" value="UTF-8" />

    <module name="FileTabCharacter" />

    <module name="RegexpSingleline">
        <property name="format" value="System\.out\.println" />
        <property name="message" value="代码中发现 System.out.println，去掉或改成日志打印。" />
    </module>

    <module name="RegexpSingleline">
        <property name="format" value="System\.err\.println" />
        <property name="message" value="代码中发现 System.err.println，去掉或改成日志打印。" />
    </module>

    <module name="FileLength">
        <property name="max" value="3500" />
        <property name="fileExtensions" value="java" />
    </module>

    <module name="TreeWalker">

        <module name="UnusedImports">
            <property name="processJavadoc" value="true" />
        </module>
        <module name="RedundantImport" />

        <module name="EqualsHashCode" />

        <module name="LineLength">
            <property name="max" value="160" />
        </module>

        <module name="FinalParameters" />

<!--         <module name="JavadocType"> -->
<!--             <property name="allowUnknownTags" value="true" /> -->
<!--             <message key="javadoc.missing" value="类注释：缺少Javadoc注释。" /> -->
<!--         </module> -->

<!--         <module name="JavadocMethod"> -->
<!--             <property name="tokens" value="METHOD_DEF" /> -->
<!--             <property name="allowMissingPropertyJavadoc" value="false" /> -->
<!--             <message key="javadoc.missing" value="方法注释：缺少Javadoc注释。" /> -->
<!--         </module> -->

        <module name="RedundantThrows" />

        <module name="SuperClone" />

        <module name="ParameterAssignment" />
    </module>
</module>
```

``` xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-checkstyle-plugin</artifactId>
    <version>2.15</version>
    <configuration>
        <configLocation>checkstyle/checks.xml</configLocation>
        <encoding>UTF-8</encoding>
        <consoleOutput>true</consoleOutput>
        <failsOnError>true</failsOnError>
        <includeTestSourceDirectory>false</includeTestSourceDirectory>
    </configuration>
    <executions>
        <execution>
            <id>verify</id>
            <phase>package</phase>
            <configuration>
                <failOnViolation>true</failOnViolation>
            </configuration>
            <goals>
                <goal>check</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

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

# maven-dependency-plugin
## [http://maven.apache.org/components/plugins/maven-dependency-plugin/](http://maven.apache.org/components/plugins/maven-dependency-plugin/)
``` xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-dependency-plugin</artifactId>
    <!--
    <configuration>
        <outputDirectory>${project.build.directory}/dependency</outputDirectory>
    </configuration>
    -->
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

# maven-jar-plugin
## [http://maven.apache.org/components/plugins/maven-jar-plugin/](http://maven.apache.org/components/plugins/maven-jar-plugin/)
``` xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-jar-plugin</artifactId>
    <configuration>
        <archive>
            <manifest>
                <!-- 是否在Manifest文件里增加Class-Path -->
                <addClasspath>true</addClasspath>
                <!-- Manifest文件里Class-Path项前增加的路径 -->
                <classpathPrefix>lib/</classpathPrefix>
                <mainClass>fully.qualified.MainClass</mainClass>
                <addDefaultImplementationEntries>true</addDefaultImplementationEntries>
                <addDefaultSpecificationEntries>true</addDefaultSpecificationEntries>
            </manifest>
        </archive>
    </configuration>
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

# maven-source-plugin
## [http://maven.apache.org/plugins/maven-source-plugin/](http://maven.apache.org/plugins/maven-source-plugin/)
``` xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-source-plugin</artifactId>
    <executions>
    	<execution>
    	    <id>attach-sources</id>
    	    <phase>package</phase>
    	    <goals>
    	        <goal>jar-no-fork</goal>
    	    </goals>
    	</execution>
    </executions>
    <configuration>
        <!-- Manifest文件是否使用与dist版本一致 -->
        <useDefaultManifestFile>true</useDefaultManifestFile>
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
