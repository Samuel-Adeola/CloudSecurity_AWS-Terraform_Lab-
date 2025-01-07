## Title: Building a Cybersecurity Home Lab for in-depth investigation and threat hunting with AWS Services Using Terraform

## 1.0	Background Overview
The recent development in IT industry has necessitated the use of necessary technology and tool to achieve the result. This is not limited to the use of Infrastructure as Code in automating security systems at every stages.  This project focuses on using Terraform to provision and configure a homelab environment on AWS Cloud with AWS services for in-depth investigation and threat hunting. The homelab includes two victim workstations, and one for Blue Team (defending the environment), one for Red Team (simulating attackers). The goal is to simulate cybersecurity scenarios for learning and testing incident detection, response, and remediation techniques.

## 1.0	Introduction
As the world becomes increasingly digital, the frequency and sophistication of cyberattacks continue to rise, making it crucial for cybersecurity professionals to stay ahead of emerging threats. In-depth investigation and threat hunting are vital practices for identifying, analyzing, and mitigating potential security incidents within any network or cloud environment. To effectively train and test cybersecurity skills, hands-on experience with real-world scenarios is essential. This project focuses on building a comprehensive cybersecurity home lab that simulates both attack and defense environments using AWS services and Infrastructure as Code (IaC) principles via Terraform.
The lab is designed to replicate the dynamics of a real-world enterprise network, consisting of two workstations: one for the Blue Team, tasked with defending the environment, and one for the Red Team, simulating malicious attackers. The Red Team workstation is equipped with tools and frameworks to emulate various types of cyberattacks, including penetration testing and exploit simulations. On the other hand, the Blue Team workstation is configured with various monitoring, detection, and response tools, enabling the detection and mitigation of simulated threats in real time.
By leveraging Terraform, a powerful IaC tool, the entire infrastructure can be provisioned, configured, and maintained in an automated, repeatable, and consistent manner. Terraform allows for the dynamic creation of resources in AWS, including EC2 instances, security groups, IAM roles, and networking setups. This project utilizes a variety of AWS services such as EC2 for virtual machines, S3 for storage, VPC for networking, and CloudWatch for monitoring and log analysis. The combination of Terraform and AWS services enables an efficient, scalable, and cost-effective environment that mirrors real-world cybersecurity challenges.


The primary objective of this lab is to create a realistic and interactive environment for simulating cybersecurity incidents, which can be used for training, research, and skill development. The home lab environment is purposefully designed with distinct components, including: 

•	Two victim workstations for threat simulations and two team-specific setups.

•	Blue Team Workstation: Focused on monitoring, detecting, and responding to malicious activities.

•	Red Team Workstation: Simulating advanced persistent threats (APTs), penetration testing, and attack vectors.

This lab provides a hands-on platform for executing and analyzing real-world scenarios, such as network intrusions, malware attacks, and incident response workflows. The incorporation of AWS services enhances the scalability and reliability of the lab, while Terraform ensures rapid deployment and teardown of environments, promoting repeatability and experimentation.


What is Terraform?
Terraform is an infrastructure as code tool that lets you build, change, and version cloud and on-prem resources safely and efficiently.
HashiCorp Terraform is an infrastructure as code tool that lets you define both cloud and on-prem resources in human-readable configuration files that you can version, reuse, and share. You can then use a consistent workflow to provision and manage all of your infrastructure throughout its lifecycle. Terraform can manage low-level components like compute, storage, and networking resources, as well as high-level components like DNS entries and SaaS features.

