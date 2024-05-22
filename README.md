# Simple CI/CD Pipeline

In this project I used Jenkins to create a CI/CD Pipeline. For version controll system I used git and for centralized code storage used github. Create a ubuntu VM machine using VM ware and after the installing the guest os I installed the requied tool for this project like git, maven , docker and also installed the all dependencies required for the services. Then I install java because Jenkins is based on the java after sucessfull installation of java I installed Jenkins.

After the jenkins installation open the jenkins dashboard and create Project Pipeline Project 

![jenkins free style project](https://github.com/KaranNawale02/Jenkins_Docker_Integration/assets/124289243/ad513de7-6d1e-434a-b715-bcdc8f49decd)

Now lets configure the git for a directory to do that go to the project directory and enter the command

    git init
    git add .
    git remote addd origin <url for repo >
    git push -m origin master

After sussfully initializing the git go the jenkins and configure the pipeline and declerative script fot the project and also selct a build trigger a Git web hook. that will do whenerver a commit happend jenkins will automaticallly pull the code from git and do the process

![buiild_triggers](https://github.com/KaranNawale02/Jenkins_Docker_Integration/assets/124289243/4603f208-9856-4147-820e-ddee6bbb668d)

