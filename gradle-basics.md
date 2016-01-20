---
layout: post
title: Gradle Basics
permalink: /gradle-basics/
---

##Application Development Tutorial

###Gradle Basics
[Gradle](http://gradle.org/) is an open source build automation system.  It has a Java plugin to allow building and running test of Java applications.

In this tutorial you will explore the different task available in Gradle.

<br>

>**Prerequisite:**

>You are not required (but **recommended**) to do  the [Git Basics Tutorial](/git-basics).

>- **However**, ensure that you have Git client installed in your machine.




<br>


####Install Gradle


1. Go to [Gradle's download page](http://gradle.org/gradle-download/).  Download the latest version.  The `Binary only distribution` is sufficient.


1. Extract Gradle directory.

1. In the extracted Gradle directory, confirm that there is a `bin` subdirectory.  Take note of the path of the `bin` subdirectory (e.g., `/temp/gradle-2.10/bin`).

1. Add the path of the `bin` subdirectory to the `PATH` environment variable.

	In `Windows`, you may use this [link](http://geekswithblogs.net/renso/archive/2009/10/21/how-to-set-the-windows-path-in-windows-7.aspx) as a guide.

	In `Linux`, kindly consult the Internet to permanently include the path of the Gradle `bin` directory to the `PATH` environment variable.

1. Open a terminal window and issue the `gradle` command to confirm that gradle is set-up properly.

	```text
	> gradle
	```

	**Output:**

	```text
	:help
	
	Welcome to Gradle 2.10.
	
	To run a build, run gradle <task> ...
	
	To see a list of available tasks, run gradle tasks
	
	To see a list of command-line options, run gradle --help
	
	To see more detail about a task, run gradle help --task <task>
	
	BUILD SUCCESSFUL
	
	Total time: 2.034 secs
	```




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

####What's next?




