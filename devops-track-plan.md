---
layout: post
title: Bluemix Devops Services Track and Plan
permalink: /devops-track-plan/
---

##Application Development Tutorial

###Bluemix DevOps Services Track and Plan

[Bluemix DevOps Services](https://hub.jazz.net) has a track and plan feature to support Agile planning.

In this tutorial you will learn how to use track and plan to create and monitor stories and defects in a web application project.


>**Prerequisite:**

>You are **required** to do the [Bluemix DevOps Services Delivery Pipeline Tutorial](/devops-delivery-pipeline).

>- The Bluemix DevOps project as well as the GitHub repository you created in this tutorial are needed in the current tutorial. 

>You are not required (but **recommended**) to do  the [Bluemix Basics Tutorial](/bluemix-basics).

>- **However**, ensure that you have a Bluemix account.  
>- Your account should have the space `dev` under the region `US-South`.  The creation of the space `dev` is discussed in [Bluemix Basics Tutorial](/bluemix-basics).

>You are not required (but **recommended**) to do  the [GitHub Basics Tutorial](/github-basics).

>- **However**, ensure that you have a GitHub account.


<br>


####Open AN Existing Bluemix DevOps project

1. Login to [Bluemix DevOps](https://hub.jazz.net/).

1. Click the `<username>|devops-delivery-pipeline` project you created in the [Bluemix DevOps Services Delivery Pipeline Tutorial](/devops-delivery-pipeline).

1. Click the `EDIT CODE` button.  You will be redirected to Bluemix DevOps' editor.  In this tutorial, we will refer to this browser tab as `DEVOPS-EDITOR TAB`.

1. On the `DEVOPS-EDITOR TAB`: Click (open in another browser tab) the `Git Repository` icon found on the left side of the screen.  We will refer to this browser tab as `DEVOPS-GIT TAB`.

1. On the `DEVOPS-GIT TAB`: Make sure that there are no `Incoming` changes.  IF there are, click the `Sync` button to make sure that your Bluemix DevOps working directory and GitHub repository are in sync.


1. On the `DEVOPS-GIT TAB`: Click (open in another browser tab) the `BUILD & DEPLOY` button.  We will refer to this browser tab as `DEVOPS-DELIVERY-PIPELINE TAB`.

1. On the `DEVOPS-GIT TAB`: Click (open in another browser tab) the `TRACK & PLAN` button.  We will refer to this browser tab as `DEVOPS-AGILE TAB`.

	This opens Bluemix DevOps` quick planner that allow you to do agile planning.

	<br>

1. On the `DEVOPS-AGILE TAB`: On the left pane, click the `BACKLOG` link.

	The backlog for the current DevOps project is empty.  You will be adding entries in the backlog.

	<br>

1. On the `DEVOPS-AGILE TAB`: Click the `Create a work item` link to add a story.

1. On the `DEVOPS-AGILE TAB`: On the `Type a work item summary` text box, type the following: `As a user, I want to see the multiplication table for 9`.

	This is an example of a story.  You may add attributes to a story using `Tweet-like notation`.

	<br>
	
1. On the `DEVOPS-AGILE TAB`: Make sure that your cursor is still in the text box and at the end of the `As a user, I want to see the multiplication table for 9`, click the following icons below the text box and choose the following values:

	||||
	|---|---|---|
	| **type** | Story |
	| **priority** | High |

	>**Note**: Mouse hover on the icons to know the purpose of each icon.

	Confirm that the text box now contains `As a user, I want to see the multiplication table for 9 *story $high`.  

	If you made a mistake in using the icons, just copy the text `As a user, I want to see the multiplication table for 9 *story $high` in the text box.

	<br>

1. On the `DEVOPS-AGILE TAB`: Click the `CREATE` button.

	You now have your first entry in your backlog.

	You will add another entry, this time the type is a defect (instead of a story).

	<br>
	
1. On the `DEVOPS-AGILE TAB`: Click the `Create a work item` link to add a defect.

1. On the `DEVOPS-AGILE TAB`: On the `Type a work item summary` text box, type the following: `Foreground color must be blue`.
	
1. On the `DEVOPS-AGILE TAB`: Make sure that your cursor is still in the text box and at the end of the `Foreground color must be blue`, click the following icons below the text box and choose the following values:

	||||
	|---|---|---|
	| **type** | Defect |
	| **priority** | Low |


	Confirm that the text box now contains `Foreground color must be blue *defect $low`.  


	<br>

1. On the `DEVOPS-AGILE TAB`: Click the `CREATE` button.

	You now have two entries in your backlog.

	You will fix the defect (i.e., foreground color must be blue) in the backlog.  To properly track the fix you will do later, take note of the defect number of this defect.  This is the number (around 4-digits) that is visible on the left side of the `Foreground color must be blue` entry.  In this tutorial, we will refer to this defect as the foreground defect.
	
	<br>
	
1. On the `DEVOPS-AGILE TAB`: Click the `Unassigned` link of the foreground defect and assign it to yourself.

	>In an actual project, you may add members in your Bluemix DevOps project so that you may assign a backlog to a particular member.  You will learn later how to add members in a Bluemix DevOps project.

	<br>

1. On the `DEVOPS-AGILE TAB`: Click the `New` link of the foreground defect and change it `Start Working`.

1.  On the `DEVOPS-EDITOR TAB`:  Open the file `src/main/webapp/calculator.jsp`.  

1. On the `DEVOPS-EDITOR TAB`: Update the `body` section of `calculator.jsp` to include the `<font>` and `</font>` tags:

	```text
	<font color="blue">
	<%="5 + 9 = " + m.add(5, 9)%>
	<br>
	<%="8 - 2 = " + m.sub(8, 2)%>
	<br>
	<%="4 x 7 = " + m.multiply(4, 7)%>
	<br>
	<%="2 + 2 = " + m.add(2, 2)%>
	<br>
	<%="3 - 3 = " + m.sub(3, 3)%>
	<br>
	<%="4 x 4 = " + m.add(4, 4)%>
	<br>
	</font>
	```

	<br>
	
1. On the `DEVOPS-EDITOR TAB`:  Make sure to save the changes made.

1. On the `DEVOPS-GIT TAB`: Refresh the page.

1. On the `DEVOPS-GIT TAB`: Set the following values:

	||||
	|---|---|---|
	| **Select All** | checked |
	| **Commit message** | updated `calculator.jsp` to fix defect `<defect number>` |

	>**IMPORTANT:** Make sure to change `<defect number>` with the defect number of the foreground defect.  If you don't remember the defect number, go back to the `DEVOPS-AGILE TAB`.

	<br>

1. On the `DEVOPS-GIT TAB`: Click the `Commit` button.


1. On the `DEVOPS-GIT TAB`: Click the `Push` button.

	Your GitHub repository is now updated with the new version of `calculator.jsp`.

1. Quickly switch to the `DEVOPS-DELIVERY-PIPELINE TAB` and verify that the `Build Stage` automatically started due to the changes made in the GitHub repository.

	Wait for the first three stages (i.e., `Build Stage`, `Test Stage`, and `Dev Deploy Stage`) to complete.

	<br>

1. Open another web browser tab.  We will refer to this browser tab as `CALCULATOR-APP TAB`.

1.  On the `CALCULATOR-APP TAB`:  Go to `http://calculator-<your_name>.mybluemix.net/calculator.jsp`.

	The value of `<your_name>` is the one you used in the [Bluemix DevOps Services Delivery Pipeline Tutorial](/devops-delivery-pipeline). 

	If you cannot recall the URL of your application, look at the `Dev Deploy Stage` of the `DEVOPS-DELIVERY-PIPELINE TAB`.   The URL of the Bluemix application is indicated here.
	
	<br>

1.  On the `CALCULATOR-APP TAB`:  Verify that the foreground color is already blue.

	<br>
	
####Update your Work Progress

1.  On the `DEVOPS-AGILE TAB`: On the left pane, click the `MY WORK` link.
 
1.  On the `DEVOPS-AGILE TAB`: Click the foreground defect to update its progress.

1.  On the `DEVOPS-AGILE TAB`: Change the status `In Progress` to `Resolve`.

1.  On the `DEVOPS-AGILE TAB`: In the `DISCUSSION` text area, enter `added the <font> and </font> tags to make the foreground color blue`.

1.  On the `DEVOPS-AGILE TAB`: Click the `SAVE` button.


	<br>

####Add members to your Bluemix DevOps Project

In the activity below, you need to have a teammate with a Bluemix DevOps account.

1. On the `DEVOPS-AGILE TAB`: In the menu, click `MY PROJECTS`.

1. On the `DEVOPS-AGILE TAB`: Click the `<username>|devops-delivery-pipeline` project.

1. On the `DEVOPS-AGILE TAB`: Click the `Invite others to join your project` link.

1. On the `DEVOPS-AGILE TAB`: Enter the Bluemix DevOps acount (e-mail address) of your teammate.  Click the `INVITE` button.

1. Ask your teammate to:
- login to his/her Bluemix DevOps account
- click `MY PROJECTS`
- click `INVITATIONS`
- click `ACCEPT`
- click `MY PROJECTS`
- verify if project you shared is already in his/her project list.

	<br>
	
####Delete your Bluemix Application

1. Delete the Bluemix application that was created in this tutorial.

	This will free up some resources which is essential to accommodate new applications and services you want to deploy in the future.


	<br>

1. You may close all the browser tabs you have opened.
	
	<br>

####End of Tutorial

Go back to the [List of Tutorials](/tutorial-list).

####What's next?

Coming Soon


