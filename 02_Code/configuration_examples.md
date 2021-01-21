#### DataSource for Oracle

https://www.oracle.com/technetwork/database/enterprise-edition/jdbc-10201-088211.html

**server.xml**


```
<!-- Global JNDI resources Documentation at /docs/jndi-resources- howto.html-->
<GlobalNamingResources>
<!-- Editable user database that can also be used by UserDatabaseRealm to authenticate users-->
<Resource name="jdbc/tomcat7" auth="Container"
type="javax.sql.DataSource" driverClassName="oracle.jdbc.OracleDriver"
url="jdbc:oracle:thin:@127.0.0.1:1521:test"
description="test database for tomcat 7"
username="admin" password="admin" maxActive="20" maxIdle="10"
maxWait="-1"/>
</GlobalNamingResources>
```


**WEB-INF/web.xml**

```
<resource-ref>
<description>Oracle Datasource for tomcat </description>
<res-ref-name>jdbc/tomcat7 </res-ref-name>
<res-type>javax.sql.DataSource</res-type>
<res-auth>Container</res-auth>
</resource-ref>
```


#### DataSource for MySQL

http://dev.mysql.com/downloads/

**server.xml**

```
<Resource name="jdbc/tomcat7" auth="Container" type="javax.sql.DataSource"
maxActive="100" maxIdle="30" maxWait="10000" username="tomcatuser" password="tomcat" driverClassName="com.mysql.jdbc.Driver"
url="jdbc:mysql://localhost:3306/tomcat7"/>

```

**WEB-INF/web.xml**

```
<web-app xmlns="http://java.sun.com/xml/ns/j2ee" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://java.sun.com/xml/ns/j2ee http://java.sun.com/xml/ns/j2ee/web-app_2_4.xsd"
version="2.4">
<description>Tomcat 7 test DB</description>
<resource-ref>
<description>DB Connection</description>
<res-ref-name>jdbc/tomcat7</res-ref-name>
<res-type>javax.sql.DataSource</res-type>
<res-auth>Container</res-auth>
</resource-ref>
</web-app>

```



```
mysql> GRANT ALL PRIVILEGES ON *.* TO tomcatuser@localhost IDENTIFIED BY 'tomcat7' WITH GRANT OPTION;
mysql> create database tomcat7;
mysql> use tomcat7;
mysql> create table testdata ( id int not null auto_increment primary key,foo varchar(25), bar int);
```




#### DataSource for MySQL

**server.xml**

```
<Resource name="jdbc/tomcat7" auth="Container" type="javax.sql.DataSource" driverClassName="org.postgresql.Driver" url="jdbc:postgresql://127.0.0.1:5432/tomcat7" username="tomcat7" password="tomcat" maxActive="20" maxIdle="10" maxWait="-1"/>

```


**WEB-INF/web.xml**

```
<resource-ref>
<description>postgreSQL Tomcat datasource </description>
<res-ref-name>jdbc/tomcat7 </res-ref-name>
<res-type>javax.sql.DataSource</res-type>
<res-auth>Container</res-auth>
</resource-ref>
```





