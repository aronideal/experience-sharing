# Java代码混淆

在pom.xml添加插件[proguard-maven-plugin](https://github.com/wvengen/proguard-maven-plugin)，自定义部分改成你自己的代码过滤。其它部分按需修改，满足需要。

``` xml
<plugin>
	<groupId>com.github.wvengen</groupId>
	<artifactId>proguard-maven-plugin</artifactId>
	<version>2.0.13</version>
	<executions>
		<execution>
			<phase>package</phase>
			<goals>
				<goal>proguard</goal>
			</goals>
		</execution>
	</executions>
	<configuration>
		<injar>${project.build.finalName}.jar</injar>
		<outjar>${project.build.finalName}-proguard.jar</outjar>
		<obfuscate>true</obfuscate>
		<options>
			<option>-ignorewarnings</option>
			<option>-dontshrink</option>
			<option>-dontnote </option>
			<!-- java.** -->
			<option>-dontwarn java.**</option>
			<option>-keep class java.** { *;}</option>
			<!-- com.sun.** -->
			<option>-dontwarn com.sun.**</option>
			<option>-keep class com.sun.** { *;}</option>
			<!-- javax.** -->
			<option>-dontwarn javax.**</option>
			<option>-keep class javax.** { *;}</option>
			<!-- org.bouncycastle.** -->
			<option>-dontwarn org.bouncycastle.**</option>
			<option>-keep class org.bouncycastle.** { *;}</option>
			<!-- 自定义的 -->
			<option>-keep class com.xxx.toolkit.SignedVerify { *;}</option>
			<option>-keep class com.xxx.toolkit.pojo.VerifyResponse { *;}</option>
		</options>
		<libs>
			<lib>${java.home}/lib/rt.jar</lib>
			<lib>${java.home}/lib/jce.jar</lib>
		</libs>
	</configuration>
</plugin>
```
