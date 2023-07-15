# Full Stack Web Application - Phase 7
In this section, we will learn how to build the basic Infrastructure

This phase includes

- Building Basic Infrastructure with Terraform on AWS
- Topics Covered
  - **Terraform** 
    - Concepts : Import, Functions
    - Actions : All that followed in previous Phases
  - **Cloud** : AWS
    - Network Resources such as VPC, IGW, NGW, Route, RT, Subnet, Default SG
    - Storage Resources such as S3

For terraform basic tutorial : [Terraform Tutorial](infra/terraform/README.md)
For previous phases : [Project Phases](#project-phases) 

### Architecture
Following Architecture will be built on our Infrastructure
![Screenshot](img/module-vpc-ec2-sg.png)

  
## Cloud Resources 
All the infrastructure related codes are present under the folder `infra` and IaC is under `terraform`
### 0. Pre-requisites
Before making the hands dirty, there are few things to understand about terraform code such as how to find appropriate resource?, what are all the attributes need? etc
- Always refer terraform documentation for any type of resources (implemenatation may differ terraform version to version)
- Once after the `Architecture` is signed off from the customer/architect, decide on TF version for the project and startup TF project folder structure (that we learnt in `Phase - 3`)


> **Let's Get Started**

 ### 1. Import
In this section we are going to learn what is `Import` in terraform.

A **import** is a terraform command (till version 1.5) that is used to import the configuration for the AWS resources that are created ie in other words when there is a need to write an IaC for already existing/running infrastructure.

Let us assume that we already have an EC2 machine running in AWS account and we have the terraform code for EC2 module which is not applied. 
So in this case we will be having no values / metadata for this EC2 instance in our terraform state file.

But when we try to run `terraform plan` then it will show that it is going to create an EC2 instance on the AWS account which we dont wanted to create, so the option is to `import` the existing EC2 instance.


1. connect to AWS account, get the Instance ID
2. if the EC2 code in TF is written in module then 
   ```
   terraform import aws_instance.foo i-abcd1234
   ```
3. if in resource block only
   ```
   terraform import module.foo.aws_instance.bar i-abcd1234
   ```
4. if the resource has count described
   ```
   terraform import 'aws_instance.baz[0]' i-abcd1234
   ```
   
Please verify the state file for the successfull import of the resources


 ### 2. Functions
In this section we are going to learn what is `Functions` in terraform.

There are several fucntions in terraform which cannot be writted on this single readme.
Basically functions are used for minimizing the codes, repeating the same code in several places. 

Please focus on built0in fuctions of terraform from 
https://developer.hashicorp.com/terraform/language/functions
    
 ### 3. Destroy All
 #### - Destroy the infrastructure
 - reun `terraform destroy` to destroy all the resources created by the terraform code.


### Project Phases
-------
1. [Phase - 0 : Full Stack App Deployment (Manually)](https://github.com/jumisa/ems-ops/tree/phase-0)
1. [Phase - 1 : Full Stack App Deployment (Daemonize)](https://github.com/jumisa/ems-ops/tree/phase-1)
1. [Phase - 2 : Infrastructure by Terraform (Basics)](https://github.com/jumisa/ems-ops/tree/phase-2)
1. [Phase - 3 : Infrastructure by Terraform (Network Resource)](https://github.com/jumisa/ems-ops/tree/phase-3)
1. [Phase - 4 : Infrastructure by Terraform (Terraform Modules)](https://github.com/jumisa/ems-ops/tree/phase-4)
2. [Phase - 5 : Infrastructure by Terraform (Terraform State)](https://github.com/jumisa/ems-ops/tree/phase-5)
3. [Phase - 6 : Infrastructure by Terraform (Terraform Workspace)](https://github.com/jumisa/ems-ops/tree/phase-6)