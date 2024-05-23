# Simple CI/CD Pipeline

In this project I used Jenkins to create a CI/CD Pipeline. For version controll system I used git and for centralized code storage used github. Create a ubuntu VM machine using VM ware and after the installing the guest os I installed the requied tool for this project like git, maven , docker and also installed the all dependencies required for the services. Then I install java because Jenkins is based on the java after sucessfull installation of java I installed Jenkins.

After the jenkins installation open the jenkins dashboard and create Project Pipeline Project 

![jenkins free style project](https://github.com/KaranNawale02/Jenkins_Docker_Integration/assets/124289243/ad513de7-6d1e-434a-b715-bcdc8f49decd)

Now lets configure the git for a directory to do that go to the project directory and enter the command

    git init
    git add .
    git remote addd origin <url for repo >
    git push -m origin master

After sucessfully initializing the git go the jenkins and configure the pipeline and declerative script fot the project and also selct a build trigger a Git web hook. that will do whenerver a commit happend jenkins will automaticallly pull the code from git and do the process

![buiild_triggers](https://github.com/KaranNawale02/Jenkins_Docker_Integration/assets/124289243/4603f208-9856-4147-820e-ddee6bbb668d)

Now our first stage is complete of our pipeline that is integrate a version controll system with jenkins now Lets build the projcet using maven casue this is maven project.
Add the following script in the jenkins pipeline script. here we are using declarative scripting.

![mvn build script](https://github.com/KaranNawale02/Jenkins_Docker_Integration/assets/124289243/676e7e41-aeaa-4965-a681-fe7d9ac741e2)

We sucessfully added the maven clean installation step to build our project. Now we have to build a docker image that we will use to containers from that image.
To do that we need add the docker file in our project . Go to your project folder and add a file named as DockerFile and add this line in the file 

    FROM openjdk:8
    EXPOSE 8080
    ADD target/devops-automation.jar devops-automation.jar
    ENTRYPOINT  ["java", "-jar" , "/devops-automation.jar"]

here I used my project name as devops-automation to set a final name for your project go to the .pem file in your project and add this  line 

    <finalName>devops-automation</finalName>

here you can give any name but you have to mention this name into your docker file 

now to check that is it working or not is created target file name is same or not build the project and install using maven on locally it will create a target folder and in that folder there will be a your file as per the name 
As we added a dockerfile in local now we have to push it our VCS to do that do 

    git pull
    git add .
    git commit -m "commit to add docker file in the project"
    git push

It will do pull first, if ther is any new files or commits happend in central repo then it will firstly pull that and then push new updated files or project 

Now, Befor doing anything check that all necessary services are up and running like docker, maven, git 

After shure that all services are up and running then add the next step in the script 

