# Terraform AWS EC2 Docker Setup
## This project provisions an EC2 instance on AWS using Terraform and installs Docker on it automatically via a user data script.
### Project structure
To work with this project, you need to have a code editor installed I used Visual Studio Code (VS Code)[(https://code.visualstudio.com/)] , along with the [Terraform extension](https://marketplace.visualstudio.com/items?itemName=HashiCorp.terraform) for syntax highlighting and linting. You must also install [Terraform CLI](https://developer.hashicorp.com/terraform/downloads) and ensure it’s accessible from your terminal. Additionally, you’ll need an AWS account with programmatic access configured using the [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) (`aws configure`). Make sure you have a valid EC2 key pair created in your AWS region for SSH access, and a basic understanding of AWS networking concepts like VPCs, subnets, and security groups will be helpful for customizing the infrastructure.
### Setup Instructions
Follow these steps to deploy the EC2 instance with Docker installed:
### Step 1 Clone the Repository
git clone https://github.com/KhanNoellaPenn/terraform-docker-ec2.git
cd terraform-docker-ec2
### Step 2
create a folder for your project on VS code and create the following files in the project folder
 #### main.tf # Main Terraform configuration
 ![2025-06-02 16_33_45-main tf - ec2 - Visual Studio Code](https://github.com/user-attachments/assets/f9c5cb03-c585-4acc-a8f8-7028927fca94)
 
 #### variables.tf # 
 declare variables like the ami
NB: always remember to enter valid ami
 #### network.tf # for network configuration
 Ensure to use public subnet 
 ![2025-06-02 16_44_16-network tf - ec2 - Visual Studio Code](https://github.com/user-attachments/assets/71fe8b50-57fa-4792-a973-d19fed5b4134)
 
 #### install-docker.sh # User data script to install Docker
 ![2025-06-02 16_46_15-install-docker sh - ec2 - Visual Studio Code](https://github.com/user-attachments/assets/90e20028-dea1-4926-a46b-ab0c73731ecd)

 #### security group.tf # for the security group settings
 Ensure to allow ssh
 ### Step 3 Initialize Terraform 
 run terraform init on terminal
 ### Step 4 Review the Plan - run terraform plan on terminal
 Before creating any resources, it's important to review the Terraform execution plan, to see a detailed preview of what Terraform intends to do — including what resources will be created, changed, or destroyed. This helps ensure your configuration is correct and avoids any unintended changes to your AWS environment.
 after you have verified that your configurations gives the desire outcome we proceed to step 5 which is
 ### Step 5 Apply the Configuration - run terraform apply
 confirm apply witha yes and 

 
