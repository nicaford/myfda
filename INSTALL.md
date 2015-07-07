Install Quick Reference
=======================

This file contains basic instructions on obtaining, building, and running the MyFDA prototype.
For detailed installation instructions, please consult the [Install Guide](docs/Install%20Guide.md).
For information on configuring MyFDA in a production environment, please see the [Configuration Guide](docs/Configuration%20Guide.md).

Development Environment Setup
-----------------------------

To begin development you'll need a few tools installed.  MyFDA is a Java/Javascript application and so 
should run easily on most operating systems.  You will need the following software installed before you 
can begin:

* Java 1.8
  * Windows : http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
  * Linux : http://openjdk.java.net/install/
* Apache Maven 3.3.3 : https://maven.apache.org/download.cgi
* Git 2.4.5 : https://git-scm.com/downloads

Cloning the Application
-----------------------

The MyFDA development team uses GitHub to manage the application source code and pull requests to approve 
changes to the project.  You will need to signup for GitHub and fork the main project repository if you 
wish to contribute.  This fork will be used to hold your commits while they are waiting for review.  To 
fork the repository visit https://github.com/NIC-Federal/myfda then click the Fork button in the upper 
right hand corner of the project.  Once you have created the fork you should clone your fork to your 
development environment.  You can get the URL of your fork by looking on your GitHub fork page on the left 
hand side of the page under "HTTPS clone URL" then use git to clone the repository.  This guide assumes 
you will clone the project into the directory ~/Source/[github username]/myfda .  To do this first change 
directories to the directory above where you would like a copy of the project repository.

```
cd ~/Source
```

Now you are ready to clone the repository.  Below is an example:

```
git clone https://github.com/marktchurch/myfda.git
```

When the git clone is completed you should change directories into the root of the project.

```
cd myfda
```

Running the Application
-----------------------

With the application checked out you are ready to start working with the application.  You have a couple of 
choices for this.  The MyFDA team primarily uses two methods for running the application the first is to 
launch the application using Maven and the second is to launch the application using a Docker image.

###Using Maven

If you will be making changes to the application you will likely want to build and run the application 
using Maven.  This will build and run the application more quickly than by using the Docker method 
described below.  To do this simply execute the maven goal "spring-boot:run".

```
mvn spring-boot:run
```

The application will be built, tested and finally executed.  When completed you will see the message:

```
2015-06-28 15:57:11.959  INFO 11095 --- [lication.main()] s.b.c.e.t.TomcatEmbeddedServletContainer : Tomcat started on port(s): 8080 (http)
2015-06-28 15:57:11.961  INFO 11095 --- [lication.main()] com.nicusa.UiApplication                 : Started UiApplication in 6.849 seconds (JVM running for 46.964)
2015-06-28 16:01:29.871  INFO 11095 --- [nio-8080-exec-1] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring FrameworkServlet 'dispatcherServlet'
2015-06-28 16:01:29.871  INFO 11095 --- [nio-8080-exec-1] o.s.web.servlet.DispatcherServlet        : FrameworkServlet 'dispatcherServlet': initialization started
2015-06-28 16:01:29.883  INFO 11095 --- [nio-8080-exec-1] o.s.web.servlet.DispatcherServlet        : FrameworkServlet 'dispatcherServlet': initialization completed in 12 ms
```

You now should be able to use the application by visiting http://localhost:8080

###Using Docker
In order to facilitate the deployment of the MyFDA application in a variety of environments the 
application has been packaged as a Docker image.  This method of running MyFDA is most suitable when you 
want to make changes to the way MyFDA will be deployed in production or establish an environment as close 
as possible to production in order to perform functional and security testing.  In order to use this 
section of the document you must first [install Docker](https://docs.docker.com/installation/).   Once
Docker is installed you can build the application using the following command:

```
docker build -t myfda .
```

Once completed you can run the docker image using:

```
docker run -p 8080:8080 myfda
```

You now should be able to use the application by visiting http://localhost:8080