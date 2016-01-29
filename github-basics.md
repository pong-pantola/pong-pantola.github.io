---
layout: post
title: GitHub Basics
permalink: /github-basics/
---


[GitHub](https://github.com) is a Git repository hosting system that can be used as a remote Git repository.

In the [Git Basics Tutorial](/git-basics) , you learned to do version control in a local Git repository (i.e., repository in your hard drive).  This allows you to go back to a previous version of your work.  However, using only a local repository prevents you to collaborate with a teammate efficiently.  For example, if you are working on  a Java code `Module1.java` and your teammate is working on `Module2.java`, the typical way of consolidating your work is copying through a USB drive or sending your code as an e-mail.

In this tutorial, you will learn how to use GitHub as a remote Git repository in order for you to share your work with a teammate.

<br>

>**Prerequisite:**

>You are **required** to do the [Git Basics Tutorial](/git-basics).

>There are activities in this tutorial that require a teammate.  Make sure that you identify another person who will be your teammate in this tutorial.


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

	<br>

####Create a New Repository from Scratch

1. Click the `New repository` button.  

1. In the `Create a new repository` page enter the following values:

	||||
	|---|---|---|
	| **Repository name** | myfirstrepo |
	| **Type** | Public |
	| **Initialize this repository with a README** | checked |

	<br>
	
1. Click the `Create repository` button.

1. You will be redirected to your `myfirstrepo` repository.  Currently, the repository contains a single file: `README.md`.

	You may add new files and edit existing files using the GitHub interface.  This tutorial will not cover the procedure to accomplish this.

	<br>

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

	<br>
	
1. Open a terminal window.  Create the directory `gittemp` in the root directory.  Go to the created directory.

	```text
	> mkdir gittemp
	> cd gittemp
	```

	<br>
	
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

	You have copied the contents of your remote repository `myfirstrepo` to a local repository (i.e., the `localrepo-one` directory in your hard drive).  In the `git clone` command, if you omit the parameter `localrepo-one`, the directory that will be created will have the same name as the remote repository (i.e., `myfirstrepo`).  In this tutorial, we intentionally specified the parameter `localrepo-one` so that the name of the remote repository (`myfirstrepo`)  and local repository (`localrepo-one`) are different.

	<br>
	
1. Update `README.md` in `localrepo-one` to the following:

	```text
	# myfirstrepo
	Hello GitHub!
	```

	<br>

1. Create a file `sample.txt` in `localrepo-one` directory containing the following:

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

	At this point, the changes made (i.e., updated the `README.md` file and created the `sample.txt` text file) are committed in your local repository.  However, the local repository is not synced with the remote repository `myfirstrepo`.  

	<br>

1. Go back to your web browser and refresh your page to confirm that `README.md` has not been updated and `sample.txt` is not yet created in the remote repository `myfirstrepo`.

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

	<br>
	
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

	As discussed earlier, `origin` refers to the Git URL `https://github.com/<username>/myfirstrepo.git`.   The name `master` refers to the `master` branch in your  remote repository `myfirstrepo`.  A repository may have one or more branches.  By default, a repository has only one branch named `master`.   That is why your remote repository `myfirstrepo` has a `master` branch even if you never explicitly created it.  You may look at your GitHub page to verify that there is indeed a branch named `master` under the remote repository `myfirstrepo`.  This tutorial does not cover the creation of additional branches.

	In summary, the command `git push origin master` pushes the changes of your local repository to the `master` branch of the remote repository referred to by origin (which is `https://github.com/<username>/myfirstrepo.git`).

	<br>
	
1. Go back to your web browser and refresh your page to confirm that `README.md` has been updated and `sample.txt` already exist in the remote repository `myfirstrepo`.

	<br>
	
####Fork an Existing Repository

As mentioned earlier, there are two ways to create a repository.  Either create a new repository from scratch (which is the activity you did in the previous steps) or you fork an existing repository.  In the task below, you will now create your second remote repository by forking an existing one.

<br>

1. Go back to your browser and go to the URL:
		`https://github.com/pong-pantola/mysecondrepo`

	Take note that you do not own this repository.  It is owned by user `pong-pantola`.  This can be verified through to the text `pong-pantola/mysecondrepo` found on the webpage.

	<br>
	
1. Click the `Fork` button.

	You now have your own copy of `mysecondrepo`.  This can be verified through the text `<username>/mysecondrepo` followed by `forked from pong-pantola/mysecondrepo`.

	Forking allows you to make a copy of an existing repository and make it independent from the said existing repository.  If you start making changes to your forked repository, it will affect only this repository.

	<br>


1. Take note of the Git URL of your `mysecondrepo`.  

	```text
	https://github.com/<username>/mysecondrepo.git
	```

	<br>

1. Open another terminal window.  Go to the `gittemp` directory.

	```text
	> cd gittemp
	```

	<br>
	
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
	Initialized empty Git repository in /gittemp/localrepo-two/.git/
	```

	The `git init` command creates a hidden `.git` subdirectory in the directory `localrepo-two`.  This makes the `localrepo-two` a Git repository.

	<br>

1. Create a file `anothersample.txt` in `localrepo-two` directory containing the following:

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
	

	At this point, the changes made (i.e., created the `anothersample.txt` text file) are committed in your local repository.  However, the local repository is not synced with the remote repository `mysecondrepo`.  

	<br>
	
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

	<br>
	
1. Make the localrepo-two `localrepo-two` aware of the remote repository `mysecondrepo`.

	```text
	git remote add origin https://github.com/<username>/mysecondrepo.git
	```

	**Example:**
	
	```text
	git remote add origin https://github.com/pong/mysecondrepo.git
	```
	
	>**IMPORTANT:** The example above uses the Git URL of another user.  Make sure to use the URL of your `mysecondrepo`.

	<br>
	
1. Verify that the Git URL of your remote repository is already declared in your local repository.

	```text
	> git remote -v
	```
	
	**Output:**
	
	```text
	origin  https://github.com/<username>/mysecondrepo.git (fetch)
	origin  https://github.com/<username>/mysecondrepo.git (push)
	```

	<br>
	
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

	<br>
	
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
	From https://github.com/<username>/mysecondrepo
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

	<br>
	
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

<br>

1. **Person A:** On your web browser, create a new remote repository with the following specification:

	||||
	|---|---|---|
	| **Repository name** | mysharedrepo |
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



1. **Person A:** Create a file `contribution-a.txt` in `localrepo-three` directory containing the following:

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

	<br>

1. **Person B:** Create a file `contribution-b.txt` in `localrepo-three` directory containing the following:

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

	<br>
	
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

	The `unable to access` error does not anymore appear.  This means that **Person B** is already given authorization to push updates to **Person A**'s remote repository.  However, the error message encountered in the previous activity appeared again.  This is due to to a `git push` will not sync the local repository of **Person B** and the remote repository of **Person A**.  Note that the remote repository already has `contribution-a.txt` which is still missing in **Person B**'s local repository.  This is summarized below:

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

The previous activity demonstrated how the contributions made by teammates can be consolidated together.  In the next activity, both **Person A** and **Person B** will update the same file `contribution-a.txt`.  You will see the problem caused by such an update and the steps to resolve the problem.

1. **Person A:** Update the file `contribution-a.txt` in `localrepo-three` directory so that it contains the following:

	```text
	This is the contribution of Person A.  This represents a source code written by Person A.
	
	This is an UPDATE made by Person A.
	```

	<br>


1. **Person A:** Track and commit the changes made in the local repository.

	```text
	> git add contribution-a.txt
	> git commit -m "updated contribution-a.txt"
	```

	**Output:**

	```text
	[master d972fef] updated contribution-a.txt
	 1 file changed, 3 insertions(+), 1 deletion(-)
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
	Counting objects: 5, done.
	Delta compression using up to 4 threads.
	Compressing objects: 100% (3/3), done.
	Writing objects: 100% (3/3), 391 bytes | 0 bytes/s, done.
	Total 3 (delta 1), reused 0 (delta 0)
	To https://github.com/<username_of_Person_A>/mysharedrepo.git
	   95b2e65..d972fef  master -> master
	```

	<br>
	
1. **Person B:** Update the file `contribution-a.txt` (not `contribution-b.txt`) in `localrepo-three` directory so that it contains the following:

	```text
	This is the contribution of Person A.  This represents a source code written by Person A.
	
	This is an UPDATE made by Person B.
	```

	<br>


1. **Person B:** Track and commit the changes made in the local repository.

	```text
	> git add contribution-a.txt
	> git commit -m "updated contribution-a.txt by Person B"
	```

	**Output:**

	```text
	[master 8927d94] updated contribution-a.txt by Person B
	 1 file changed, 3 insertions(+), 1 deletion(-)
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

	Similar to the error encountered by **Person B** earlier, **Person B** needs to perform a pull first before doing a push.  The only difference with the error encountered in this step is that the error is caused not by a missing file but due to the varying contents of `contribution-a.txt` in the remote repository and **Person B**'s local repository. 

	**Person B**'s  local repository's `contribution-a.txt`:
	
	```text
	This is the contribution of Person A.  This represents a source code written by Person A.
	
	This is an UPDATE made by Person B.
	```

	**Person A**'s remote repository's  `contribution-a.txt`:
	
	```text
	This is the contribution of Person A.  This represents a source code written by Person A.
	
	This is an UPDATE made by Person A.
	```

	As mentioned, **Person B** can attempt to do a pull to fix the problem.
	
	<br>
	
1. **Person B:** Pull the contents of the remote repository to the  local repository.


	```text
	> git pull origin master
	```
	
	**Output:**
	
	```text
	remote: Counting objects: 3, done.
	remote: Compressing objects: 100% (2/2), done.
	remote: Total 3 (delta 1), reused 3 (delta 1), pack-reused 0
	Unpacking objects: 100% (3/3), done.
	From https://github.com/<username_of_Person_A>/mysharedrepo
	 * branch            master     -> FETCH_HEAD
	   95b2e65..d972fef  master     -> origin/master
	Auto-merging contribution-a.txt
	CONFLICT (content): Merge conflict in contribution-a.txt
	Automatic merge failed; fix conflicts and then commit the result.
	```
	
	The `git pull` command is able to pull the changes from the remote repository (i.e., the line added in `contribution-a.txt`) and include it in `contribution-a.txt` in the local repository of **Person B**.  However, since **Person B** did its own changes on the file, Git failed to figure out how to properly merge/consolidate the two changes.  

	The `contribution-a.txt` in the local repository of **Person B** now contains the following:

	```text
	This is the contribution of Person A.  This represents a source code written by Person A.
	
	<<<<<<< HEAD
	This is an UPDATE made by Person B.
	=======
	This is an UPDATE made by Person A.
	>>>>>>> d972fefa5dc88f258ded0d157977600e7503293f
	```
	
	The `git pull` command placed a marker on the changes that it failed to merge.  The reason why it failed to merge is `git pull` does not know if your intention is to retain only one of the two lines or if you want to retain both.  Git is letting you to manually merge these updates.

	You will retain both `This is an UPDATE made by Person B.` and `This is an UPDATE made by Person A.`.  This represents both **Person A** and **Person B** placing updates on the same file.


	<br>

1. **Person B:** Fix the file `contribution-a.txt`  in `localrepo-three` directory so that the markers are removed:

	```text
	This is the contribution of Person A.  This represents a source code written by Person A.
	
	This is an UPDATE made by Person B.
	
	This is an UPDATE made by Person A.
	```

	Take note that `contribution-a.txt` in the remote repository still does not contain the updates made by **Person B**.  This is the current content of  `contribution-a.txt` in the remote repository:

	```text
	This is the contribution of Person A.  This represents a source code written by Person A.
	
	This is an UPDATE made by Person A.
	```

	**Person B** will commit the changes made in `contribution-a.txt` and push the updates to the remote repository.
	
	<br>
	


1. **Person B:** Track and commit the changes made in the local repository.

	```text
	> git add contribution-a.txt
	> git commit -m "merged updates on contribution-a.txt"
	```

	**Output:**

	```text
	[master 72c9355] merged updates on contribution-a.txt
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
	Counting objects: 10, done.
	Delta compression using up to 4 threads.
	Compressing objects: 100% (6/6), done.
	Writing objects: 100% (6/6), 709 bytes | 0 bytes/s, done.
	Total 6 (delta 2), reused 0 (delta 0)
	To https://github.com/<username_of_Person_A>/mysharedrepo.git
	   d972fef..72c9355  master -> master
	```

	Note that before the push, `contribution-a.txt` of the local repository of **Person B** and the remote repository are different.  The version in the remote repository does not contain the line `This is an UPDATE made by Person B.`.  After the push, git is able to successfully merge the updates made in the local repository of **Person B** to the remote repository.

	At this point, the local repository of **Person B** and remote repository are synced.  However, `contribution-a.txt` of the local repository of **Person A** is not yet updated.  It does not contain the line `This is an UPDATE made by Person B.`.  This can be resolved with another pull from **Person A**.
	
	<br>

1. **Person A:** Pull the contents of the remote repository to the  local repository.


	```text
	> git pull origin master
	```
	
	**Output:**
	
	```text
	remote: Counting objects: 6, done.
	remote: Compressing objects: 100% (4/4), done.
	remote: Total 6 (delta 2), reused 6 (delta 2), pack-reused 0
	Unpacking objects: 100% (6/6), done.
	From https://github.com/<username_of_Person_A>/mysharedrepo
	 * branch            master     -> FETCH_HEAD
	   d972fef..72c9355  master     -> origin/master
	Updating d972fef..72c9355
	Fast-forward
	 contribution-a.txt | 4 +++-
	 1 file changed, 3 insertions(+), 1 deletion(-)		
	```

	The two local repositories and the remote repository are now synced.

	<br>

	
####End of Tutorial

Go back to the [List of Tutorials](/tutorial-list).

####What's next?

[JUnit Basics Tutorial](/junit-basics)




