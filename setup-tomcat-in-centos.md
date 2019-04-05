# Setup Tomcat in Centos

## Getting Super Powers

context.xml

```
 <Resource name="jdbc/test" 
    auth="Container" 
    type="javax.sql.DataSource" 
    driverClassName="org.hsqldb.jdbcDriver" 
    url="jdbc:hsqldb:hsql://localhost:9010/xdb" 
    username="sa" 
    password="" 
    maxActive="20" 
    maxIdle="10" 
    maxWait="10000"/>
```

server.xml

```
    <Connector port="9090" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />
```

tomcat-user.xml

```
<role rolename="manager-gui"/>
<role rolename="manager-status"/>
<role rolename="manager-script"/>
<role rolename="manager-jmx"/>
<role rolename="admin-gui"/>
<user username="admin" 
    password="admin" 
    roles="manager-gui,manager-status,manager-script,manager-jmx,admin-gui"/>
```

start tomcat

```text
systemctl status tomcat
systemctl start tomcat
systemctl restart tomcat
```

