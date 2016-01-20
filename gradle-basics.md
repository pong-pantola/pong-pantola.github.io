---
layout: post
title: Gradle Basics
permalink: /gradle-basics/
---



[Gradle](http://gradle.org/) is an open source build automation system.  It has a Java plugin to allow building Java applications and running tests for them.

In this tutorial you will explore the different tasks available in Gradle.

<br>

>**Prerequisite:**

>Having a basic background in Java programming is required to do this tutorial.




<br>


####Install Gradle


1. Go to [Gradle's download page](http://gradle.org/gradle-download/).  Download the latest version.  The `Binary only distribution` is sufficient.


1. Extract Gradle directory.

1. In the extracted Gradle directory, confirm that there is a `bin` subdirectory.  Take note of the path of the `bin` subdirectory (e.g., `/temp/gradle-2.10/bin`).

1. Add the path of the `bin` subdirectory to the `PATH` environment variable.

	In `Windows`, you may use this [link](http://geekswithblogs.net/renso/archive/2009/10/21/how-to-set-the-windows-path-in-windows-7.aspx) as a guide.

	In `Linux`, kindly consult the Internet to permanently include the path of the Gradle `bin` directory to the `PATH` environment variable.

	<br>
	
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

	<br>

####Understanding Gradle

Gradle is a build automation system.  A build has one or more projects (e.g., the thing we build like a `.jar` file).  A project, on the other hand, has one or more tasks (e.g., compiling a project or running a test).


1. Open a terminal window and check the tasks available in Gradle.


	```text
	> gradle tasks
	```

	**Output:**

	```
	:
	:
	assemble - Assembles the outputs of this project.
	build - Assembles and tests this project.
	buildDependents - Assembles and tests this project and all projects that depend on it.
	buildNeeded - Assembles and tests this project and all projects it depends on.
	classes - Assembles main classes.
	clean - Deletes the build directory.
	jar - Assembles a jar archive containing the main classes.
	testClasses - Assembles test classes.
	war - Generates a war archive with all the compiled classes, the web-app content and the libraries.
	```

	Some of these tasks will be used in succeeding exercises involving Gradle.

	<br>

####End of Tutorial

Go back to the [List of Tutorials](/tutorial-list).

####What's next?

[Gradle's Dependency Management Tutorial](/gradle-dependency-management)


