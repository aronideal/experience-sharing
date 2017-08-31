# Spring集成持久层的数据源配置

## Apache Commons DBCP
### [http://commons.apache.org/proper/commons-dbcp/download_dbcp.cgi](http://commons.apache.org/proper/commons-dbcp/download_dbcp.cgi)

## Apache Commons DBCP 2
### [http://commons.apache.org/proper/commons-dbcp/download_dbcp.cgi](http://commons.apache.org/proper/commons-dbcp/download_dbcp.cgi)

## C3P0
### [http://www.mchange.com/projects/c3p0/](http://www.mchange.com/projects/c3p0/)

## HikariCP
### [http://brettwooldridge.github.io/HikariCP/](http://brettwooldridge.github.io/HikariCP/)
``` xml
<bean id="dataSource" class="com.zaxxer.hikari.HikariDataSource" destroy-method="close" scope="singleton">
    <property name="driverClassName" value="${jdbc.driverClassName}" />
    <property name="jdbcUrl" value="${jdbc.url}" />
    <property name="username" value="${jdbc.username}" />
    <property name="password" value="${jdbc.password}" />
    
    <!-- 连接只读数据库时配置为true， 保证安全 -->
    <property name="readOnly" value="false" />
    <!-- 等待连接池分配连接的最大时长（毫秒），超过这个时长还没可用的连接则发生SQLException， 缺省:30秒 -->
    <property name="connectionTimeout" value="300000" />
    <!-- 一个连接idle状态的最大时长（毫秒），超时则被释放（retired），缺省:10分钟 -->
    <property name="idleTimeout" value="600000" />
    <!-- 一个连接的生命时长（毫秒），超时而且没被使用则被释放（retired），缺省:30分钟，建议设置比数据库超时时长少30秒，参考MySQL wait_timeout参数（show variables like '%timeout%';） -->
    <property name="maxLifetime" value="1800000" />
    <!-- 连接池中允许的最大连接数。缺省值：10；推荐的公式：((core_count * 2) + effective_spindle_count) -->
    <property name="maximumPoolSize" value="150" />
</bean>
```

## Druid
### [http://druid.io/](http://druid.io/)
``` xml
<bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource" destroy-method="close">
    <property name="driverClassName" value="${jdbc.driverClassName}" />
    <property name="url" value="${jdbc.url}" />
    <property name="username" value="${jdbc.username}" />
    <property name="password" value="${jdbc.password}" />
    <property name="validationQuery" value="SELECT 1" />
    
    <property name="initialSize" value="20" />
    <property name="minIdle" value="20" />
    <property name="maxActive" value="150" />
    <property name="maxWait" value="60000" />
    <property name="testOnReturn" value="true" />
    <property name="testOnBorrow" value="true" />
    <property name="testWhileIdle" value="true" />
    <property name="timeBetweenEvictionRunsMillis" value="300000" />
    <property name="filters" value="stat" /> 
    <property name="proxyFilters">
        <list>
            <ref bean="logFilter" />
        </list>
    </property>
</bean>
```
