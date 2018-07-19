![](http://us-west-2-aws-training.s3.amazonaws.com/awsu-spl/spl11-media-1-upload/media/image001.gif)



# &lt;AWS&gt; ISV Labs: Immersion Day



# Monolith to Microservices: Part I



## Self-Paced Lab

### Version 1.0.0C

© 2018 Amazon Web Services, Inc. and its affiliates. All rights reserved. This work may not be reproduced or redistributed, in whole or in part, without prior written permission from Amazon Web Services, Inc. Commercial copying, lending, or selling is prohibited.

Errors or corrections? Please open an issue on our [issue tracker](https://github.com/isvlabs/cloud-developer/issues).



## Prerequisite Client Software

To complete this lab, you will need to have the following software installed on your development machine

 *Note: You'll need local admin access to the machine you use today. Basically, make sure you have the rights to install software.*

- [Git client](https://git-scm.com/book/en/v1/Getting-Started-Installing-Git)
- [Java JDK 8+ ](http://www.oracle.com/technetwork/pt/java/javase/downloads/jdk8-downloads-2133151.html "Java 8 JDK")
- [Maven 3.0+](https://maven.apache.org/download.cgi "Maven")
- [Eclipse IDE for Java EE Developers](https://www.eclipse.org/downloads/eclipse-packages/ "Eclipse IDE"). (Please install Eclipse Neon or above)    
- [Tomcat 8.0+](https://tomcat.apache.org/tomcat-9.0-doc/index.html "Tomcat")
- [AWS Toolkit for Eclipse](http://docs.aws.amazon.com/toolkit-for-eclipse/v1/user-guide/setup-install.html)
- [AWS CLI](http://docs.aws.amazon.com/cli/latest/userguide/installing.html)
- [Elastic Beanstalk CLI](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install.html). Follow the instructions in the guide to install the AWSEBCLI. **Note:** please do not use `brew` to install the tool, it is known to have some issues. Instead, follow the instructions as per the link above.
- [Docker](https://docs.docker.com/engine/installation/)

- Optional:
  - HTTP Client for testing web services e.g. [curl](http://macappstore.org/curl/), [Postman](https://www.getpostman.com/)
  - Have a SQL client (which supports **MySQL**) *or simply use the embedded IDE database client* e.g. [Workbench](https://www.mysql.com/products/workbench/), [SQuirrel](http://squirrel-sql.sourceforge.net/)



## Lab Overview

### Overview

*In this lab you learn how to deploy our fictitious web application **TravelBuddy** to run on the AWS Elastic Beanstalk PaaS service. You will learn how to use CloudFormation to automate the creation of your base cloud infrastructure, and the AWS Elastic Beanstalk CLI tool to automate the provisioning and deployment of the web application. The CloudFormation template provided for you will automatically provision a MySQL database instance hosted with Amazon RDS, and all the necessary networking components to secure the environment. It also deploys a Jump host server that you will use to access the secured environment.*



### Topics Covered

By the end of this lab, you will be able to:

  

- [ ] Take an existing monolithic application and packing as a [Docker Container](https://www.docker.com/what-container) 

- [ ] Use [AWS Elastic Container Registery (ECR)](https://aws.amazon.com/ecr/) to

- [ ] Deploying docker containers to [AWS Elastic Container Service (ECS)](https://aws.amazon.com/ecs/)

- [ ] Use [AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/) deploy to a Elastic Beanstalk environment.

- [ ] Technique to decompose the monolith into a number of microservices using Docker, Elastic Beanstalk and ECS

- [ ] **TBC** CodeStar

  

### Technical Knowledge Prerequisites

To successfully complete this lab, you should be familiar the Eclipse application development environment, the Java programming language and the command line/terminal.



### The AWS Console

#### Accessing the AWS Management Console

1. Browse to the following URL for the AWS Management Console:

    https://console.aws.amazon.com/console/home  

    You will have been given a username and password for this lab. Please make sure you have this handy. If you don't, let your lab instructor know.

2. Log into the AWS console using the supplied credentials. You should see the default landing page for the AWS Management Console.

You will need to provide:
* **IAM User Name** - `Username` 
* **Password** - `Password` 
* **Account ID or alias** - `AWS Account`  

![](designtime_images/awsconsolelogin.png)



#### Verifying Your Region in the AWS Management Console

Make a note of the AWS *region name*, for example, *Asia Pacific (Sydney)*, that your lab is configured for.

The AWS region name is always shown in the upper-right corner of the AWS Management Console, in the navigation bar. You should double-check that the current region in the AWS Console matches the region your instructor has requested you to use.

You will normally use the code - for example, *ap-southeast-2* - instead of the region name - for example, *Asia Pacific (Sydney)* - whenever the lab guide asks you to specify your region.

**NOTE:** We will use the **Asia Pacific (Sydney)**, or **ap-southeast-2** region for this lab.





## Setting up your Lab environment.

The first we need to do is clone this git repo.



## Git checkout

The first thing you'll need to do is check out the repository. The monolith is part of the Github repository, so clone this to your local environment.

```
git clone https://github.com/isvlabs/amazon-ecs-java-microservices.git
```



## Setting up access to your AWS lab account

### Configuring the AWS CLI

You'll need to configure the AWS CLI to use the credentials supplied to you for this lab.

Run:
	aws configure

and configure with your **AWS Access Key ID** and **AWS Secret Access Key**.

Many developers are very at home automating their AWS infrastructure from the command line. Much of the lab will suppose this. If you're not in this camp, that's OK, you can also use the AWS Console instead. We won't show you step by step how to use the console though, but use the account ID and password given to you.




## Contributing

The [issue tracker](https://github.com/isvlabs/monolith-to-microservices/issues) is the preferred channel for bug reports, features requests and submitting pull requests.

For pull requests, editor preferences are available in the [editor config](https://github.com/isvlabs/monolith-to-microservices/blob/master/.editorconfig) for easy use in common text editors. Read more and download plugins at <http://editorconfig.org>.