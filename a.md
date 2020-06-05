terraform {
	backend "s3" {
	
	bucket         = "Snobbish-state"
    key            = "myuser/s3/terraform.tfstate"
    region         = "us-east-2"
	
	dynamodb_table = "Snobbish_lock"
    encrypt        = true
  }
}

we had to restart our system every few months because of a memory leak.++ and the mystery annoyed me. So I spent a few hours reading very carefully through our memory management code, and realized that we incorrectly double-parsing in one of our helper functions. Not only did it save on memory, but CPU as well. It'd been there for years.

------------G+D---------------
The aim of my current project is to provide a technical solution for the remote provisioning and
management of the Embedded UICC (eUICC) in machine-to-machine Devices which are not
easily reachable. 

My client offers market leading, secure and flexible embedded SIM (eSIM) management that enables the remote change of the subscription profile in an eSIM. The eSIM, or more correctly the eUICC, may either be soldered into the device during production, or later inserted as a plug-in form factor (like the traditional SIM card). First, AirOn eSIM management can download the subscription profile into a new device, anywhere in the world and anytime the customer chooses; and second, AirOn can provide the lifetime remote management of the eUICC and its subscription profiles. 

First, AirOn eSIM management can download the subscription profile into a new device, anywhere in the world and anytime the customer chooses; and second, AirOn can provide the lifetime remote management of the eUICC and its subscription profiles. 

------Terraform------------
Example: Terraform and Ansible. You use Terraform to deploy all the underlying infrastructure, including the network topology (i.e., VPCs, subnets, route tables), data stores (e.g., MySQL, Redis), load balancers, and servers. You then use Ansible to deploy your apps on top of those servers.

This is an easy approach to start with, as there is no extra infrastructure to run (Terraform and Ansible are both client-only applications) and there are many ways to get Ansible and Terraform to work together (e.g., Terraform adds special tags to your servers and Ansible uses those tags to find the server and configure them). The major downside is that using Ansible typically means you’re writing a lot of procedural code, with mutable servers, so as your code base, infrastructure, and team grow, maintenance may become more difficult.

--------------Jenkins----------------

It is a server-based application and requires a web server like Apache Tomcat. It is written in Java. if your team is developing a project, Jenkins will continuously test your project builds and show you the errors in early stages of your development

----------------GitHub-----------------

GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.

you can do the changes in separate branch and commit it and then pull request(When you open a pull request, you’re proposing your changes and requesting that someone review and pull in your contribution and merge them into their branch. Pull requests show diffs, or differences, of the content from both branches.) after the succesful review , deploy it, if it successful then merge with main branch. Or else try again.

 0008004401837
 
 Requirements:

terraform installed on jenkins
correct plugin installed on jenkins
github access token
aws credentials
s3 bucket

egress {
    from_port   = 0
    to_port     = 0
    protocol    = "-1"
    cidr_blocks = ["0.0.0.0/0"]
	 }

git init
git add .
git config --global user.email "vivekkrdixit"
git commit -m "First commit"
git remote add origin "url"
git remote -v ( to verify )
git push origin master

Plugins Required
Workspace Cleanup Plugin
Credentials Binding Plugin
AnsiColor Plugin
GitHub Plugin
Pipeline Plugin
CloudBees AWS Credentials Plugin
GitHub Pull Request Builder
 
------------ Virtualization v/s Cloud ----------------
 Virtualization: – The ability to run multiple operating systems on a single physical system at the same time and share the underlying hardware resources • Cloud Computing: – “The provisioning of services in a timely (near on instant), on-demand manner, to allow the scaling up and down of resources”

Cloud computing takes virtualization to the next step

• You don’t  have to own the hardware • You “rent” it as needed from a cloud • You get billed only for what you used • There are public clouds – e.g. Amazon, and now many others (Microsoft, IBM, Google, and so on ...) • A company can create a private one – With more control over security, etc.
 
---------- steps to integrate jenkins,github and terraform   --------------
 Install git --> go to Global tool configuration (Jenkins) -->give path to git executable (Ex - C:\Program Files\Git\bin\git.exe)
 create aws s3 bucket for maintenance of state remotely
 then pass the local state file to s3 backend
 prepare module files and jenkinsfile put it on github
 Go to github settings -> under developer setting --> create personal token for Jenkins --> make sure to check repo and  admin_repo --> you will get a token
 go to jenkins --> configure system --> github --> set the connection --> use the same token got in above step in secret (while creating credentials)
 then press on test connection --> You will see a message like "Credentials verified for user vivekkrdixit, rate limit: 4999" if connection is success. --> once done, save it.
 then , go to credentials --> and create two more credentials --> one for aws and another for github (cloning)
	1.credentials --> global credentials --> Add credentials --> this time use (username with password) and use same token for password
	2.credentials --> kind:aws credentials --> ID would be as same as you have mentioned in the jenkinsfile. --> provide access key ID and secret acess key-->save	
 now, click on create new item jobs --> item name and choose multibranch pipeline --> click ok
	under branch sources select github and add all the details (you will see credential 1 and choose)--> fill owner and repository to use -->save
	It will start scanning the files in the repository and prepare the build
	also, you can go to settings --> webhooks in github webpage and see, webhook has been created.
	once, build is passed , you can see pipeline under branch name -->	"build now"
	press build and go to console output.
	Once, build is successful, we can go to your main.tf file in github and do some changes and commit change(thorugh another branch) to check if pull reuest is happening without any issues.
	Under setting(github) --> branches --> branch protection rule --> create
	
	Note: To set up the webhook , please refer : https://dzone.com/articles/adding-a-github-webhook-in-your-jenkins-pipeline
	
	
Sonarqube 8ca0418cd085a0c591a78fcf3bc2fb6c4f07e2d7 token
----------------- git flow init --------------------------	
	
The overall flow of Gitflow is:

A develop branch is created from master
A release branch is created from develop
Feature branches are created from develop
When a feature is complete it is merged into the develop branch
When the release branch is done it is merged into develop and master
If an issue in master is detected a hotfix branch is created from master
Once the hotfix is complete it is merged to both develop and master


-------------------- SonarQube ------------------ used for inspect code and performs automated review.

Install Java 11 before installing sonarqube
Go to http://localhost:9000 and check if it up
Install Sonar scanner for Jenkins from update center and also on windows and defines the location of bin in PATH
Go to global configuration tool -> under Sonar Scanner -> give any name and path of the sonarscanner installer.
Now go to configure system under manage jenkins and fill the details for sonarqube servers and tick inject and save.
Go to http://localhost:9000 --> management-> user -> security -> click on token and generate one and save the credential on jenkins.
