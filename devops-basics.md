---
layout: post
title: Bluemix Devops Services Basics
permalink: /devops-basics/
---

##Application Development Tutorial

###Bluemix DevOps Services Basics

[Bluemix DevOps Services](https://hub.jazz.net) or simply Bluemix DevOps is a software as a service (SaaS) cloud technology from IBM that supports development, tracking and planning, and continuous delivery of software.

In this tutorial you will explore the different features of Bluemix DevOps.

>**Prerequisite:**

>Having a basic background in web application development is required to do this tutorial.

>You are not required (but **recommended**) to do  the [Bluemix Basics Tutorial](/bluemix-basics).

>- **However**, ensure that you have a Bluemix account.  

>You are required to do  the [GitHub Basics Tutorial](/github-basics).

<br>

####Set-up your Bluemix DevOps Account

1. Go to [Bluemix DevOps](https://hub.jazz.net) and click the `LOG IN` button.
	
1. Login using your Bluemix account.  

1. If this is the first time you login to Bluemix DevOps, you may be asked for an alias.  Enter an alias.


<br>

####Explore Public Projects in Bluemix DevOps

There are public projects in Bluemix DevOps that you may use as a basis for your own project.

1. In the menu, click `EXPLORE`.

1. In the `Search` text box, type `Blue-Labs`.  

1. In the search result, look for the project.  `jlmarech | Blue-Labs`.  Click the link for this project.

1. Create a copy of this project by clicking the `FORK PROJECT` button.

1. For the name of the project use `Blue-Labs`.  Click the `CREATE` link.

	Even if the name of your project is the same as `jlmarech`s project (i.e., `Blue-Labs`, you can still differentiate your project with his due to to your and his alias.  For example, `jlmarech` project is referred to as `jlmarech | Blue-Labs`.
	
	In the [GitHub Basics Tutorial](/github-basics), you learned how to fork an existing repository.  The concept behind forking a repository is similar to forking a Bluemix DevOps project.  However, it should be emphasized that a repository is different from a project.

	A project utilizes a repository.  Therefore, when you forked the Bluemix DevOps project `jlmarech | Blue-Labs`, the different components of the project including the repository are copied as well.  The source code you will view later is under your repository and not under `jlmarech`.

	It should also be emphasized that the repository that was created is not saved in GitHub.  IBM Bluemix maintains its own Git repository (which we will call as Bluemix repository) and this is utilized by Bluemix DevOps.  However, when you create a project from scratch (i.e., you did not fork a project from an existing one), you have the option to use a Bluemix or GitHub repository.

	<br>
	
1. Click the `EDIT CODE` button.  This will open the Bluemix DevOps editor.

	The Bluemix DevOps editor allows you to update files that are in the working directory.  The files in a working directory is similar to files in a local repository as discussed in the [GitHub Basics Tutorial](/github-basics).  Recall that changes made in the local repository are not reflected automatically in the GitHub remote repository.
	
	Similarly, changes made in the working directory are not reflected automatically in the Bluemix repository.  You still need to push changes to sync the working directory with the Bluemix repository.  This is further discussed in the [Bluemix DevOps Delivery Pipepline Tutorial](/devops-delivery-pipeline).

	<br>
	
7. Click `app.js`.  As you can see, an editor will appear which allows you to modify the code.

8. Click the `TRACK & PLAN` button.  This will open the quick planner.

	The quick planner allows you to do agile planning (e.g., creating stories and defects).  This is further discussed in  the [Bluemix DevOps Track and Plan Tutorial](/devops-track-plan).

	<br>

9. Click the `BUILD & DEPLOY` button.  This will open the delivery pipeline.

	The delivery pipeline allows you to have continuous delivery (e.g, updates made in your repository gets reflected immediately in your deployed application).  This is further discussed in the [Bluemix DevOps Delivery Pipepline Tutorial](/devops-delivery-pipeline).

	<br>

####End of Tutorial

Go back to the [List of Tutorials](/tutorial-list).

####What's next?

[Bluemix DevOps Services Delivery Pipeline Tutorial](/devops-delivery-pipeline)


