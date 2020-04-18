terraform {
	backend "s3" {
	
	bucket         = "Snobbish_state"
    key            = "myuser/s3/terraform.tfstate"
    region         = "us-east-2"
	
	dynamodb_table = "Snobbish_lock"
    encrypt        = true
  }
}


 0008004401837
 how to use Terraform as a team