# JavaServer Faces Tutorial

## Description 

In this tutorial we will show you how to create a simple project struture for using [JavaServer Faces (JSF) web framework](http://www.javaserverfaces.org).

It is based on [this tutorial](http://www.javaserverfaces.org/get-started).

## Dependencies

* Ubuntu 18.04
* Java 8
* Maven

## Install Maven

* [Check this tutorial](https://maven.apache.org/install.html)

## Setup maven project

```
mvn archetype:generate -DgroupId=com.github.cristnascimento.helloworld  \
    -DartifactId=helloworld -DarchetypeArtifactId=maven-archetype-webapp
```

## Project structure

```
src
target
pom.xml
```

## Set up `pom.xml`

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.github.cristnascimento.helloworld</groupId>
  <artifactId>helloworld</artifactId>
  <packaging>war</packaging>
  <version>1.0-SNAPSHOT</version>
  <name>helloworld Maven Webapp</name>
  <url>http://maven.apache.org</url>
  <repositories>
    <repository>
        <id>maven2-repository.dev.java.net</id>
        <name>Java.net Repository for Maven</name>
        <url>http://download.java.net/maven/2</url>
    </repository>
</repositories>

  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>3.8.1</version>
      <scope>test</scope>
    </dependency>
    <dependency>
        <groupId>javax.faces</groupId>
        <artifactId>jsf-api</artifactId>
        <version>2.0</version>
        <scope>provided</scope>
    </dependency>
      <dependency>
        <groupId>com.sun.faces</groupId>
        <artifactId>jsf-api</artifactId>
        <version>2.0.2</version>
        <scope>runtime</scope>
    </dependency>
    <dependency>
        <groupId>com.sun.faces</groupId>
        <artifactId>jsf-impl</artifactId>
        <version>2.0.2</version>
        <scope>runtime</scope>
    </dependency>
  </dependencies>
  <build>
    <finalName>helloworld</finalName>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>2.0.2</version>
            <configuration>
                 <source>1.8</source>
                 <target>1.8</target>
                 <encoding>UTF-8</encoding>
            </configuration>
        </plugin>
    </plugins>
  </build>
</project>
```

## Add Faces Servlet and Mapping

`/src/main/webapp/WEB-INF/web.xml`
```xml
<!DOCTYPE web-app PUBLIC
 "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"
 "http://java.sun.com/dtd/web-app_2_3.dtd" >

<web-app>
    <display-name>Archetype Created Web Application</display-name>

    <context-param>
        <param-name>javax.faces.PROJECT_STAGE</param-name>
        <param-value>Development</param-value>
    </context-param>

    <servlet>
        <servlet-name>Faces Servlet</servlet-name>
        <servlet-class>javax.faces.webapp.FacesServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>Faces Servlet</servlet-name>
        <url-pattern>*.jsf</url-pattern>
    </servlet-mapping>
</web-app>
```

## Create a managed bean

`/src/main/java/com/github/cristnascimento/helloworld/WelcomeBean.java`
```java
import javax.faces.bean.ManagedBean;

@ManagedBean(name = "welcome", eager = true)
public class WelcomeBean {
    public WelcomeBean() {
        System.out.println("WelcomeBean instantiated");
    }
    public String getMessage() {
        return "I'm alive!";
    }
}
```

## Create a view

 `/src/main/webapp/home.xhtml`

```xml
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
   "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Hello JSF 2!</title>
    </head>
    <body>
       #{welcome.message}
    </body>
</html>
```

## Build the project

```
$ mvn package
```

It will create the `target/helloworld.war`

## Copy the project to Tomcat server

```
$ sudo cp target/helloworld.war /opt/tomcat/webapps
```

## Restart the server

```
$ sudo systemctl restart tomcat
```

## Check the log

Logs will be written in `/opt/tomcat/logs`.

## Access the website

[http://localhost:8080/helloworld/home.jsf](http://localhost:8080/helloworld/home.jsf)

## Conclusion

That's it! You have learned how to set up a simple project with JSF and Maven.

Try to learn more by reading articles and watching videos. I suggest those to start with:

* [Article: JavaServer Faces from DevMedia (Portuguese)](https://www.devmedia.com.br/javaserver-faces/33272)
* [Video: Maratona JSF from DevDojo (Portuguese)](https://www.youtube.com/playlist?list=PL62G310vn6nHSNpACkELWiPlM8J8z8t5J)