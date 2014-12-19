
# gradle-plugin-mvn-push

-------------------------------------------------------

Equivalent to Chris Banes' [gradle-mvn-push](https://github.com/chrisbanes/gradle-mvn-push)
script but for Gradle custom plugins written in Groovy.

Thanks to Chris Banes

--------------------------------------------------------
## Use
###Step 1 ：

	apply from: 'https://raw.githubusercontent.com/sdaduanbilei/gradle-plugin-mvn-push/master/gradle-mvn-push.gradle'


Add  code above to your library for publishing build.gradle

>e.g: [build.gradle](https://github.com/sdaduanbilei/DashboardViewExample/blob/master/library/build.gradle)

###Step 2：

	POM_NAME = My Library    
	POM_ARTIFACT_ID = my-library
	POM_PACKAGING = aar
	
Add a gradle.prorerties file in the library, and add the code above 

>e.g [gradle.properties](https://github.com/sdaduanbilei/DashboardViewExample/blob/master/library/gradle.properties)

### Step 3:

	NEXUS_USERNAME = your user name
	NEXUS_PASSWORD = your password
	
This will include the username and password to upload to the Maven server and so that they are kept local on your machine. The location defaults to `USER_HOME/.gradle/gradle.properties`.
It may also include your signing key id, password, and secret key ring file (for signed uploads). Signing is only necessary if you're putting release builds of your project on maven central.

### Step 4：
You may already have this file, in which case just edit the original. This file should contain the POM values which are common to all of your sub-project (if you have any). For instance, here's [DashboardView](https://github.com/sdaduanbilei/DashboardViewExample):

	VERSION_NAME=1.0.0
	GROUP=com.github.sdaduanbilei
	POM_DESCRIPTION=A custom view for dashboradview
	POM_URL=https://github.com/sdaduanbilei/DashboardViewExample
	POM_SCM_URL=https://github.com/sdaduanbilei/DashboardViewExample
	POM_SCM_CONNECTION=scm:git@github.com:sdaduanbilei/DashboardViewExample.git
	POM_SCM_DEV_CONNECTION=scm:git@github.com:sdaduanbilei/DashboardViewExample.git
	POM_LICENCE_NAME=The Apache Software License, Version 2.0
	POM_LICENCE_URL=http://www.apache.org/licenses/LICENSE-2.0.txt
	POM_LICENCE_DIST=repo
	POM_DEVELOPER_ID=sdaduanbilei
	POM_DEVELOPER_NAME=sdaduanbilei
	
The `VERSION_NAME` value is important. If it contains the keyword `SNAPSHOT` then the build will upload to the snapshot server, if not then to the release server.

>e.g [gradle.properties](https://github.com/sdaduanbilei/DashboardViewExample/blob/master/gradle.properties)

### Step 5


     ` $./gradlew clean assemble uploadArchives`

Under the item before you execute the following command, Then you need to enter your configuration information on the GPG，Upload completed OK 。



##Important

### tips 1
 
 Before that you have to have a JIRA account and create a JIRA ticket ：
 
 `Sonatype JIRA	` [https://issues.sonatype.org/](https://issues.sonatype.org/)

 Create a JIRA ticket
 
 `JIRA TICKET`  [Create a JIRA ticket](https://issues.sonatype.org/secure/CreateIssue.jspa)
 Your project corresponds to a JIRA ticket here,Summary of which you can fill in the project name and Description to fill in project description. Group Id is very important ,Follow the prompts to fill in. Probably about 2 working days after the completion, the Issue turns into a `resolved` State is available, then you can start publishing your project.

### tips 2 

You need to have your GPG public key uploaded to Sonatype as well. You may have missed that step. I plan to write a blog post with the detailed steps, but here are some quick notes with steps you'll need to perform:

Generate gpg key [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

 `$ gpg --gen-key`
 
Add gpg public key to ubuntu keyserver: [http://keyserver.ubuntu.com/](http://keyserver.ubuntu.com/)

`$ gpg --send-keys --keyserver keyserver.ubuntu.com $GPGKEY`

Save the KeyID and password, this is when you publish more often need information of GPG 。

PGP Secret Key Ring File (absolute path) :`/Users/<username>/.gnupg/secring.gpg`

 
##About Me


sdaduanbilei  kunming

##License
	Copyright 2014 sdaduanbilei

	Licensed under the Apache License, Version 2.0 (the "License");
	you may not use this file except in compliance with the License.
	You may obtain a copy of the License at

		 http://www.apache.org/licenses/LICENSE-2.0

	Unless required by applicable law or agreed to in writing, software
	distributed under the License is distributed on an "AS IS" BASIS,
	WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
	See the License for the specific language governing permissions and
	limitations under the License.	
 














