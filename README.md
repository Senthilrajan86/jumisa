# Full Stack Web Application - Phase 6
In this section, we will learn how to build the basic Infrastructure

This phase includes

- Building Basic Infrastructure with Terraform on AWS
- Topics Covered
  - **Terraform** 
    - Concepts : Workspace
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

 ### 1. Workspace
In this section we are going to learn what is `Workspace` in terraform.

A **workspace** is to isolate the terraform configuration by enviroment. Simply manages multiple state file for a same working directory

In other words , the same terraform code base can be used to create AWS resources in multiple AWS accounts, environments. To isolate their states and managing with ease `workspaces` are used.

- Variable values for each workspace must declared in specfic for each, example: `WORKSPACE-ems.tfvars`
- State files can be on local or remote backend
- Remaining all works the same way as on previous phases  

#### - Setup
This section explains about how to setup the workspace and deploy with terraform
1. First thing is to create `.tfvars` file for the workspace/environment for which the values of variables must be passed
    a. in this case `dev.tfvars` file is created inside the folder `env-config/tfvars`
    b. there are few variables with values in this. You have to migrate all the variable values from `variables.tf` file to `dev.tfvars` using the sample shared
1. Create a workspace
    - `env=dev`
    - `terraform workspace new ${env}`
2. Select a workspace for which the terraform config to be applied (can select the workspace only if it is already created)
    - `terraform workspace select ${env} `
 

#### - Workspace command
`terraform workspace list` - to list the workspaces on the working directory of terraform
`terraform workspace new` - to create new workspace  
`terraform workspace select` - to choose the workspace that needs the resources to be created
`terraform workspace show` - to show what is the current workspace you are in
`terraform workspace delete` - to delete a workspace

 ### 2. Re-Initiate, Plan Terraform Modules
In this section we are going to perform the terraform actions post `s3 backend, remote state` configuration. 

- Try the following command and observe 
  - terraform init 
  - terraform plan -var-file=env-config/tfvars/${env}.tfvars
  - terraform apply -var-file=env-config/tfvars/${env}.tfvars
    
### 3. Understand Remote State
 #### - Connect to AWS S3 and Look at the terraform state file created
 - `dev.tfstate` is the file that holds all the infrastructure details and metadata

 ### 4. Destroy All
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