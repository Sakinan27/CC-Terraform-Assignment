# CC-Terraform-Assignment
Sakina Terraform Assignment 

# USING TERRAFORM, CREATING A FILE WITH EXTENSION tf
code main.tf
code variable.tf
code output.tf

# In terminal 
~/.aws/credentials


# In Text Editor –  paste the Credentials 
# Copy the configuration from AWS – go to AWS CLI:
[default]
aws_access_key_id=ASIAV4ICCXFK3L6I7JMB
aws_secret_access_key=DJu+6ylVufyKbMnUiRblThkjp+sjEb8Niv7pxSVu
aws_session_token=FwoGZXIvYXdzEO7//////////wEaDKeeeCo4wHFpT3f4ACLRAcskkTQPUgcJfbEVMhmjLBxeGlwSku+rkeR/fmYlBEI3oSTj1FG9bg3MF1H/dF10DhESa03/MN5qduxO/6h0Bx1ELiJs28Fk26Ycbu5uoskBLxJ61hfz241V+BdnFDgLdEcmCoATm3Y6u8DmZK2u+UHybbv39xOmodmGMnPDLvsCpl5qOw8SNkJky2VnewaaveTF7302it2gNnIvgXfJ2a88EgUgxRwKTiaJUMesRmfqJpmMOctVTHjtMP8eJF7nhNtFXFxXTSG7lltBfzQzFF0HKOXfxJQGMi2PiqvgN4PaKmJb9aqQkKLvH6jmmGCMFxYEdOJCqOX+IE+FDOw6OXa0Y/x/7HE=


aws s3 ls


# USING TERRAFORM, CREATING A FILE WITH EXTENSION tf
code main.tf
code variable.tf
code output.tf


# MAIN.tf
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
variable "instance_name" {
  description = "Value of the Name tag for the EC2 instance"
  type        = string
  default     = "ExampleAppServerInstance2"
}



# TO CHANGE THE LOCATION OF STATE FILE FROM LOCAL TO S3
terraform {
    backend "s3"{
        bucket = "my-sakina-test-bucket-cc2022-onsite-34"
        key = "terraform-state.state"
        region ="us-east-1"
    }
}
