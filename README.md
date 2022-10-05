# JENKINS-FREE-STYLE-PROJECT

###### Prerequisites: -->Jenkins Server ---> Sonarqube server ---->Nexus Repository ---->Apache Tomcat server

###### Before starting the project we need to have all the above four servers installed and configured

###### 1. In Jenkins, go to new item-->Freestyle project

###### 2. Under source code management,give your git hub URL where your code resides and also configure your github password in Jenkins

###### 3. Then in the build select "Invoke top level Maven target"( Since we are going to build Java project)

######   - And also select Maven version

######   - Goals To build the app- Clean package

######   - Goals to push the code to Sonarqube - sonar:sonar

###### 4. To combine both it is- clean package sonar:sonar Now build the Code

###### Then need to transfer it to Sonarqube to check the code vulnerabilites and bugs (And for this we need to update the sonarqube URL and token in pom.xml)

##### 5. Once the code passed the checks in Sonarqube, need to send the artifact file or binary file(war file) to Nexus repository. (And for this we need to update the nexus username and password in settings.xml in maven-/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/maven3.8.6/conf/settings.xml) Goals to deploy the artifacts to Nexus repo- deploy (clean package sonar:sonar deploy)

###### 6. Once it got updated then we can start the build and the artifacts will save under snapshot repository in Nexus

###### 7. Now we are going to deploy to Tomcat server --> And for this we need to install plugin called "deploy to container" in Jenkins --->Update tomcat credentials in Jenkins ---> vi cd/opt/tomcat/conf/tomcatusers.xml. In tomcatusers.xml,we need to update the manager-script role ---> Restart the tomcat server ----> Then start the build and it deploy to tomcat server
