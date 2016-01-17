---
layout: post
title: GitHub Basics
permalink: /github-basics/
---

##Application Development Tutorial

###GitHub Basics
[GitHub](https://github.com) is a Git repository hosting system that can be used as remote Git repository.

In the [Git Basics Tutorial](/git-basics) , you learned to do version control in a local Git repository (i.e., repository in your hard drive).  This allows you to go back to a previous version of your work.  However, using only a local repository prevents you to collaborate with a teammate.  For example, if you are working on  a Java code `Module1.java` and your teammate is working on `Module2.java`, the typical way of consolidating your work is copying through a USB drive or sending your code as an e-mail.

In this tutorial, you will learn how to use GitHub as a remote Git repository in order for you to share your work with a teammate.


>**Prerequisite:**

>You are **required** to do the [Creating a Web Application using Gradle Tutorial](/gradle-web-application).

>- The sample code used in the current tutorial is based from the sample code used in [Creating a Web Application using Gradle Tutorial](/gradle-web-application). 

>You are not required (but **recommended**) to do  the [Bluemix Basics Tutorial](/bluemix-basics).

>- **However**, ensure that you have a Bluemix account.  
>- Your account should have the space `dev` under the region `US-South`.  The creation of the space `dev` is discussed in [Bluemix Basics Tutorial](/bluemix-basics).

>XXXYou are not required (but **recommended**) to do  the [Bluemix DevOps Services Basics Tutorial](/devops-basics).

>- **However**, ensure that you have a Bluemix DevOps Services account.

>XXXYou are not required (but **recommended**) to do  the [GitHub Basics Tutorial](/github-basics).

>- **However**, ensure that you have a GitHub account.


<br>


####Create a GitHub Account
1. Go to [GitHub](https://github.com) and click the `SIGN UP` button.

1. Fill-up and submit the registration form.

1. Wait for a confirmation e-mail and follow the instructions in the e-mail to validate your GitHub registration.

<br>

####Explore your GitHub Account

1. Open a web browser and login to your [GitHub](https://github.com) account.

1. You will be redirected to your homepage.  Your homepage lists the available repositories in your account.  At this point you don't have any repository.
	
	
	There are two ways to create a repository in GitHub:
	- create a new repository from scratch
	- fork an existing repository

	You will try both approaches in this tutorial.


####Create a New Repository from Scratch

1. Click the `New repository` button.  

1. In the `Create a new repository` page enter the following values:

	||||
	|---|---|---|
	| **Repository name** | myfirstrepo |
	| **Type** | Public |
	| **Initialize this repository with a README** | checked |

1. Click the `Create repository` button.

1. You will be redirected to your `myfirstrepo` repository.  Currently, the repository contains a single file: `README.md`.

	You may add new files and edit existing files using the GitHub interface.  This tutorial will not cover the procedure to accomplish this.

1. Take note of the Git URL of your `myfirstrepo`.  In GitHub, the Git URL follows the following format:

	```text
	https://github.com/<username>/<repository_name>.git
	```

	**Example:**
	```text
	https://github.com/pong/myfirstrepo.git
	```
	>**IMPORTANT:** The example above is the Git URL of another user.  Make sure to take note the URL of your `myfirstrepo`.

	The Git URL is important to sync your local repository (i.e., the one in your hard drive)  and your remote repository (e.g., `myfirstrepo`).

1. Open a terminal window.  Create the directory `gittemp` in the root directory.  Go to the created directory.

	```text
	> mkdir gittemp
	> cd gittemp
	```

1. Clone the git repository `https://github.com/<username>/myfirstrepo.git` and go to the created directory.

	```text
	> git clone https://github.com/<username>/myfirstrepo.git localrepo-one
	> cd localrepo-one
	```
 
 	**Example:**
	```text
	> git clone https://github.com/pong/myfirstrepo.git localrepo-one
	> cd localrepo-one
	```
	>**IMPORTANT:** As mentioned earlier, the example above is the Git URL of another user.  Make sure to use the URL of your `myfirstrepo`.

	**Output:**
	```text
	Cloning into 'localrepo-one'...
	remote: Counting objects: 3, done.
	remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
	Unpacking objects: 100% (3/3), done.
	Checking connectivity... done.
	```

	You have copied the contents of your remote repository `myfirstrepo` to a local repository (i.e., the `localrepo-one` directory in your hard drive).  In the `git clone` command, if you omit the parameter `localrepo-one`, the directory that will be created will have he same name as the remote repository (i.e., `myfirstrepo`).  In this tutorial, we intentionally specified the parameter `localrepo-one` so that the name of the remote repository (`myfirstrepo`)  and local repository (`localrepo-one`) are different.

1. Update `README.md` to the following:

	```text
	# myfirstrepo
	Hello GitHub!
	```

	<br>

1. Create a file `sample.txt` in `localrepo-one` directory containing the following value:

	```text
	This is just a sample text file.
	```

	<br>


1. Track and commit the changes made in the local repository.

	```text
	> git add README.md sample.txt
	> git commit -m "updated README.md and created sample.txt"
	```

	**Output:**

	```text
	[master 671b491] updated README.md and created sample.txt
	 2 files changed, 3 insertions(+), 1 deletion(-)
	 create mode 100644 sample.txt
	```	
	<br>

	At this point, the changes made (i.e., updated the `README.md` file and created the `sample.txt text file`) are committed in your local repository.  However, the local repository is not synced with the remote repository `myfirstrepo`.  

1. Go back to your web browser and refresh your page to confirm that `README.md` has not been updated and `sample.txt` is not yet created in the remote repository`myfirstrepo`.

1. Verify that the Git URL of your remote repository is declared in your local repository.

	```text
	> git remote -v
	```
	
	**Output:**
	```text
	origin  https://github.com/<username>/myfirstrepo.git (fetch)
	origin  https://github.com/<username>/myfirstrepo.git (push)
	```
	
	As shown in the output above, your local repository is aware of the Git URL of your remote repository.  The name `origin` is used to refer to the Git URL (e.g., instead of mentioning the very long Git URL `https://github.com/<username>/myfirstrepo.git`, you may just refer to it as `origin`).

	Note that the declaration of having the name `origin` associated with the Git URL `https://github.com/<username>/myfirstrepo.git` was automatically done when you did a `git clone` earlier.  The name `origin` can be changed to something else but in this tutorial you will retain this name.

1. Sync the contents of the local repository to the remote repository.


	```text
	> git push origin master
	```
	
	**Output:**
	```text
	Username for 'https://github.com': <username>
	Password for 'https://<username>@github.com':
	Counting objects: 6, done.
	Delta compression using up to 4 threads.
	Compressing objects: 100% (2/2), done.
	Writing objects: 100% (4/4), 375 bytes | 0 bytes/s, done.
	Total 4 (delta 0), reused 0 (delta 0)
	```

	The command `git push` is used because you did some modifications in the local repository (i.e., updated `README.md` and created `sample.txt`) and you want to push these changes to your `remote repository`.

	As discussed earlier, `origin` refers to the Git URL `https://github.com/<username>/myfirstrepo.git`.   The name `master` refers to the `master` branch in your  remote repository`myfirstrepo`.  A repository may have one or more branch.  By default, a repository has only one branch named `master`.   That is why your remote repository `myfirstrepo` has a `master` branch even if you never explicitly created it.  You may look at your GitHub page to verify that there is indeed a branch named `master` under the remote repository `myfirstrepo`.  This tutorial does not cover the creation of additional branches.

	The command `git push origin master` pushes the changes of your local repository to the `master` branch of the remote repository referred to by origin (which is `https://github.com/<username>/myfirstrepo.git`).

	<br>
	
1. Go back to your web browser and refresh your page to confirm that `README.md` has been updated and `sample.txt` already exist in the remote repository`myfirstrepo`.

	<br>
	
####Fork an Existing Repository

As mentioned earlier, there are two ways to create a repository.  Either create a new repository from scratch (which is the activity you did in the previous steps) or you fork an existing repository.  In the task below, you will now create your second remote repository by forking an existing one.

1. Go back to your browser and go to the URL:
		`https://github.com/pong-pantola/mysecondrepo`

		Take note that you do not own this repository.  It is owned by user `pong-pantola`.  This can be verified through to the text `pong-pantola/mysecondrepo` found on the webpage.

1. Click the `Fork` button.

		You know have your own copy of `mysecondrepo`.  This can be verified through to the text `pantolav/mysecondrepo` followed by `forked from pong-pantola/mysecondrepo`.

	Forking allows you to make a copy of an existing repository and make it independent from the said existing repository.  If you start making changes to your forked repository, it will affect only this repository.



1. Take note of the Git URL of your `mysecondrepo`.  

	```text
	https://github.com/<username>/mysecondrepo.git
	```


1. Open another terminal window.  Go to the `gittemp` directory.

	```text
	> cd gittemp
	```

1. Create the directory `localrepo-two` and go to the created directory.

	```text
	> mkdir localrepo-two
	> cd localrepo-two
	```

	Recall that you previously created the local repository `localrepo-one` by issuing the command `git clone https://github.com/<username>/myfirstrepo.git localrepo-one`.  You could have done the same thing with `localrepo-two`.  However, we want to discuss an alternative technique in syncing with a remote repository.

	<br>
	
1. Make the `localrepo-two` a local repository.

	```text
	> git init
	```
	
	**Output:**
	
	```text
	Initialized empty Git repository in D:/gittemp/localrepo-two/.git/
	```

	The `git init` command creates a hidden `.git` subdirectory in the directory `localrepo-two`.  This makes the `localrepo-two` a Git repository.



1. Create a file `anothersample.txt` in `localrepo-two` directory containing the following value:

	```text
	This is just a ANOTHER sample text file.
	```

	<br>


1. Track and commit the changes made in the local repository.

	```text
	> git add anothersample.txt
	> git commit -m "created anothersample.txt"
	```

	**Output:**

	```text
	[master (root-commit) e6f6dbb] created anothersample.txt
	 1 file changed, 1 insertion(+)
	 create mode 100644 anothersample.txt
	```	
	<br>

	At this point, the changes made (i.e., created the `anothersample.txt text file`) are committed in your local repository.  However, the local repository is not synced with the remote repository `mysecondrepo`.  

1. Go back to your web browser and refresh your page to confirm that `anothersample.txt` is not yet created in the remote repository`mysecondrepo`.

1. Verify if the Git URL of your remote repository is declared in your local repository

	```text
	> git remote -v
	```
	
	**Output:**
	```text

	```

	The output of the command is blank.  Recall that when you issued the same command in the `localrepo-one` repository, the output is not blank.  It states that the following declaration:

	```text
	origin  https://github.com/<username>/myfirstrepo.git (fetch)
	origin  https://github.com/<username>/myfirstrepo.git (push)
	```
	Note that the `localrepo-one` repository was created when you issued the `git clone https://github.com/<username>/myfirstrepo.git localrepo-one` command earlier.  The `git clone` command did not only created the `localrepo-one` repository but also did the necessary declaration to map the name `origin` to the Git URL `https://github.com/<username>/myfirstrepo.git`.

	However, in the case of `localrepo-two`, this repository was created by manually creating the directory `localrepo-two` and issuing the command `git init` inside it.  Therefore, `localrepo-two` is not even aware of the existence of the remote repository `mysecondrepo` nor its Git URL `https://github.com/<username>/mysecondrepo.git`.

	You need to explicitly inform the local repository `localrepo-two` of the remote repository `mysecondrepo`.

1. Make the localrepo-two `localrepo-two` aware of the remote repository `mysecondrepo`.

	```text
	git remote add origin https://github.com/<username>/mysecondrepo.git
	```

	**Example:**
	```text
	git remote add origin https://github.com/pong/mysecondrepo.git
	```
	>**IMPORTANT:** The example above uses the Git URL of another user.  Make sure to use the URL of your `mysecondrepo`.

1. Verify that the Git URL of your remote repository is already declared in your local repository.

	```text
	> git remote -v
	```
	
	**Output:**
	```text
	origin  https://github.com/<username>/mysecondrepo.git (fetch)
	origin  https://github.com/<username>/mysecondrepo.git (push)
	```

1. Sync the contents of the local repository to the remote repository.


	```text
	> git push origin master
	```
	
	**Output:**
	```text
	Username for 'https://github.com': <username>
	Password for 'https://<username>@github.com':
	To https://github.com/<username>/mysecondrepo.git
	 ! [rejected]        master -> master (fetch first)
	error: failed to push some refs to 'https://github.com/<username>/mysecondrepo.git
	'
	hint: Updates were rejected because the remote contains work that you do
	hint: not have locally. This is usually caused by another repository pushing
	hint: to the same ref. You may want to first integrate the remote changes
	hint: (e.g., 'git pull ...') before pushing again.
	hint: See the 'Note about fast-forwards' in 'git push --help' for details.
	```


	Unlike the `git push` command you issued to sync the contents of `localrepo-one` with the remote repository `myfirstrepo` in an earlier task, the `git push` command above encountered an error.

	The intention of a `git push` command is to make the contents of the local repository the same as the remote repository.  If `git push` detects that proceeding with the push will not result to a local and remote repositories that are synced, it will not proceed with the push.  This is what happened with your attempt to push the changes in `localrepo-two` to the remote repository `mysecondrepo`.

	Note that the remote repository `mysecondrepo` contains the file `README.md` while `localrepo-two` contains the file `anothersample.txt`.  A `git push` command would have copied `anothersample.txt` to `mysecondrepo`. This is summarized below:

	Repository | Contents Before the Push | Contents After the Push (if push will be allowed to proceed)
	---|---|---
	`localrepo-two` | `anothersample.txt` |  `anothersample.txt`
	`mysecondrepo` | `README.md` | `anothersample.txt` and `README.md`

	Proceeding with the push will not result to synced `mysecondrepo` and `localrepo-two`.  This is the reason why the `git push` command resulted to an error.

	To solve this problem, a `git pull` command will be performed first.

1. Pull the contents of the remote repository to the  local repository.


	```text
	> git pull origin master
	```
	
	**Output:**
	```text
	warning: no common commits
	remote: Counting objects: 3, done.
	remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
	Unpacking objects: 100% (3/3), done.
	From https://github.com/pantolav/mysecondrepo
	 * branch            master     -> FETCH_HEAD
	 * [new branch]      master     -> origin/master
	Merge made by the 'recursive' strategy.
	 README.md | 1 +
	 1 file changed, 1 insertion(+)
	 create mode 100644 README.md
	```

	The `git pull` command checks files in the remote repository that are missing or different from the local repository.  Those that are missing will be copied, while those that are different will be merged (or attempted to be merged) by `git pull`.

	The remote repository `mysecondrepo` has a `README.md` file that is missing in the local repository `localrepo-two`.  A pull will copy the `README.md` file the local repository.  This is summarized below:

	Repository | Contents Before the Pull | Contents After the Pull
	---|---|---
	`localrepo-two` | `anothersample.txt` |  `anothersample.txt` and `README.md`
	`mysecondrepo` | `README.md` | `README.md`

	Note that a `git pull` command does not require that the local and remote repositories to be synced with each other.  It only ensures that files in the remote repository that are missing or different from the local repository is copied/merged to the local repository.

1. Go back to your web browser and refresh your page to confirm that the remote repository `mysecondrepo` still contains only the `README.md` file.  At this point, `anothersample.txt` should still not exist in the remote repository.

1. Try to sync again the contents of the local repository to the remote repository.


	```text
	> git push origin master
	```
	
	**Output:**
	```text
	Username for 'https://github.com': <username>
	Password for 'https://<username>@github.com':
	Counting objects: 6, done.
	Delta compression using up to 4 threads.
	Compressing objects: 100% (3/3), done.
	Writing objects: 100% (5/5), 588 bytes | 0 bytes/s, done.
	Total 5 (delta 0), reused 0 (delta 0)
	To https://github.com/<username>/mysecondrepo.git
	   125720e..86cb740  master -> master	
	```

	Repository | Contents Before the Push | Contents After the Push
	---|---|---
	`localrepo-two` |  `anothersample.txt` and `README.md` | `anothersample.txt` and `README.md`
	`mysecondrepo` | `README.md` | `anothersample.txt` and `README.md`


	<br>

1. Go back to your web browser and refresh your page to confirm that aside from `README.md`, the remote repository `mysecondrepo` now contains `anothersample.txt`.

	<br>

####Sharing a Remote Repository
Syncing the contents of a local repository to a remote repository is an effective way of creating a back up of your source code.  However, sharing a remote repository to teammates allow you to easily consolidate your team's work.  In the next activity, you will work with another person.  One of you will be **Person A** (the one who will share the repository) and the other one is **Person B**.

>**IMPORTANT:** 
>Each step is labeled as **Person A**, **Person B**, or **Both** to know who should be performing a particular step.  Note that even if two steps are assigned to different persons, it does not mean that they can be performed in parallel.  For example, if step X is for **Person A** and step Y is for **Person B**, **Person B** should wait for **Person A** to finish step X before **Person B** performs step Y.


1. **Person A:** On your web browser, create a new remote repository with the following specification:

	||||
	|---|---|---|
	| **Repository name** | myfirstrepo |
	| **Type** | Public |
	| **Initialize this repository with a README** | checked |

	<br>
	
1. **Both:** Open another terminal window. Go to the `gittemp` directory.

	```text

	> cd gittemp
	```

	<br>
	
1. **Both:** Clone the git repository `https://github.com/<username_of_Person_A>/mysharedrepo.git` and go to the created directory.

	```text
	> git clone https://github.com/<username_of_Person_A>/mysharedrepo.git localrepo-three
	> cd localrepo-three
	```
 
 	**Example:**
	```text
	> git clone https://github.com/usera/mysharedrepo.git localrepo-three
	> cd localrepo-three
	```
	>**IMPORTANT:** The example above is the Git URL of another user.  Make sure to use the URL of **Person A**'s `mysharedrepo`.  Even **Person B** should use the URL of **Person A**'s `mysharedrepo`.

	**Output:**
	```text
	Cloning into 'localrepo-three'...
	remote: Counting objects: 3, done.
	remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
	Unpacking objects: 100% (3/3), done.
	Checking connectivity... done.
	```

	<br>



1. **Person A:** Create a file `contribution-a.txt` in `localrepo-three` directory containing the following value:

	```text
	This is the contribution of Person A.  This represents a source code written by Person A.
	```

	<br>


1. **Person A:** Track and commit the changes made in the local repository.

	```text
	> git add contribution-a.txt
	> git commit -m "created contribution-a.txt"
	```

	**Output:**

	```text
	[master 83d407a] created contribution-a.txt
	 1 file changed, 1 insertion(+)
	 create mode 100644 contribution-a.txt
	```	
	<br>


1. **Person A:** Sync the contents of the local repository to the remote repository.


	```text
	> git push origin master
	```
	
	**Output:**
	```text
	Username for 'https://github.com': <username_of_Person_A>
	Password for 'https://<username_of_Person_A>@github.com':
	Counting objects: 4, done.
	Delta compression using up to 4 threads.
	Compressing objects: 100% (3/3), done.
	Writing objects: 100% (3/3), 377 bytes | 0 bytes/s, done.
	Total 3 (delta 0), reused 0 (delta 0)
	To https://github.com/<username_of_Person_A>/mysharedrepo.git
	   cb74f88..83d407a  master -> master
	```


1. **Person B:** Create a file `contribution-b.txt` in `localrepo-three` directory containing the following value:

	```text
	This is the contribution of Person B.  This represents a source code written by Person B.
	```

	<br>


1. **Person B:** Track and commit the changes made in the local repository.

	```text
	> git add contribution-b.txt
	> git commit -m "created contribution-b.txt"
	```

	**Output:**

	```text
	[master d0d039d] created contribution-b.txt
	 1 file changed, 1 insertion(+)
	 create mode 100644 contribution-b.txt
	```	
	<br>


1. **Person B:** Sync the contents of the local repository to the remote repository.


	```text
	> git push origin master
	```
	
	**Output:**
	
	```text
	Username for 'https://github.com': <username_of_Person_B>
	Password for 'https://<username_of_Person_B>@github.com':
	remote: Permission to <username_of_Person_A>/mysharedrepo.git denied to <username_of_Person_B.>
	fatal: unable to access 'https://github.com/<username_of_Person_A>/mysharedrepo.git/': The requested URL returned error: 403
	```

	Unlike **Person A**, **Person B** encountered an `unable to access` error.  Recall that both **Person A** and **Person B** cloned the remote repository `mysharedrepo` of **Person A**.

	When **Person A** issued the `git push` command to push its update to the remote repository `mysharedrepo` of **Person A** this does not cause any problem since **Person A** has access to its remote repository.

	However, when **Person B** issued the `git push` command to push its update to the remote repository `mysharedrepo` of **Person A**, an error is encountered because **Person B** is not given any authorization to push updates to **Person A**'s remote repository.

1. **Person A:** Give permission to **Person B** to push updates to the remote repository `mysharedrepo`.  Go to the web browser and make sure that you are in the `mysharedrepo` repository.

1. **Person A:** Click the `Settings` link.  Click the `Collaborators` link.  Confirm your password.

1. **Person A:** In the text box, type the username of **Person B** and click the `Add Collaborator` button.


1. **Person B:** Try again to sync the contents of the local repository to the remote repository.


	```text
	> git push origin master
	```
	
	**Output:**
	
	```text
	Username for 'https://github.com': <username_of_Person_B>
	Password for 'https://<username_of_Person_B>@github.com':
	To https://github.com/<username_of_Person_A>/mysharedrepo.git
	 ! [rejected]        master -> master (fetch first)
	error: failed to push some refs to 'https://github.com/<username_of_Person_A>/mysharedrepo.git
	'
	hint: Updates were rejected because the remote contains work that you do
	hint: not have locally. This is usually caused by another repository pushing
	hint: to the same ref. You may want to first integrate the remote changes
	hint: (e.g., 'git pull ...') before pushing again.
	hint: See the 'Note about fast-forwards' in 'git push --help' for details.
	```

	The `unable to access` error does not anymore appear.  This means that **Person B** is already given authorization to push updates to **Person A**'s remote repository.  However, the error message encountered in the previous activity.  This is due to to a `git push` will not sync the local repository of **Person B** and the remote repository of **Person A**.  Note that the remote repository already has `contribution-a.txt` which is still missing in **Person B**'s local repository.  This is summarized below:

	Repository | Contents Before **Person B**'s Push | Contents After **Person B**'s Push (if push will be allowed to proceed)
	---|---|---
	`localrepo-three` of **Person A** | `contribution-a.txt` and `README.md` |  `contribution-a.txt` and `README.md`
	`localrepo-three` of **Person B** | `contribution-b.txt` and `README.md` |  `contribution-b.txt` and `README.md`
	`mysharedrepo` of **Person A** | `contribution-a.txt` and `README.md` | `contribution-a.txt`, `contribution-b.txt`, and `README.md`

	Note that the push is not allowed because the local repository of **Person B** will not be synced with the remote repository of **Person A**.

	This can easily be solved by **Person B** by doing a pull followed by a push.


	<br>

1. **Person B:** Pull the contents of the remote repository to the  local repository.


	```text
	> git pull origin master
	```
	
	**Output:**
	```text
	remote: Counting objects: 3, done.
	remote: Compressing objects: 100% (3/3), done.
	remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
	Unpacking objects: 100% (3/3), done.
	From https://github.com/<username_of_Person_A>/mysharedrepo
	 * branch            master     -> FETCH_HEAD
	   cb74f88..83d407a  master     -> origin/master
	Merge made by the 'recursive' strategy.
	 contribution-a.txt | 1 +
	 1 file changed, 1 insertion(+)
	 create mode 100644 contribution-a.txt
	```

	The repositories' contents after the pull are the following:
	
	Repository | Contents Before **Person B**'s Pull | Contents After **Person B**'s Pull
	---|---|---
	`localrepo-three` of **Person A** | `contribution-a.txt` and `README.md` |  `contribution-a.txt` and `README.md`
	`localrepo-three` of **Person B** | `contribution-b.txt` and `README.md` |  `contribution-a.txt`, `contribution-b.txt`, and `README.md`
	`mysharedrepo` of **Person A** | `contribution-a.txt` and `README.md` | `contribution-a.txt`  and `README.md`
	

	<br>

1. **Person B:** Try again to sync the contents of the local repository to the remote repository.


	```text
	> git push origin master
	```
	
	**Output:**
	
	```text
	Username for 'https://github.com': <username_of_Person_B>
	Password for 'https://<username_of_Person_B>@github.com':
	Counting objects: 7, done.
	Delta compression using up to 4 threads.
	Compressing objects: 100% (5/5), done.
	Writing objects: 100% (5/5), 647 bytes | 0 bytes/s, done.
	Total 5 (delta 1), reused 0 (delta 0)
	To https://github.com/<username_of_Person_A>/mysharedrepo.git
	   83d407a..95b2e65  master -> master
	```

	The repositories' contents after the pull are the following:
	
	Repository | Contents Before **Person B**'s Push | Contents After **Person B**'s Push
	---|---|---
	`localrepo-three` of **Person A** | `contribution-a.txt` and `README.md` |  `contribution-a.txt` and `README.md`
	`localrepo-three` of **Person B** | `contribution-a.txt`, `contribution-b.txt`, and `README.md` |  `contribution-a.txt`, `contribution-b.txt`, and `README.md`
	`mysharedrepo` of **Person A** | `contribution-a.txt` and `README.md` | `contribution-a.txt`,  `contribution-b.txt`, and `README.md`
	
	The local repository of **Person B** and the remote repository of **Person A** are now synced.  However, **Person A**'s local repository is not synced with the remote repository.  This can easily be solved with another pull from **Person A**.
	<br>

1. **Person A:** Pull the contents of the remote repository to the  local repository.


	```text
	> git pull origin master
	```
	
	**Output:**
	```text
	remote: Counting objects: 5, done.
	remote: Compressing objects: 100% (4/4), done.
	remote: Total 5 (delta 1), reused 5 (delta 1), pack-reused 0
	Unpacking objects: 100% (5/5), done.
	From https://github.com/<username_of_Person_A>/mysharedrepo
	 * branch            master     -> FETCH_HEAD
	   83d407a..95b2e65  master     -> origin/master
	Updating 83d407a..95b2e65
	Fast-forward
	 contribution-b.txt | 1 +
	 1 file changed, 1 insertion(+)
	 create mode 100644 contribution-b.txt
	```

	The repositories' contents after the pull are the following:
	Repository | Contents Before **Person A**'s Pull | Contents After **Person A**'s Pull
	---|---|---
	`localrepo-three` of **Person A** | `contribution-a.txt` and `README.md` |  `contribution-a.txt`, `contribution-b.txt`, and `README.md`
	`localrepo-three` of **Person B** | `contribution-a.txt`, `contribution-b.txt`, and `README.md` |  `contribution-a.txt`, `contribution-b.txt`, and `README.md`
	`mysharedrepo` of **Person A** | `contribution-a.txt` and `README.md` | `contribution-a.txt`,  `contribution-b.txt`, and `README.md`
	
	The two local repositories and the remote repository are now synced.

	<br>
	
####Merge Changes Made on the same file
xxx
	The command `git push` is used because you did some modifications in the local repository (i.e., updated `README.md` and created `sample.txt`) and you want to push these changes to your `remote repository`.

	As discussed earlier, `origin` refers to the Git URL `https://github.com/<username>/myfirstrepo.git`.   The name `master` refers to the `master` branch in your  remote repository`myfirstrepo`.  A repository may have one or more branch.  By default, a repository has only one branch named `master`.   That is why your remote repository `myfirstrepo` has a `master` branch even if you never explicitly created it.  You may look at your GitHub page to verify that there is indeed a branch named `master` under the remote repository `myfirstrepo`.  This tutorial does not cover the creation of additional branches.

	The command `git push origin master` pushes the changes of your local repository to the `master` branch of the remote repository referred to by origin (which is `https://github.com/<username>/myfirstrepo.git`).

	<br>
	
1. Go back to your web browser and refresh your page to confirm that `README.md` has been updated and `sample.txt` already exist in the remote repository`myfirstrepo`.

	<br>



####Install a Git Client


1. Go to [Git](https://git-scm.com/).

1. Download the Git client installer and install.

1. Test if the Git client is installed successfully.  Open a terminal window.

	```text
	> git
	```
	**Output:**

	```text
	usage: git [--version] [--help] [-C <path>] [-c name=value]
	           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
	           [-p|--paginate|--no-pager] [--no-replace-objects] [--bare]
	           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
	           <command> [<args>]
	
	The most commonly used git commands are:
	   add        Add file contents to the index
	   bisect     Find by binary search the change that introduced a bug
	   :
	   :
	```

	You should see the help screen of the Git client.

	<br>
	
####Create several text files and use Git to manage the versions of the files

In this tutorial, you will be creating several `.txt` files that will contain a list of words representing each letter of the alphabet.  The use of this approach will help you understand how Git works.  Once you are familiar with Git, you may use Git with your source code (e.g., `.java` file).

1. Create the directory `gittemp` in the root directory.  Go to the created directory.

	```text
	> mkdir gittemp
	> cd gittemp
	```

1. Create the subdirectory `alphabet` in the `gittemp` directory.  Go to the created directory.

	```text
	> mkdir alphabet
	> cd alphabet
	```

	The `alphabet` directory represents a working directory containing your source code.  As mentioned earlier, instead of source code, text files will be used in this tutorial.

	<br>
	
1. Make the `alphabet` directory a local Git repository.

	```text
	> git init
	```

	**Output:**

	```text
	Initialized empty Git repository in /gittemp/alphabet/.git/
	```

	A hidden directory named `.git` is created after you issued the `git init` command.  You should not modify the contents of the `.git` hidden directory.  This contains information that will track the changes you made inside the `alphabet` directory.

	<br>


1. Check the status of your local Git repository.

	```text
	> git status
	```

	**Output:**

	```text
	On branch master
	
	Initial commit
	
	nothing to commit (create/copy files and use "git add" to track)
	```

	As stated in the status, there is `nothing to commit`.  This will change once you start creating files.

	<br>
	
1. Create a file `animal.txt` in the `alphabet` directory with the following contents:

	```text
	ant
	bat
	cat
	dog
	eagle
	fox
	goat
	horse
	```

	<br>
	
1. Check the status of your local Git repository.

	```text
	> git status
	```

	**Output:**

	```text
	On branch master
	
	Initial commit
	
	Untracked files:
	  (use "git add <file>..." to include in what will be committed)
	
	        animal.txt
	
	nothing added to commit but untracked files present (use "git add" to track)
	```

	Git detected the `animal.txt` file that you created.  However, it is currently untracked by Git.  Untracked files are those in the working directory but are NOT in index.

	Git does not track all the files you created since it is possible that some of the files are non-essential.  You need to explicitly tell Git to track a file.

	<br>
	
1. Let Git track `animal.txt`.

	```text
	> git add animal.txt
	```

	>If there are multiple files that you want Git to track, you may use the same `git add` command and just separate the files with a `space`.

	The `git add animal.txt` command places the `animal.txt` in the index.  Those files in the index are staged. Staging means that a file is being prepared to be committed. 

	<br>
	
1. Check the status of your local Git repository.

	```text
	> git status
	```

	**Output:**

	```text
	On branch master
	
	Initial commit
	
	Changes to be committed:
	  (use "git rm --cached <file>..." to unstage)
	
	        new file:   animal.txt
	```

	At this point, `animal.txt` is already in index and being tracked by Git.  However, changes made in `animal.txt` is not yet committed.

	<br>

1. Commit the changes made in `animal.txt`.

	```text
	> git commit -m "added words from ant to horse"
	```

	**Output:**

	```text
	[master (root-commit) 828389d] added words from ant to horse
	 1 file changed, 8 insertions(+)
	 create mode 100644 animal.txt
	```
	
	Note that if there are other files that are staged aside from `animal.txt`, the changes made in those files will also be committed.

	<br>
	
1. Check the status of your local Git repository.

	```text
	> git status
	```

	**Output:**

	```text
	On branch master
	nothing to commit, working directory clean
	```

	At this point,  changes made in `animal.txt` are committed.  In the `git commit` command, you included a message `added words from ant to horse` to give a short description on what changes were committed.  This is very useful when you perform several commits later and you want to undo previous commits.

	<br>

1. Visually look at the the details regarding the commit you performed.

	```text
	> gitk
	```

	**Output:**

	```text
	*master added words from ant to horse
	```	

	`gitk` is a tool which allows you to visualize the commits you performed.  You may use `gitk` as a guide when you need to undo previous commits.
	
	<br>

1. Update `animal.txt` to include words `iguana` to `pig`:

	```text
	ant
	bat
	cat
	dog
	eagle
	fox
	goat
	horse
	iguana
	jaguar
	kangaroo
	lion
	monkey
	newt
	octopus
	pig
	```

	<br>
	
1. Track and commit the changes made in `animal.txt`.

	```text
	> git add animal.txt
	> git commit -m "added words from iguana to pig"
	```

	**Output:**

	```text
	[master 5394740] added words from iguana to pig
	 1 file changed, 9 insertions(+), 1 deletion(-)
	```	
	
	<br>

1. Update `animal.txt` to include words `quail` to `zebra`.  In addition, delete `dog` and change `monkey` to `mouse`:

	```text
	ant
	bat
	cat
	eagle
	fox
	goat
	horse
	iguana
	jaguar
	kangaroo
	lion
	mouse
	newt
	octopus
	pig
	quail
	rabbit
	snail
	tiger
	uakari
	vulture
	wolf
	x-ray tetra
	yak
	zebra
	```

	<br>
	
1. Track and commit the changes made in `animal.txt`.

	```text
	> git add animal.txt
	> git commit -m "added words from quail to zebra, deleted dog, and changed monkey to mouse"
	```

	**Output:**

	```text
	[master f1fbe3c] added words from quail to zebra, deleted dog, and changed monkey to mouse
	 1 file changed, 12 insertions(+), 3 deletions(-)
	```	
	
	<br>




####Checkout Previous Commits

Checking out previous commits allows you to inspect the state of the files after a particular commit.  This is done by changing back the contents of the working directory.  However, the latest committed changes remain intact.

1. Get a summary of the commits performed in the local Git repository.

	```text
	> git log
	```

	**Output:**

	```text
	commit f1fbe3cfccfa0343f0b4ffe0d9c35967174b5f77
	Author: Alexis V. Pantola <pantolav@gmail.com>
	Date:   Sun Jan 10 23:32:48 2016 +0800
	
	    added words from quail to zebra, deleted dog, and changed monkey to
	commit 539474028f1a73dcb01111ce79eefa4a50a31baf
	Author: Alexis V. Pantola <pantolav@gmail.com>
	Date:   Sun Jan 10 23:31:45 2016 +0800
	
	    added words from iguana to pig
	
	commit 828389d84eedf01b1ca4fa842c879139bc8e62b5
	Author: Alexis V. Pantola <pantolav@gmail.com>
	Date:   Sun Jan 10 23:29:40 2016 +0800
	
	    added words from ant to horse
	```

	>**NOTE**: You may press `Q` to exit the log console.

	Notice that the three commits performed earlier are listed in the log.  In addition, there are unique hash values identifying each commit.  As an example, in the log above, the commit `added words from ant to horse` has a hash value of `828389d84eedf01b1ca4fa842c879139bc8e62b5`.  Note that the hash value in your repository is not necessarily the same as the one shown in this tutorial.

	The hash value is important to undo previous commits and go to a particular state of a file.

1. Inspect the state of the file when the words ant to horse has just been added.

	```text
	> git checkout <hash of commit for "added words from ant to horse">
	```

	**Example:**

	```text
	> git checkout 828389d84eedf01b1ca4fa842c879139bc8e62b5
	```


	**Output:**

	```text
	Note: checking out '828389d84eedf01b1ca4fa842c879139bc8e62b5'.

	You are in 'detached HEAD' state. You can look around, make experimental
	changes and commit them, and you can discard any commits you make in this
	state without impacting any branches by performing another checkout.
	
	If you want to create a new branch to retain commits you create, you may
	do so (now or later) by using -b with the checkout command again. Example:
	
	  git checkout -b new_branch_name
	
	HEAD is now at 828389d... added words from ant to horse
	```

	<br>
	
1. Open (or reload) `animal.txt`and verify that its content is now the following:

	```text
	ant
	bat
	cat
	dog
	eagle
	fox
	goat
	horse
	```

	As expected,  you went back to the state  when the words ant to horse has just been added to `animal.txt`.
	
	<br>
	
1. Check the contents of the log.

	```text
	> git log
	```

	**Output:**

	```text
	commit 828389d84eedf01b1ca4fa842c879139bc8e62b5
	Author: Alexis V. Pantola <pantolav@gmail.com>
	Date:   Sun Jan 10 23:29:40 2016 +0800
	
	    added words from ant to horse
	```

	Notice that the log has only one commit.

	<br>



1. Go back to the last commit you made (i.e., `added words from quail to zebra, deleted dog, and changed monkey to mouse`).

	```text
	> git checkout master
	```


	**Output:**

	```text
	Previous HEAD position was 828389d... added words from ant to horse
	Switched to branch 'master'
	```

	<br>
	
1. Open (or reload) `animal.txt`and verify that its content is now the following:

	```text
	ant
	bat
	cat
	eagle
	fox
	goat
	horse
	iguana
	jaguar
	kangaroo
	lion
	mouse
	newt
	octopus
	pig
	quail
	rabbit
	snail
	tiger
	uakari
	vulture
	wolf
	x-ray tetra
	yak
	zebra
	```

	As expected, you are able to return to the latest state of the file.

	<br>


####Go back to a particular Commit

The `git checkout` command that was demonstrated above allows you to inspect the state of a file of a particular commit.  However, the latest committed changes remain intact.  In the event that you really want to go back to a particular commit (e.g., you realized that you erroneously changed the contents of a file and want to go back to its correct state), you may use the `git reset` command.

1. Get a summary of the commits performed in the local Git repository.

	```text
	> git log
	```

	**Output:**

	```text
	commit f1fbe3cfccfa0343f0b4ffe0d9c35967174b5f77
	Author: Alexis V. Pantola <pantolav@gmail.com>
	Date:   Sun Jan 10 23:32:48 2016 +0800
	
	    added words from quail to zebra, deleted dog, and changed monkey to
	commit 539474028f1a73dcb01111ce79eefa4a50a31baf
	Author: Alexis V. Pantola <pantolav@gmail.com>
	Date:   Sun Jan 10 23:31:45 2016 +0800
	
	    added words from iguana to pig
	
	commit 828389d84eedf01b1ca4fa842c879139bc8e62b5
	Author: Alexis V. Pantola <pantolav@gmail.com>
	Date:   Sun Jan 10 23:29:40 2016 +0800
	
	    added words from ant to horse
	```

	This is the same log that was shown in the previous steps.

1. Go back to the state of the file when the words ant to horse has just been added.

	```text
	> git reset --hard <hash of commit for "added words from ant to horse">
	```

	**Example:**

	```text
	> git reset --hard 828389d84eedf01b1ca4fa842c879139bc8e62b5
	```


	**Output:**

	```text
	HEAD is now at 828389d added words from ant to horse
	```

	<br>
	
1. Open (or reload) `animal.txt`and verify that its content is now the following:

	```text
	ant
	bat
	cat
	dog
	eagle
	fox
	goat
	horse
	```

	Similar to `git checkout`,  you are able to go back to the state   when the words ant to horse has just been added to `animal.txt` using `git reset`.  You will see later the difference of these two commands.
	
	<br>
	
1. Check the contents of the log.

	```text
	> git log
	```

	**Output:**

	```text
	commit 828389d84eedf01b1ca4fa842c879139bc8e62b5
	Author: Alexis V. Pantola <pantolav@gmail.com>
	Date:   Sun Jan 10 23:29:40 2016 +0800
	
	    added words from ant to horse
	```

	<br>



1. **TRY** to go back to the last commit you made (i.e., `added words from quail to zebra, deleted dog, and changed monkey to mouse`).

	```text
	> git checkout master
	```

	**Output:**

	```text
	Already on 'master'
	```
	Notice that the output is `Already on 'master'`.  This means that you have reset the last commit from `added words from quail to zebra, deleted dog, and changed monkey to mouse` to `added words from ant to horse`.   The `added words from quail to zebra, deleted dog, and changed monkey to mouse`commit as well as the `added words from iguana to pig` commit are already removed.
	
	<br>
	
1. Open (or reload) `animal.txt`and verify that its content is **STILL** ant to horse:

	```text
	ant
	bat
	cat
	dog
	eagle
	fox
	goat
	horse
	```

	<br>
	
####End of Tutorial


####What's next?





