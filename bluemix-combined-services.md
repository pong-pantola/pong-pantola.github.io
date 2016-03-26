---
layout: post
title: Combining Services in Bluemix
permalink: /bluemix-combined-services/
---


Bluemix has a set of services that can be combined in a single web application (e.g., output of one service will serve as input of another service).

In this tutorial you will learn how to combine services in [IBM Bluemix](https://ibm.biz/bluemixph).

<br>

>**Prerequisite:**

>You are **required** to do the [Creating a Web Application using Gradle Tutorial](/gradle-web-application).

>- The steps used in this tutorial is based from [Creating a Web Application using Gradle Tutorial](/gradle-web-application). 

>You are not required (but **recommended**) to do  the [Bluemix Basics Tutorial](/bluemix-basics).

>- **However**, ensure that you have a Bluemix account.  
>- Your account should have the space `dev` under the region `US-South`.  The creation of the space `dev` is discussed in [Bluemix Basics Tutorial](/bluemix-basics).
>- Make sure that the `cf` tool is installed.  The installation of `cf` tool is discussed in [Bluemix Basics Tutorial](/bluemix-basics).

>You are not required (but **recommended**) to do  the [GitHub Basics Tutorial](/github-basics).

>- **However**, ensure that you have a GitHub account.



<br>


####Copy Sample Codes from Git repository


1. Open a terminal window and create the directory `gradletemp` in the root directory.  Go to the created directory.

	```text		
	> mkdir bluemixtemp
	> cd bluemixtemp
	```

	<br>
	
1. Clone the git repository `https://github.com/pong-pantola/bluemix-combined-services.git` and go to the created `bluemix-combined-services` directory.

	```text
	> git clone https://github.com/pong-pantola/bluemix-combined-services.git
	> cd bluemix-combined-services
	```
 

1. Assemble the Gradle project.

	> Make sure that you are in the `bluemix-combined-services` directory before issuing the command below.

	```text
	> gradle assemble
	```

	**Output:**
		
	```text
	:compileJava
	:processResources
	:classes
	:war
	:assemble
	
	BUILD SUCCESSFUL
	
	Total time: 9.289 secs
	```
	


	<br>


####Deploy the Web Application in Bluemix

1. Login to your Bluemix account using the `cf` tool.

	> Make sure that you are in the `bluemix-combined-services` directory before issuing the command below.

	```text
	> cf login -a https://api.ng.bluemix.net -s dev
	```

	<br>
	
1. Upload the web application to your Bluemix account.

	```text
	> cf push combination-<your_name> -m 512M -p build/libs/webapp.war
	```

	**Example:**
		
	```text
	> cf push combination-pong -m 512M -p build/libs/webapp.war
	```

	<br>

####Add Bluemix Services to the Web Application

1. Open a web browser and login to your [Bluemix](https://ibm.biz/bluemixph) account.

1. Click the widget of your application (`combination-<your_name>`) to see its overview.

1. Click the `ADD A SERVICE OR API` link.  You will be redirected to the `Catalog` page. 

1. Look for the `AlchemyAPI` service and click it.

1. In the `Service name` text box, use the default name.

1. Click the `CREATE` button.

1. When asked to restage your application, click the `CANCEL` button.

	> If you click the `RESTAGE` button, your application will restart.  It is advisable to click the `RESTAGE` button once you have added all the services, otherwise your web application will keep on restarting every time you click `RESTAGE` which will make the procedure of adding services longer.

1. Repeat the steps above to add the following services:
	- Language Translation
	- Speech To Text
	- Text To Speech
	- Cloudant NoSQL DB
	- Object Storage
	- mongodb (not MongoDB by Compose)
	- redis (not Redis by Compose)

	> **VERY IMPORTANT:**
	>For monogdb and redis, as mentioned above, do not use the version "by Compose".  Instead, in the `Catalog` page, scroll down in the `CATALOG` page until you see the `Bluemix Labs Catalog` link.  Click this link.	 Look for the services named `mongodb` and `redis`.

	> When you add the last service (redis), you will be asked to restage your application, click the `RESTAGE` button.  If you don't click the `RESTAGE` button, your application will not restart and it will not recognize all the services you added.

1. Wait for your application to restart.
	
1. On another browser tab, go to `http://combination-<your_name>.mybluemix.net`.

	**Output:**
		
	```text
	Alchemy-Cloudant
	
	Alchemy-MongoDB
	
	Alchemy-Redis
	
	Alchemy-TextToSpeech
	
	LanguageTranslation-TextToSpeech
	
	ObjectStorage-SpeechToText
	
	TextToSpeech-ObjectStorage 
	```

	You have successfully deployed the web application in Bluemix.

	<br>

####Test the Application
Each hyperlink demonstrates how two services are combined.  For example, the link `Alchemy-Cloudant` demonstrates how the output of Alchemy API is used in Cloudant NoSQL DB.

1. Alchemy-Cloudant

	This asks a user to enter a URL of an image file.  The image should contain at least one person.  Alchemy API will extract information from the image.  Specifically, it will extract the age and gender of the person in the image.

	The extracted age and gender are saved in a Cloudant NoSQL DB service.
	
1. Alchemy-MongoDB

	This is the same as Alchemy-Cloudant except that the extracted age and gender are saved in a mongodb service .
	
1. Alchemy-Redis

	This is the same as Alchemy-Cloudant and Alchemy-MongoDB except that the extracted age and gender are saved in a redis service .
	
1. Alchemy-TextToSpeech
	
	This is the same as Alchemy-Cloudant, Alchemy-MongoDB, and Alchemy-Redis.  However, instead of saving the age and gender, it will create a WAV file that contains the following sound: `Information Extraction Complete.  The person in the picture is a <GENDER>.  <His/Her> age is <AGE>`.
	
1. LanguageTranslation-TextToSpeech

	This asks a user to enter a text in Spanish.  Using the Language Translation service, it will convert the text to English.  The English text is converted to a speech (i.e., WAV file) using the Text To Speech Service.
	
1. ObjectStorage-SpeechToText

	This asks a user to select a WAV file containing an English sentence.  The WAV file is uploaded in an Object Storage service.

	From the Object Storage service, it will download the WAV file and convert it to its equivalent to text using the Speech To Text service.
	
1. TextToSpeech-ObjectStorage 

	This asks a user to enter a text.  The text is converted to speech (i.e., WAV file) using the Text To Speech service.  The WAV file is uploaded in an Object Storage service.  

####Clean up

1. Delete your Bluemix application `combination-<your_name>`.

1. Make sure to delete as well all the created services.
	<br>

####End of Tutorial

Go back to the [List of Tutorials](/tutorial-list).

