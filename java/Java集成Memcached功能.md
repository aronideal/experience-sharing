
# Java 集成 Memcached功能
本文以 Xmemcached 使用为例

## 配置 pom.xml
``` xml
<dependency>
    <groupId>com.googlecode.xmemcached</groupId>
    <artifactId>xmemcached</artifactId>
    <version>2.3.2</version>
</dependency>
```

## 配置 Memcached 参数
新建文件 spring-memcached.xml
``` xml
<?xml version="1.0" encoding="UTF-8"?>

<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:context="http://www.springframework.org/schema/context"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="
	http://www.springframework.org/schema/beans 
	http://www.springframework.org/schema/beans/spring-beans-4.1.xsd
	http://www.springframework.org/schema/context 
	http://www.springframework.org/schema/context/spring-context-4.1.xsd">

	<bean name="memcachedClientBuilder" class="net.rubyeye.xmemcached.XMemcachedClientBuilder"
		scope="singleton">
		<constructor-arg>
			<value>memcached-host:11211</value>
		</constructor-arg>
	</bean>

	<bean id="memcachedClient" factory-bean="memcachedClientBuilder"
		factory-method="build" destroy-method="shutdown" scope="singleton" />

</beans>
```

## Memcached 接口使用
``` java
@Autowired
private MemcachedClient memcachedClient;

Object getObject() {
    // 1，通过Memcached获得value，得到则直接返回
    Object value = memcachedClient.get(key);
    if (value != null) {
        return value;
    }
    // 2，获取value的值，如请求数据库
    //...
    // 3，设置value到Memcached
    memcachedClient.set(key, exp, value);
    return value;
}
```

