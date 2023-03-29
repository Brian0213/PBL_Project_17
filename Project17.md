# AUTOMATE INFRASTRUCTURE WITH IAC USING TERRAFORM. PART 2

## Networking

Private subnets & best practices
Create 4 private subnets keeping in mind following principles:

Make sure you use variables or length() function to determine the number of AZs
Use variables and cidrsubnet() function to allocate vpc_cidr for subnets
Keep variables and resources in separate files for better code structure and readability
Tags all the resources you have created so far. Explore how to use format() and count functions to automatically tag subnets with its respective number.

- Run the command below in command line:

`terraform plan`

- The screenshots below should display:

[Private Subnet Create](./images/priv-subnet-create1.PNG)

[Private Subnet Create](./images/priv-subnet-create2.PNG)

[Private Subnet Create](./images/priv-subnet-create3.PNG)

[Private Subnet Create](./images/priv-subnet-create4.PNG)

[Private Subnet Create](./images/priv-subnet-create5.PNG)

[Private Subnet Create](./images/priv-subnet-create6.PNG)

[Private Subnet Create](./images/priv-subnet-create7.PNG)

- A little bit more about Tagging
Tagging is a straightforward, but a very powerful concept that helps you manage your resources much more efficiently:

Resources are much better organized in ‘virtual’ groups
They can be easily filtered and searched from console or programmatically
Billing team can easily generate reports and determine how much each part of infrastructure costs how much (by department, by type, by environment, etc.)
You can easily determine resources that are not being used and take actions accordingly
If there are different teams in the organisation using the same account, tagging can help differentiate who owns which resources.

- Now you can tag all you resources using the format below in the main.tf file:

[Private Public Tag](./images/priv-pub-tag-update.PNG)

- NOTE: Update the variables.tf to declare the variable tags used in the format above;

[Variable Tf File](./images/vari-tf.PNG)

- Note: You can add multiple tags as a default set. for example, in out terraform.tfvars file we can have default tags defined:

[Terraform Tfvars File](./images/terratfvars-tf.PNG)

- Run the command below in command line:

`terraform plan`

- The screenshots below should display:

[Private Public Tag Plan Run Output](./images/priv-pub-tag-output1.PNG)

[Private Public Tag Plan Run Output](./images/priv-pub-tag-output2.PNG)

[Private Public Tag Plan Run Output](./images/priv-pub-tag-output3.PNG)

[Private Public Tag Plan Run Output](./images/priv-pub-tag-output4.PNG)

[Private Public Tag Plan Run Output](./images/priv-pub-tag-output5.PNG)

[Private Public Tag Plan Run Output](./images/priv-pub-tag-output6.PNG)

[Private Public Tag Plan Run Output](./images/priv-pub-tag-output7.PNG)

[Private Public Tag Plan Run Output](./images/priv-pub-tag-output8.PNG)

[Private Public Tag Plan Run Output](./images/priv-pub-tag-output9.PNG)

- The nice thing about this is – anytime we need to make a change to the tags, we simply do that in one single place (terraform.tfvars).

But, our key-value pairs are hard coded. So, go ahead and work out a fix for that. Simply create variables for each value and use var.variable_name as the value to each of the keys.
Apply the same best practices for all other resources you will create further.

Internet Gateways & format() function
Create an Internet Gateway in a separate Terraform file internet_gateway.tf:

[Internet Gateway File Create](./images/int-gw-tf.PNG)

- NAT Gateways
Create 1 NAT Gateways and 1 Elastic IP (EIP) addresses

Now use similar approach to create the NAT Gateways in a new file called natgateway.tf.

Note: We need to create an Elastic IP for the NAT Gateway, and you can see the use of depends_on to indicate that the Internet Gateway resource must be available before this should be created. Although Terraform does a good job to manage dependencies, but in some cases, it is good to be explicit.

You can read more on dependencies here

[Nat Gateway File Create](./images/int-gw-tf.PNG)

- Run the command below in command line:

`terraform plan`

- The screenshots below should display:

[Terraform Run after creation of Nat and Internet Gateway](./images/terform-output1.PNG)

[Terraform Run after creation of Nat and Internet Gateway](./images/terform-output2.PNG)

[Terraform Run after creation of Nat and Internet Gateway](./images/terform-output3.PNG)

[Terraform Run after creation of Nat and Internet Gateway](./images/terform-output4.PNG)

[Terraform Run after creation of Nat and Internet Gateway](./images/terform-output5.PNG)

[Terraform Run after creation of Nat and Internet Gateway](./images/terform-output6.PNG)

[Terraform Run after creation of Nat and Internet Gateway](./images/terform-output7.PNG)

[Terraform Run after creation of Nat and Internet Gateway](./images/terform-output8.PNG)

[Terraform Run after creation of Nat and Internet Gateway](./images/terform-output9.PNG)

[Terraform Run after creation of Nat and Internet Gateway](./images/terform-output10.PNG)

[Terraform Run after creation of Nat and Internet Gateway](./images/terform-output11.PNG)

[Terraform Run after creation of Nat and Internet Gateway](./images/terform-output12.PNG)

[Terraform Run after creation of Nat and Internet Gateway](./images/terform-output13.PNG)

- Create Route tables:

- Run `terraform plan` to create routes tables:

[Private Public Create Route Table](./images/pri-pub-rtb1.PNG)

[Private Public Create Route Table](./images/pri-pub-rtb2.PNG)

[Private Public Create Route Table](./images/pri-pub-rtb3.PNG)

[Private Public Create Route Table](./images/pri-pub-rtb4.PNG)

