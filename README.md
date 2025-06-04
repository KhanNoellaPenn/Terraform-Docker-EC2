# Terraform AWS EC2 Docker Setup
# Introduction
This project uses Terraform to automate the provisioning of an AWS EC2 instance and installs Docker on it using a startup script. It's designed to demonstrate infrastructure as code (IaC) practices by setting up a lightweight, Docker-ready server in minutes. Ideal for developers, DevOps learners, or anyone looking to streamline cloud infrastructure deployment, this project combines the power of AWS, Terraform, and shell scripting to create a repeatable and reliable setup.
### Project structure
To work with this project, you need to have a code editor installed I used Visual Studio Code (VS Code)[(https://code.visualstudio.com/)] , along with the [Terraform extension](https://marketplace.visualstudio.com/items?itemName=HashiCorp.terraform) for syntax highlighting and linting. You must also install [Terraform CLI](https://developer.hashicorp.com/terraform/downloads) and ensure it’s accessible from your terminal. Additionally, you’ll need an AWS account with programmatic access configured using the [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) (`aws configure`). Make sure you have a valid EC2 key pair created in your AWS region for SSH access, and a basic understanding of AWS networking concepts like VPCs, subnets, and security groups will be helpful for customizing the infrastructure.
### Setup Instructions
Follow these steps to deploy the EC2 instance with Docker installed:
### Step 1 Clone the Repository
- git clone https://github.com/KhanNoellaPenn/terraform-docker-ec2.git
- cd terraform-docker-ec2
### Step 2
- create a folder for your project on VS code and create the following files in the project folder
 #### main.tf # Main Terraform configuration
 ![2025-06-02 16_33_45-main tf - ec2 - Visual Studio Code](https://github.com/user-attachments/assets/f9c5cb03-c585-4acc-a8f8-7028927fca94)
 
 #### variables.tf # 
 - declare variables like the ami
NB: always remember to enter valid ami
 #### network.tf # for network configuration
 - Ensure to use public subnet 
 ![2025-06-02 16_44_16-network tf - ec2 - Visual Studio Code](https://github.com/user-attachments/assets/71fe8b50-57fa-4792-a973-d19fed5b4134)
 
 #### install-docker.sh # User data script to install Docker
 ![2025-06-02 16_46_15-install-docker sh - ec2 - Visual Studio Code](https://github.com/user-attachments/assets/90e20028-dea1-4926-a46b-ab0c73731ecd)

 #### security group.tf # for the security group settings
 - Ensure to allow ssh
 ### Step 3 Initialize Terraform 
 - run terraform init on terminal
 
![2025-06-02 18_33_41-2025-05-31 15_42_07-Greenshot init](https://github.com/user-attachments/assets/21812ffc-ada9-4419-a20d-94ce217c4d5a)

 ### **Step 4 Review the Plan - run terraform plan on terminal**
 - Before creating any resources, it's important to review the Terraform execution plan, to see a detailed preview of what Terraform intends to do — including what resources will be created, changed, or destroyed. This helps ensure your configuration is correct and avoids any unintended changes to your AWS environment.
 after you have verified that your configurations gives the desire outcome we proceed to step 5 which is
 
 ![2025-06-02 17_57_20-2025-05-31 15_43_31-Greenshot plan 22](https://github.com/user-attachments/assets/4b1ef66e-bee1-442c-8f90-cfe2e9f7844a)

 ### Step 5 Apply the Configuration - run terraform apply
- confirm apply with a yes
 
 ![2025-06-02 18_06_21-2025-05-31 15_44_00-Greenshot apply1](https://github.com/user-attachments/assets/0bb22223-a8e1-4e62-8513-28def8b7e1ac)

 ### Step 6 Verifying Docker 
 Once the EC2 instance is running, you can ssh  into it and verify that Docker was successfully installed by;
  - Connect to the instance using SSH with your private key  - ssh -i docker-server.pem ec2-user@<public-ip>
  - After logging in, check the Docker version to confirm it's installed   -   docker --version
    
 ![2025-06-02 18_08_48-2025-05-22 13_35_15-Greenshot docker installed](https://github.com/user-attachments/assets/f3b643b7-936a-49f4-a07d-a77779e9224f)



 
