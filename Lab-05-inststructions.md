# IT Infrastructure Lab 5 Instructions #
**Overview**

Lab objectives:
Examine the details of an end to end DevOps pipeline and participate in it using your development environment.

outline (somewhat meta)

first, the default is not for each student to install their own entire pipeline on the server. the server will not scale to that level, and it's too much complexity for me to support.

so, we need to stand up ONE pipeline. (I need to get the pipeline working end to end on seis660)

they each need their own development machine working... or should I do one per team?  I may need to configure the whole cluster. This is where containers would make a lot more sense. 

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