[Private Public Create Route Table](./images/pri-pub-rtb5.PNG)

[Private Public Create Route Table](./images/pri-pub-rtb6.PNG)

[Private Public Create Route Table](./images/pri-pub-rtb7.PNG)

[Private Public Create Route Table](./images/pri-pub-rtb8.PNG)

[Private Public Create Route Table](./images/pri-pub-rtb9.PNG)

[Private Public Create Route Table](./images/pri-pub-rtb10.PNG)

[Private Public Create Route Table](./images/pri-pub-rtb11.PNG)

[Private Public Create Route Table](./images/pri-pub-rtb12.PNG)

[Private Public Create Route Table](./images/pri-pub-rtb13.PNG)

[Private Public Create Route Table](./images/pri-pub-rtb14.PNG)

[Private Public Create Route Table](./images/pri-pub-rtb15.PNG)

[Private Public Create Route Table](./images/pri-pub-rtb16.PNG)

[Private Public Create Route Table](./images/pri-pub-rtb17.PNG)

- Run `terraform apply --auto-approve`

[Terraform Apply Output](./images/terra-app1.PNG)

[Terraform Apply Output](./images/terra-app2.PNG)

[Terraform Apply Output](./images/terra-app3.PNG)

- Create certificate:

- Create Loadbalancers:

[Securitygrp](./images/sec-Ib-output1.PNG)

[Securitygrp](./images/sec-Ib-output1.PNG)

[Securitygrp](./images/sec-Ib-output1.PNG)

[Securitygrp](./images/sec-Ib-output1.PNG)

[Securitygrp](./images/sec-Ib-output1.PNG)

[Securitygrp](./images/sec-Ib-output1.PNG)

[Securitygrp](./images/sec-Ib-output1.PNG)

[Securitygrp](./images/sec-Ib-output1.PNG)

[Securitygrp](./images/sec-Ib-output1.PNG)

[Securitygrp](./images/sec-Ib-output1.PNG)

[Securitygrp](./images/sec-Ib-output1.PNG)

[Securitygrp](./images/sec-Ib-output1.PNG)

[Securitygrp](./images/sec-Ib-output1.PNG)

[Securitygrp](./images/sec-Ib-output1.PNG)

[Securitygrp](./images/sec-Ib-output1.PNG)

[Securitygrp](./images/sec-Ib-output16.PNG)

[Securitygrp](./images/sec-Ib-output17.PNG)

- To create route 53 records & Certificate:

- Run `terraform apply --auto-approve` to create the records:

[Route53 Record Create](./images/route53-output-1.PNG)

[Route53 Record Create](./images/route53-output-2.PNG)

[Route53 Record Create](./images/route53-output-3.PNG)

[Securitygrp](./images/route53-output-4.PNG)

[Securitygrp](./images/route53-output-5.PNG)

[AWS Record Output](./images/route53-output-5.PNG)

[AWS Loadbalancer Output](./images/aws-loadbalancer.PNG)

[AWS Target Group Output](./images/aws-targetgrp.PNG)

- Add the following files in the project bastion.sh, tooling.sh, wordpress.sh, nginx.sh, asg-webserver.tf, output.tf:

Run `terraform apply --auto-approve` to create the autoscaling group:

[Autoscaling Output](./images/autoscalinggrp-output.PNG)

Run `terraform fmt` to format the files

Run `terraform plan` to eliminate errors

### STORAGE AND DATABASE

Run `terraform apply --auto-approve` to create rds

[AWS Database Output](./images/aws-db.PNG)

[AWS Filesystem Output](./images/aws-efs.PNG)

[AWS Rds Output](./images/aws-rds.PNG)

[AWS Launch Template Output](./images/aws-launchtemp.PNG)

[AWS Launch Template Output](./images/aws-autoscaling.PNG)

Useful Terraform Documentation, go through this documentation and understand the arguement needed for each resources:

RDS
EFS
KMS
Create Elastic File System (EFS)
In order to create an EFS you need to create a KMS key.

AWS Key Management Service (KMS) makes it easy for you to create and manage cryptographic keys and control their use across a wide range of AWS services and in your applications.

- Add the following code to efs.tf

- Let us create EFS and it mount targets- add the following code to efs.tf

Create MySQL RDS
Let us create the RDS itself using this snippet of code in rds.tf file:

- Before Applying, if you take note, we gave reference to a lot of varibales in our resources that has not been declared in the variables.tf file. Go through the entire code and spot this variables and declare them in the variables.tf file.

If you have done that well, you file should like this one below.

At this point, you shall have pretty much all infrastructure elements ready to be deployed automatically, but before we paln and apply our code we need to take note of two things;

we have a long list of files which may looks confusing but that is not bad for a start, we are going to fix this using the concepts of modules in Project 18
Secondly, our application wont work becuase in out shell script that was passed into the launch some endpoints like the RDs and EFS point is needed in which they have not been created yet. So in project 19 we will use our Ansible knowledge to fix this.
Try to plan and apply your Terraform codes, explore the resources in AWS console and make sure you destroy them right away to avoid massive costs.

- Additional tasks.

In addition to regular project submission include following:

Summarise your understanding on Networking concepts like IP Address, Subnets, CIDR Notation, IP Routing, Internet Gateways, NAT
Summarise your understanding of the OSI Model, TCP/IP suite and how they are connected – research beyond the provided articles, watch different YouTube videos to fully understand the concept around OSI and how it is related to the Internet and end-to-end Web Solutions. You don not need to memorise the layers – just understand the idea around it.
Explain the difference between assume role policy and role policy.