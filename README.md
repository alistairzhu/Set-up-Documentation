	

Install Docker Toolbox on Windows10 HOME  (without HyperV)
-----------------------------------	
https://docs.docker.com/toolbox/toolbox_install_windows/#step-2-install-docker-toolbox
	



Install Docker on EC2 Ubuntu:
-------------------------------------
Technical setup for the CFDev 
In order to follow along with instruction during the course you'll need a couple tools installed prior to the class. The instructors will explain the technology we will be using in detail, but some of it can take a while to set up properly so installing it ahead of time is necessary. 
First install your image on AWS by following the below steps: 
Go to https://signin.aws.amazon.com 
Either Login or create and account. Once you logged in goto Service and select EC2 
When you are in the EC2 Dashboard under images select AMI’s 
In Region US East (Ohio) Region Public Images Once you are in the EC2 Search section please select public images from the search option and search for: ami-0335cbe3813a6b4e5 

Or In Region US East (Ohio) Region Public Images Once you are in the EC2 Search section please select public images from the search option and search for: ami-0335cbe3813a6b4e5 

When you see then image, select the image and from the Actions drop down select Launch 
When you select Launch you will brought to the Instance Type Selection page. 
Select the image type: “t2 micro” then click on the Review and Launch Button 
When prompted, create a new key pair and then save the resulting file onto your desktop. 
Depending on whether you are using Windows or Apple, proceed by following the steps as outlined in the below links: 
SSH Access to Amazon Instance on windows 
https://www.youtube.com/watch?v=bi7ow5NGC-U 
SSH Access To Amazon Instance on Apple: 
https://www.youtube.com/watch?v=zC05VLyNTZY 
What is Docker? 
https://www.youtube.com/watch?v=aLipr7tTuA4 
Git and Github 
You will need to install git on your computer, and sign up for a github account if you don't have one already. The capstone project will be submitted as a github repository. Use this tutorial to get started. 
http://product.hubspot.com/blog/git-and-github-tutorial-for-beginners



•	
•	install CPG Key
	curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add –
•	Add the Docker repository to APT sources:
	sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
•	update Ubuntu
	sudo apt-get upgrade
	sudo apt-get update
•	check repo
	apt-cache policy docker-ce
•	install Docker
	sudo apt-get install -y docker-ce
•	check Docker version
	docker -v
•	install Docker Composer (on Ubuntu it is not automatically installed with Docker)
•	check latest version (1.19)
•	Install
	curl -L https://github.com/docker/compose/releases/download/1.19.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
•	set permission
	sudo chmod +x /usr/local/bin/docker-compose
•	check version
	docker-compose --version

Start Docker see :
Hyper-V feature is not enabled.
Do you want to enable it for Docker to be able to work properly?
Your computer will restart automatically.
Note: VirtualBox will no longer work.

Answer Y to enable it.



Install Go:
------------------------------------------------------------------------------------------

check go website for latest version (1.10)
Download
#curl -O https://storage.googleapis.com/golang/go1.11.linux-amd64.tar.gz

Untar
#tar xvf go1.11.linux-amd64.tar.gz

change go user to root:root
#sudo chown -R root:root ./go

move directory
#sudo mv go /usr/local

set go path
#pico ~/.profile
add this to the bottom of the file
  export GOPATH=$HOME/work
  export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin
Save and exit file 

refresh profile
#source ~/.profile

Check Version
#go version


Using Docker for a java project
-----------------------------------------
https://www.youtube.com/watch?v=FlSup_eelYE
https://www.youtube.com/watch?v=wCTTHhehJbU

Docker command:
--------------------

Start Docker QuickStart terminal (or PowerShell)
docker ps
docker images
Docker run hello-world
docker run -it --name james ubuntu
Ctrl+pq  (to go back to Power Shell without stop container)
docker attach james  (to return docker)
"exit" will stop the container!
docker rmi -f hello-world (delete image)

Build and run, see document at:
https://github.com/nodejs/docker-node/blob/master/README.md#how-to-use-this-image


Create .Dockerfile at the root folder of project:

FROM node:6-onbuild
EXPOSE 80 

docker build -t hello-system  -f ./.Dockerfile .
In the root folder run: docker run -it -p 1337:80 --name hyi hello-system
Then in browser open  localhost:1337

After making any change, NO need to rebuild, just  need to sync up windows folder with unix. 
In Docker > Setting make "Share drive c:" 
Then , need to delete previoue "Run".
docker start aaa
docker ps
docker rm -f aaa

docker run -it -p 3000:80 -v //C/Projects/docker/sample/hello-system/.:/usr/src/app --name hi hello-system
Then in browser open  localhost:3000    (can see live change)

Create Docker for a java application:

In POM file , 
<artifactId>api-testing</artifactId>
    <version>1.0-snapshot</version>

Create a .jar file api-testing-1.0-snapshot.jar at target folder: 
>mvn package 	

Create Dockerfile at root:

from openjdk:10
add target/api-testing-1.0-snapshot.jar api-testing-1.0-snapshot.jar
expose 8085
entrypoint ["java", "-jar","api-testing-1.0-snapshot.jar"]

Build an image from a Dockerfile and run the image:
>docker build -f Dockerfile -t api-testing-1.0-snapshot .
>docker run -p 8085:8085 --rm api-testing-1.0-snapshot



Android Studio "Design view not show new added elements:
Edit File build.gradel (model app), update one line in dependencies:  "implementation 'com.android.support:appcompat-v7:28.0.0-alpha1'"


Docker for Android :
https://medium.com/@elye.project/intro-to-docker-building-android-app-cb7fb1b97602
