# JavaServer Faces and Eclipse Tutorial

## Description

In this tutorial we will show how to import a simple 'Hello World' `maven` project into Eclipse on Windows 10.

## Dependencies

* Windows 10
* Java 8
* Tomcat 
* Eclipse JEE

## Install Java 8

1. Download [Java 8 OpenJSDK implementation from RedHat](https://developers.redhat.com/products/openjdk/download).
1. Extrat the zip file `java-1.8.0-openjdk-<version>.zip`, in my case it was`java-1.8.0-openjdk-1.8.0.262-3.b10.redhat.windows.x86_64`.
1. Copy the extracted folder to `C:\Program Files\java` or to any other folder
1. Then go to `System > Advanced Settings > Environment Variables` edit `PATH` and add
```
C:\Program Files\java\java-1.8.0-<version>\bin
```
1. Edit or include `JAVA_HOME` with
```
C:\Program Files\java\java-1.8.0-openjdk-1.8.0-<version>
```

In this way you can include other versions of java and change it easily according to your application.

Open the `cmd` and check the java version:

```
C:\Users\Usuario>java -version
openjdk version "1.8.0_262"
OpenJDK Runtime Environment (build 1.8.0_262-b10)
OpenJDK 64-Bit Server VM (build 25.262-b10, mixed mode)
```

## Install Tomcat

1. Download Tomcat. Chose the version you need: [version 7](https://tomcat.apache.org/download-70.cgi), [version 8](https://tomcat.apache.org/download-80.cgi), [version 9](https://tomcat.apache.org/download-90.cgi).
1. Extract the zip file `apache-tomcat-<version>.zip`, here we using `apache-tomcat-8.5.57-windows-x64`
1. Copy the extracted folder to `C:\Program Files\tomcat` or to any other folder
1. Then go to `System > Advanced Settings > Environment Variables` edit `PATH` and add
```
C:\Program Files\tomcat\apache-tomcat-8.5.57-windows-x64\apache-tomcat-8.5.57\bin
```

Open the `cmd` and start the server:

```
C:\Users\Usuario>startup.bat
```

Do not use `tomcat8` to start the server, use `startup.bat` instead.

Access [http://localhost:8080](http://localhost:8080)

**Note1:** we are not going to use tomcat directly neither start it up in this way.

**Note2:** we are going to use it integrated with eclipse. It will work in a different way.

**Note3:** if you want to use tomcat as usual then just start it up as we did previously and copy your `.war` file to `webapps`

## Install Eclipse

1. Download Eclipse from [Eclipse Download Packages](https://www.eclipse.org/downloads/packages/). We chose the [Enterprise Edition](https://www.eclipse.org/downloads/packages/release/2020-06/r/eclipse-ide-enterprise-java-developers).
1. Extract the zip file `eclipse-jee-<version>.zip`, here we using `eclipse-jee-2020-06-R-win32-x86_64`
1. Copy the extracted folder to `C:\Program Files\eclipse` or to any other folder
1. Then go to `System > Advanced Settings > Environment Variables` edit `PATH` and add
```
C:\Program Files\eclipse\eclipse-jee-<version>\eclipse
```

Open the `cmd` and start eclipse:

```
C:\Users\Usuario>eclipse
``` 

You can have different versions of eclipse in your machine (Basic, JEE, C++, etc). You just need to extract it to `C:\Program Files\tomcat` and change the `PATH`.

When you open it for the first time you will be asked to select the workspace folder. It could be any folder. This is were it will save your configuration.

## Import a Maven Project

In [../README.md](../README.md) we describe how to create a simple Maven Project. It basically set up a `pom.xml` file using `maven` command line and use `mvn package` to generate `.WAR` files.

Now, we show you how to import this project.

1. Open `eclipse`
1. `File > Import > Select Maven > Existing Maven Projects > Root directory > [then select the pom.xml file] > Finish`

## Set up Tomcat as Project Server

It is important to know that `eclipse` won´t using `tomcat` directly. It will you some of its libraries and start it up for current project. Thus, `tomcat` should be stopped otherwise we will have `PORT` conflict with two servers trying to access it.

Also, `eclipse` won´t generate the `.WAR` file neither copy anything to `tomcat` standard directory `webapps`. It will start the server and use a temporary folder to keep the classes. Actually, we are able to edit the `.xhtml` files in project folder and see the changes reflected in the server.

Let´ do it:

1. Open `eclipse`
1. `Window > Preferences`
1. `Server > Server Run Time Environment`
1. `Add > Apache Tomcat <version> > Next`
1. `Tomcat installation directory`. It will verify if the directory is valid and if it contains a valid version.
1. `JRE`. I choose the java that I have installed previously. Then `Finish`

## Run the application

1. Right click on project´s name
1. `Run as > Run on the Server`

It will open a browser window and server tab on `eclipse`. That´s it!

You can do changes on your `.xhtml` files and see them without restarting the server. For `.java` files you might need to start it again.

## Generate `.WAR` file

This is really simple. Just Go to `File > Export > [choose .WAR]`

## Conclusion 

You have completed the JavaServer Faces with Eclipse on Windows Tutorial.