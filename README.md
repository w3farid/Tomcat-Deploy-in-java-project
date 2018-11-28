# Tomcat-Deploy-in-java-project
I have described the tomcat deploy a to z.

### By this tutorial can be configure 
1. Tomcat 8.0.30
2. Tomcat 7.0.67
3. Tomcat 6.0.44
## 1. Tomcat 7 and Tomcat 8
Tomcat users are defined in the file – $TOMCAT_HOME/conf/tomcat-users.xml, by default, there is NO user, it means no one can access the Tomcat manager page.

To enable users to access the Tomcat manager page, add a user as the role manager-gui.
### $TOMCAT_HOME/conf/tomcat-users.xml (Original)
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!--
  Licensed to the Apache Software Foundation (ASF) under one or more
  contributor license agreements.  See the NOTICE file distributed with
  this work for additional information regarding copyright ownership.
  The ASF licenses this file to You under the Apache License, Version 2.0
  (the "License"); you may not use this file except in compliance with
  the License.  You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License.
-->
<tomcat-users xmlns="http://tomcat.apache.org/xml"
              xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
              xsi:schemaLocation="http://tomcat.apache.org/xml tomcat-users.xsd"
              version="1.0">
<!--
  NOTE:  By default, no user is included in the "manager-gui" role required
  to operate the "/manager/html" web application.  If you wish to use this app,
  you must define such a user - the username and password are arbitrary. It is
  strongly recommended that you do NOT use one of the users in the commented out
  section below since they are intended for use with the examples web
  application.
-->
<!--
  NOTE:  The sample user and role entries below are intended for use with the
  examples web application. They are wrapped in a comment and thus are ignored
  when reading this file. If you wish to configure these users for use with the
  examples web application, do not forget to remove the <!.. ..> that surrounds
  them. You will also need to set the passwords to something appropriate.
-->
<!--
  <role rolename="tomcat"/>
  <role rolename="role1"/>
  <user username="tomcat" password="tomcat" roles="tomcat"/>
  <user username="both" password="tomcat" roles="tomcat,role1"/>
  <user username="role1" password="tomcat>" roles="role1"/>
-->
</tomcat-users>
```

### $TOMCAT_HOME/conf/tomcat-users.xml (Updated)
```xml
<?xml version="1.0" encoding="UTF-8"?>

<tomcat-users xmlns="http://tomcat.apache.org/xml"
              xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
              xsi:schemaLocation="http://tomcat.apache.org/xml tomcat-users.xsd"
              version="1.0">
<role rolename="manager-gui"/>
<role rolename="manager-script"/>
<role rolename="manager-jmx"/>
<role rolename="manager-gui"/>
<role rolename="manager-status"/>
<role rolename="admin"/>
<user username="admin" password="admin" roles="manager-gui,manager-script,admin"/>
</tomcat-users>
```
> Saved it and restart Tomcat, now you should able to access the default manager page (http://localhost:8080/manager) with 
> user = “admin” and password = “admin”

## 2. Tomcat 6

### $TOMCAT_HOME/conf/tomcat-users.xml (Updated)
```xml
<tomcat-users>

  <role rolename="manager"/>
  <user username="admin" password="admin" roles="manager"/>

</tomcat-users>
```
-- extend SpringBootServletinitilizer and override the method configure and return builder.sourses(
```@SpringBootApplication
public class Application extends SpringBootServletInitializer {

    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
    
    @Override
    protected SpringApplicationBuilder configure(SpringApplicationBuilder builder) {
    	return builder.sources(Application.class);
    }
}
```

[Tomcat Manager App HOW-TO](https://tomcat.apache.org/tomcat-8.0-doc/manager-howto.html)

## About the Author
![alt text][logo]

[logo]: https://github.com/w3farid/portfolio/blob/master/static/img/farid-nid.png "Farid Ahmed"

I love Java and open source stuff. Follow him on [Twitter](https://twitter.com/w3farid), or befriend him on [Facebook](https://facebook.com/w3farid). You can hire me any kind of java or web-based application. I have good architecture knowledge.

