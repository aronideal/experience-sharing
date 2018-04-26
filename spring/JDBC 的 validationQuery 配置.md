
## 连接池类型与参数的对应关系

The Tomcat JDBC Connection Pool	 -  validationQuery

Apache Commons DBCP Connection Pool  -  validationQuery

C3P0（JDBC3 Connection and Statement Pooling）  -  preferredTestQuery

Atomikos：Tomcat Spring ActiveMQ MySQL JMX Integration  -  testQuery

## 数据库类型与语句的对应关系

MySQL  -  SELECT 1

PostgreSQL  -  SELECT 1

Microsoft SQL Server  -  SELECT 1

SQLite  -  SELECT 1

H2  -  SELECT 1

Ingres  -  SELECT 1

Oracle  -  select 1 from dual

DB2  -  select 1 from sysibm.sysdummy1 或 SELECT current date FROM sysibm.sysdummy1

Apache Derby  -  VALUES 1 FROM SYSIBM.SYSDUMMY1 或 SELECT 1 FROM SYSIBM.SYSDUMMY1

HSQLDB  -  SELECT 1 FROM any_existing_table WHERE 1=0 或 SELECT 1 FROM INFORMATION_SCHEMA.SYSTEM_USERS

Informix  -  select count(*) from systables
