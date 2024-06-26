
---
n this challenge we will implement a simple `EC2` instance with some preinstalled packages.  
Utilize `/root/terraform-challenges/project-citadel` directory to store your Terraform configuration files.
-  AMI: ami-06178cf087598769c, use variable named `ami`
-  Region: eu-west-2, use variable named `region`
-  Instance Type: m5.large, use variable named `instance_type`
-  Elastic IP address attached to the EC2 instance
-  Create a terraform key-pair `citadel-key` with key_name `citadel`.
-  Upload the public key `ec2-connect-key.pub` to the resource. You may use the `file function` to read the the public key at `/root/terraform-challenges/project-citadel/.ssh`
-  Create a local-exec provisioner for the `eip` resource and use it to print the attribute called `public_dns` to a file `/root/citadel_public_dns.txt` on the iac-server
-  Install nginx on citadel instance, make use of the `user_data` argument.  
Using the file function or by making use of the heredoc syntax, use the script called `install-nginx.sh` as the value for the user_data argument.
---
### Answer:
---
-  `main.tf`
```
variable "region" {

  type = string

  default =  "eu-west-2"

}

resource "aws_key_pair" "citadel-key" {

  key_name   = "citadel"

  public_key = file("/root/terraform-challenges/project-citadel/.ssh/ec2-connect-key.pub")

}

  

resource "aws_instance" "web" {

  ami           = "ami-06178cf087598769c"

  instance_type = "m5.large"

  key_name = aws_key_pair.citadel-key.key_name

  user_data = file("/root/terraform-challenges/project-citadel/install-nginx.sh")

}

resource "aws_eip" "eip" {

  instance = aws_instance.web.id

  vpc = true

  provisioner "local-exec" {

   command = "echo ${self.public_dns} >> /root/citadel_public_dns.txt"

  }

}
```