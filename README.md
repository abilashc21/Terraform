# Terraform
first IAAC with terraform in GIT


provider "aws" {
  region = "us-west-2"
  access_key = ""
  Secret_key = ""
}
  
resource "aws_security_group" "terraform_SG" {
    name = "terraform_SG"
    
    ingress {
      from_port = 22
      to_port = 22
      protocal = "tcp"
      cidr = [ "0.0.0.0/0" ]
    }
    egress {
      from_port = 0
      to_port = 0
      protocal = "-1"
      cidr = [ "0.0.0.0/0" ]
    }
      
}

resource "aws_instance" "terraform" {
    ami = ""
    instance_type = ""
    vpc_security_group_ids = [ aws_security_group.terraform_SG.id ]
    tags {
      "name" = "terraform"
    }
}
