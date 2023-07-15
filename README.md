# Full Stack Web Application - Phase 7
In this section, we will learn how to build the basic Infrastructure

This phase includes

- Building Basic Infrastructure with Terraform on AWS
- Topics Covered
  - **Terraform** 
    - Actions : All that followed in previous Phases
  - **Cloud** : AWS
    - Network Resources such as VPC, IGW, NGW, Route, RT, Subnet, Default SG
    - Storage Resources such as S3
  - **Scripting**
    - Actions : Shell Script to automate Build & Deploy

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


 ### 1. Automate Build & Deploy
In this section we are going to write `Shell Script` to automate the build and deploy of the 3 tier application (that we manually validated in `Phase-1`) in AWS EC2 instance.

 ### 2. Testing
Test the application end-to-end and confirm if all is working as expected.

Post to the validation share the shell script to me to validate and use it for upcoming phases
    
  *Note it is not necessary to build the entire AWS resources, rather you use the* `phase-2` *terraform to just create the instance*
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
4. [Phase - 7 : Infrastructure by Terraform (Terraform Import , Functions)](https://github.com/jumisa/ems-ops/tree/phase-7)