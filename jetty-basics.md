---
layout: post
title: Jetty Basics
permalink: /jetty-basics/
---


Jetty is a Java HTTP (Web) server and Java Servlet container. 

In this tutorial you will learn how to deploy a web application packaged as a `.war` file in Jetty.

<br>

>**Prerequisite:**

>You are not required (but **recommended**) to do  the [Git Basics Tutorial](/git-basics).

>- **However**, ensure that you have Git client installed in your machine.

	
<br>


####Install Jetty


1. Go to [Jetty's download page](http://download.eclipse.org/jetty/).  Download the appropriate version.

	Jetty is highly dependent on the installed JDK.  Make sure that your version of JDK is compatible with the Jetty version you will download.  You may refer to the [Jetty Comparison Table](https://wiki.eclipse.org/Jetty/Starting/Jetty_Version_Comparison_Table) for Jetty-JDK version compatibility.

	<br>
	
1. Extract Jetty in a directory.  We will call this directory as Jetty's home directory.

1. Open a terminal window a go to the Jetty directory.

1. Start the Jetty server.

	```text
	java -jar start.jar
	```

	**Output:**

	```text
	:
	:
	2016-01-20 16:16:04.688:INFO:oejs.ServerConnector:main: Started ServerConnector@380fb434{HTTP/1.1,[http/1.1]}{0.0.0.0:8080}
	2016-01-20 16:16:04.689:INFO:oejs.Server:main: Started @2121ms
	```
	
	>Just in case you encounter an error in running Jetty, you may need to edit start.ini and include the following line:
	`-Dorg.apache.jasper.compiler.disablejsr199=true`
	
	>If this still does not work, remove the said line and check the Internet for possible solution.

	<br>

###Deploy a Sample Application in Jetty

1. Open another terminal window.  Clone the git repository `https://github.com/pong-pantola/jetty-basics.git` and go to the created `jetty-basics` directory.

	```text
	> git clone https://github.com/pong-pantola/jetty-basics.git
	> cd jetty-basics
	```

	A sample web application `calcu.app` can be found in the directory.  This sample application simply displays 3 simple mathematical equations.  

	<br>
	
1. Copy `calcuapp.war` to Jetty's `webapps` subdirectory.

1. On a web browser, go to [`http://localhost:8080/calcuapp/calculator.jsp`](http://localhost:8080/calcuapp/calculator.jsp).

	**Output:**
		
	```text
	5 + 9 = 14
	8 - 2 = 6
	4 x 7 = 28 
	```

	You have successfully deployed the calculator application in Jetty.

	<br>
	
1. Delete `calcuapp.war` from Jetty's `webapps` subdirectory.

1. Go back to the terminal window showing the Jetty console.  Press `Ctrl+C` to stop the server.

	<br>

####End of Tutorial

Go back to the [List of Tutorials](/tutorial-list).

####What's next?

[GitHub Basics Tutorial](/github-basics)