The providers are publicly available on the Terraform Registry, including Amazon Web Services (AWS)and others including Azure, Google Cloud Platform (GCP), Kubernetes, Helm, GitHub, Splunk, DataDog, and many more. (https://registry.terraform.io/browse/providers)

 

The core Terraform workflow consists of three stages:

•	Write: You define resources, which may be across multiple cloud providers and services. For example, you might create a configuration to deploy an application on virtual machines in a Virtual Private Cloud (VPC) network with security groups and a load balancer.

•	Plan: Terraform creates an execution plan describing the infrastructure it will create, update, or destroy based on the existing infrastructure and your configuration.

•	Apply: On approval, Terraform performs the proposed operations in the correct order, respecting any resource dependencies. For example, if you update the properties of a VPC and change the number of virtual machines in that VPC, Terraform will recreate the VPC before scaling the virtual machines.



## 2.0	Project Objective
•	Automate the deployment of infrastructure using Terraform as an Infrastructure as Code (IaC) tool.

•	Provide a controlled environment for exploring cybersecurity concepts like monitoring, intrusion detection, and incident response.

•	Develop a scalable cybersecurity home lab on AWS to simulate real-world threat detection, response, and mitigation scenarios.

Project Goals
1.	Automate the setup of a cybersecurity lab with AWS resources.
2.	Integrate tools for red and blue team activities.
3.	Simulate realistic attack scenarios and document response processes.
4.	Analyze and log network traffic for security analysis.


Scope
The lab will be capable of supporting:
•	Blue Team Activities: Defensive tasks like monitoring, detecting threats, and analyzing logs.
•	Red Team Activities: Offensive techniques such as penetration testing and simulated attacks.


## 3.0	Project Requirements and Technical Tools
The tools required for this project include the following:

•	Virtual machine: Windows 10 installed on VirtualBox (run a powershell script to configure the ADLAB machines)

•	An AWS Account: Create  AWS Free Tier account 

•	AWS Cli installed

•	Terraform configuration files (Source : https://github.com/MalTrakLab/purple-team-cloud-lab)

•	Terraform Setup: Install and configure Terraform for AWS by setting up AWS CLI and access credentials.



## 4.0	Methodology
Virtual machine: Windows 10 installed on VirtualBox
Installation
•	To install, you will need to follow these steps:
•	AWS Account: Create  AWS Free Tier account with the required resources EC2 (For deploying workstations - Blue Team, Red Team, and victim machines), VPC (For creating isolated networking environments), IAM (AdminFullAccess), Security Groups, key Pair, AWS Command Line Interface (CLI). 
•	(AWS Free Tier Account - https://aws.amazon.com/free/compute/?p=ft&z=subnav&loc=3)
•	create a user with administrator permissions and get its ACCESS KEY and SECRET KEY
•	Switch to eu-west-1 region in your aws console (on the browser)
•	Go to EC2 --> Instances --> Key Pair and create a key with name ec2_key_pair (All lowercase) and save the .pem key file
•	Copy your ec2_key_pair.pem file to your C:\Users\<your username>\.ssh folder and rename it to id_rsa
•	AWS Cli installed

 

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

•	Terraform configuration files downloaded and copied to any folder in %PATH% Environment (Source : https://github.com/MalTrakLab/purple-team-cloud-lab) 
•	Open the command prompt (cmd) and run aws configure  
•	Provide the ACCESS KEY, SECRET KEY, the region as eu-west-1
•	Open cmd again, go to the PurpleTeam lab directory (this project folder) and 
•	run: terraform init and then terraform apply and type "yes"
•	This will  40 mins to complete. The Purple team lab will be created in AWS. 
•	To destroy, run terraform destroy --auto-approve

Note: Just a reminder, keeping it running will cost you money.
To change to prefer the region, update the main.tf file and change the region and create an ec2_key_pair in the region you choose as these are not transferrable between regions.

## 5.0	Result:
# 5.1 Step 1: AWS Setup
5.1.1 AWS Account: Create  AWS Free Tier account with the required resources EC2 (For deploying workstations - Blue Team, Red Team, and victim machines), VPC (For creating isolated networking environments), IAM (AdminFullAccess), Security Groups, key Pair, AWS Command Line Interface (CLI). 

(AWS Free Tier Account - https://aws.amazon.com/free/compute/?p=ft&z=subnav&loc=3)
5.1.2 Create AWS Full administrative Access for user in IAM

![AWS Fig2](https://github.com/user-attachments/assets/b2c32ea6-0b2d-4516-86fa-96e1b5aad79e)


![AWS Fig5](https://github.com/user-attachments/assets/44b607df-3cae-4bfe-b805-d3fd7c13ca53)


To create Access Key:

![AWS Fig8](https://github.com/user-attachments/assets/bdcba978-6df5-4a7e-87d7-bb833e1f8e52)

 
![AWS Fig9](https://github.com/user-attachments/assets/d6627535-432b-4e4f-8981-15956af55843)

Access key and Secret access key created. These keys should be save and will be used in the future:

![AWS Fig11](https://github.com/user-attachments/assets/ca353416-1dbc-407c-b61c-0959d0c033cd)



![AWS Fig12](https://github.com/user-attachments/assets/b40c1c38-5ded-4898-8e75-b77a68b4509c)

5.1.3	Create Key pair
Search for ec2. On the dashboard, select Keypair under the Resources

![AWS Fig13](https://github.com/user-attachments/assets/6f81757b-728e-459a-8e7a-d3f7cb2f7e27)



![AWS Fig15](https://github.com/user-attachments/assets/4b7ff9a0-959f-4708-aeaa-1d633e1e3e29)

Keypair – ec2_key_pair created in the folder Downloads. Select the Downloads:

![AWS Fig17](https://github.com/user-attachments/assets/c1b60dff-c3e3-47c3-b55c-cacd66427f84)


Created a folder named “.ssh” in C:\Users\samar

![AWS Fig18](https://github.com/user-attachments/assets/ce821717-adbc-4cf8-8d17-f74b16e7d2c3)


 

 

Save the Key – ec2_key_pair in .ssh folder 

![AWS Fig19](https://github.com/user-attachments/assets/34eb840f-8e35-4cee-9043-7f35652c9ccc)

Rename the “ec2_key_pair” to id.rsa

![AWS Fig20](https://github.com/user-attachments/assets/e927e44b-0db3-4ad5-9361-0a2034717d95)


5.1.3 – Installing AWS Command Line Interface
Browse 
Scroll down to Windows  and copy the command:

![AWS Fig21](https://github.com/user-attachments/assets/df85b595-7926-4fa9-b220-46683b6ac2d2)



Paste the command in the CMD

![AWS Fig22](https://github.com/user-attachments/assets/b2dbf79a-c41a-4e69-9dcc-aaee58224310)


![AWS Fig23](https://github.com/user-attachments/assets/a91efb70-40ec-446f-9a08-3ac892e8b578)


![AWS Fig24](https://github.com/user-attachments/assets/cc233f98-daec-478d-9e29-b0f9081f0d50)

![AWS Fig26](https://github.com/user-attachments/assets/b02a9d89-2223-495d-bac9-6ac2537b9748)


AWS CLI successfully installed:

![AWS Fig29](https://github.com/user-attachments/assets/545fbc57-5bfc-4cf2-860b-78d3333fdeac)


Input the Access key and Secret access key previously generated


![AWS Fig30a](https://github.com/user-attachments/assets/e5c67662-dfd5-41de-b868-cad3f914f462)

# 5.2 Terraform Installation
Steps to install 

![Terraform Fig1](https://github.com/user-attachments/assets/812bd1e3-18ed-463e-b29b-c18f8c54d7a2)

Terraform downloaded for Windows from

![Terraform Fig2](https://github.com/user-attachments/assets/09707c82-c02b-44c3-b4c5-d742b6769343)

Terraform.exe extracted and save in Created a folder named “terraform” in C:\Windows

![Terraform Fig4](https://github.com/user-attachments/assets/c38a3306-6490-4a22-bcdb-454e8dd58736)


5.2.2	Download Terraform configuration files https://github.com/Samuel-Adeola/PurpleTeam_Cloud_Lab

![Terraform Fig5](https://github.com/user-attachments/assets/febc5ae2-7da4-47c9-9d45-36b14f8b96c1)


![Terraform Fig6](https://github.com/user-attachments/assets/a90ac936-d7f4-4c17-88ac-9cb500473230)


![Terraform Fig7](https://github.com/user-attachments/assets/61955f8b-091f-4ecb-b370-2a5ac883aab1)


![Terraform Fig8](https://github.com/user-attachments/assets/ac08792e-7fb6-40fc-817c-8b3fcbf32b8d)


![Terraform Fig8a](https://github.com/user-attachments/assets/28b3634a-1cbc-4090-8649-510cd066f348)

 
5.2.3	Run Terraform configuration files 
Open cmd and navigate to terraform configuration files location

![Terraform Fig9](https://github.com/user-attachments/assets/6a806b4c-cf7c-4624-90f0-5f5a4fb6b5bf)

Terraform Fig 9

Run terraform init and terraform apply:

![Terraform Fig11a](https://github.com/user-attachments/assets/492b73bc-7a46-4851-aa0f-006c412ded88)


Machines installation completed

![Terraform Fig12](https://github.com/user-attachments/assets/eb31fcf4-a2d5-49d8-b5d7-9de0a9bc1aaa)


![Terraform Fig12](https://github.com/user-attachments/assets/33a9c69a-4b3d-447f-89d8-d546d3111560)


Terraform Setup: Install and configure Terraform for AWS by setting up AWS CLI and access credentials.

Workstation Configurations: For Bue Team, Red Team and Victim Workstation

Blue Team HELK machine:  this machine is also Amazon Linux 2 with size t2.large (8 GB, 2 vcpu) and 30 GB of disk space. HELK integrates multiple technologies, making it versatile for cybersecurity operations such as ELK Stack, Elasticsearch, Logstash, Kibana, Apache Kafka, Spark, Jupyter Notebooks.

Red Team Caldera machine:  This machine is Amazon Linux 2 (Redhat based) with size t2.micro (no cost with AWS Free tier). 
