# CC-Terraform-Assignment
Sakina Terraform Assignment 

# USING TERRAFORM, CREATING A FILE WITH EXTENSION tf
code main.tf
code variable.tf
code output.tf


# MAIN.tf
# TO CHANGE THE LOCATION OF STATE FILE FROM LOCAL TO S3
terraform {
    backend "s3"{
        bucket = "my-sakina-test-bucket-cc2022-onsite-34"
        key = "terraform-state.state"
        region ="us-east-1"
    }
}



# TO CREATE EC2 INSTANCE IN AWS THROUGH TERRAFORM
resource "aws_instance" "web_server" {
  ami          = "ami-06eecef118bbf9259"
  instance_type = "t2.micro"
  tags = {
    Name = var.instance_name
  }
}


# TO CREATE S3 BUCKET USING TERRAFORM 
resource "aws_s3_bucket" "main_s3_bucket" {
  bucket = "my-sakina-test-bucket-cc2022-onsite-34"
  tags = {
    Name        = "My bucket"
    Environment = "Dev"
  }
}



# VARIABLE.tf 
