# IT Infrastructure Lab 5 Instructions #
**Overview**

Lab objectives:
Examine the details of an end to end DevOps pipeline and participate in it using your development environment.

In this lab, you will configure and instantiate your own VM that serves as a distributed development environment. You will change software that other students are also changing at the same time, and see how git is used to manage this.

**In the following material substitute the 2-digit number you receive from the instructor, for XX**

First, clone the "Lab O5" branch of Calavera thus (DON'T FORGET TO CHANGE XX TO YOUR 2 DIGIT #!):

    cd
    git clone https://github.com/StThomas-SEIS660/Calavera.git -b Lab-05 --single-branch manosXX

What does this do? Git repositories can be branched; a branch is a separate line of development. The Cala-dev branch gives you a single machine Vagrantfile to modify, making things a little easier for you.

Review [this link](http://stackoverflow.com/questions/1778088/how-to-clone-a-single-branch-in-git) for further explanation

cd into Cala-dev

and change the machine # and related settings from 40 to the 2-digit number you have been assigned in class.



You can do this in nano easily:

````
Ctrl \
Enter your search term [press return]
Enter your replacement term [press return]
A [to replace all instances]
````
Vagrant up!

    XXXXXX/manos41$ vagrant up
    Bringing machine 'manos41' up with 'virtualbox' provider...

ssh into your development VM:

    vagrant ssh manosXX

Set your git variables:

    vagrant@manos40:~/hijo$ git config --global user.name "Manos XX"
    vagrant@manos40:~/hijo$ git config --global user.email manosXX@calavera.biz

Type:

    vagrant@manos40:~$ git clone ssh://cerebro/home/hijo.git

You should get:

````
Cloning into 'hijo'...
The authenticity of host 'cerebro (192.168.33.30)' can't be established.
ECDSA key fingerprint is 7c:d9:8b:ec:ac:27:b5:f8:2d:2c:ff:e0:11:1e:51:f2.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'cerebro,192.168.33.30' (ECDSA) to the list of known hosts.
remote: Counting objects: 22, done.
remote: Compressing objects: 100% (15/15), done.
remote: Total 22 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (22/22), 7.76 KiB | 0 bytes/s, done.
Checking connectivity... done.
````
Go into your new hijo directory and build:

    vagrant@manos40:~$ cd hijo
    vagrant@manos40:~/hijo$ sudo ant

You should get

````
Buildfile: /home/vagrant/hijo/build.xml

init:
     [echo]
     [echo] 			Computer name is ${my_env.COMPUTERNAME}
     [echo]                         User name is root
     [echo] 			Building from /home/vagrant/hijo/build.xml
     [echo] 			Java is version 1.7
     [echo] 			Project is ${ant.project.name}
     [echo] 			Ant is Apache Ant(TM) version 1.9.4 compiled on April 29 2014
     [echo] 			Basedir is /home/vagrant/hijo
     [echo] 			Source is ./src/main/java/biz/calavera
     [echo] 			Build target is ./target
     [echo] 			Deployment target is /var/lib/tomcat6/webapps/ROOT/WEB-INF/lib
     [echo]

compile:
    [javac] Compiling 2 source files to /home/vagrant/hijo/target
    [javac] Compiling 1 source file to /home/vagrant/hijo/target

test:
     [echo]
     [echo] 			entering test
     [echo]
    [junit] Running biz.calavera.TestClass1
    [junit] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.064 sec

compress:
      [jar] Building jar: /home/vagrant/hijo/target/CalaveraMain.jar

deploy:
    [mkdir] Created dir: /var/lib/tomcat6/webapps/ROOT/WEB-INF/lib
     [copy] Copying 1 file to /var/lib/tomcat6/webapps/ROOT/WEB-INF/lib
     [copy] Copying 1 file to /var/lib/tomcat6/webapps/ROOT/WEB-INF
     [echo]
     [echo] 			Attempting Tomcat restart.
     [echo]
     [exec] The command attribute is deprecated.
     [exec] Please use the executable attribute and nested arg elements.
     [exec]  * Stopping Tomcat servlet engine tomcat6
     [exec]    ...done.
     [exec] The command attribute is deprecated.
     [exec] Please use the executable attribute and nested arg elements.
     [exec]  * Starting Tomcat servlet engine tomcat6
     [exec]    ...done.

main:
     [echo]  
     [echo] 			built and deployed to Tomcat.
     [echo]

BUILD SUCCESSFUL
Total time: 7 seconds
````
Check that your development Tomcat server is serving your page:

    vagrant@manos40:~/hijo$ curl localhost:8080/MainServlet
    <h1>This is a skeleton application-- to explore the end to end Calavera delivery framework.</h1>

Up til now, this should all seem familiar as it is similar to Lab 04. However, you are now in a fully distributed development environment with many others working on the same code base.

You are going to make a change, test it out locally, commit it to git locally, and then push it to the central repository (cerebro). When you do this, it will trigger a remote build and test, and you will see on the Jenkins dashboard whether it succeeded or failed





The key principle is that you must pull very frequently, especially if you are about to change something.

http://192.168.33.33:8080/ jenkins




they need to examine the chain step by step and run small experiments

we need a lab that has the students collaborating on making small contributions to the application in a distributed way.

they each need to add a small piece of functionality with a small test case
  - each should add their own Class and TestClass
  - and one main class should call each method



they need to check out, make changes, refresh & sync & test locally, then push and run the build.

then deploy to production.

what about breaking and backing out? reverting?

will need XWindows working for Jenkins and Artifactory and the final application result.




=======================

Future:

lab 6: Nagios monitoring

Lab 7: Jira & collab

Lab 8: Project mgmt

Lab 9: ITSM

Lab 10: ITSM?

Lab 11: Portfolio

Lab 12: Performance? Simulated outage?
