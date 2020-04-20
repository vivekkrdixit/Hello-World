terraform {
	backend "s3" {
	
	bucket         = "Snobbish-state"
    key            = "myuser/s3/terraform.tfstate"
    region         = "us-east-2"
	
	dynamodb_table = "Snobbish_lock"
    encrypt        = true
  }
}


 0008004401837
 how to use Terraform as a team
 jenkins personal token from github : 3189876af59bc8271b5dbfa15821405ff01c3748
 
 Requirements:

terraform installed on jenkins
correct plugin installed on jenkins
github access token
aws credentials
s3 bucket

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
 
 create aws s3 bucket for maintenance of state remotely
 then pass the local state file to s3 backend
 prepare module files and jenkinsfile put it on github
 Go to github settings -> under developer setting --> create personal token for Jenkins --> make sure to check repo and  admin_repo --> you will get a token
 go to jenkins --> configure system --> github --> set the connection --> use the same token got in above step in secret (while creating credentials)
 then press on test connection --> You will see a message like "Credentials verified for user vivekkrdixit, rate limit: 4999" if connection is success. --> once done, save it.
 then , go to credentials --> and create two more credentials --> one for aws and another for github (cloning)
	1.credentials --> global credentials --> Add credentials --> this time use (username with password) and use same token for password
	2.credentials --> kind:aws credentials --> ID would be as same as you have mentioned in the jenkinsfile. --> provide access key ID and secret acess key-->save	
 now, click on create new jobs --> item name and choose multibranch pipeline --> click ok
	under branch sources select github and add all the details (you will see credential 1 and choose)--> fill owner and repository to use -->save
	It will start scanning the files in the repository and prepare the build
	also, you can go to settings --> webhooks in github webpage and see, webhook has been created.
	once, build is passed , you can see pipeline under branch name -->	"build now"
	press build and go to console output.
	Once, build is successful, we can go to your main.tf file in github and do some changes and commit change(thorugh another branch) to check if pull reuest is happening without any issues.
	Under setting(github) --> branches --> branch protection rule --> create