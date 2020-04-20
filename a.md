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
 
 
 
 create aws s3 bucket for maintenance of state remotely
 then pass the local state file to s3 backend
 prepare module files and put it on github
 Go to github settings -> under developer setting --> create personal token for Jenkins --> make sure to check repo and  admin_repo --> you will get a token
 go to jenkins --> configure system --> github --> set the connection --> use the same token got in above step in secret (while creating credentials)
 then press on test connection --> You will see a message like "Credentials verified for user vivekkrdixit, rate limit: 4999" if connection is success.
 
 