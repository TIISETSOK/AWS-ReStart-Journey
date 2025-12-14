# AWS Lab: Build Your VPC and Launch a Web Server

## Overview

### Customer Scenario
- In this lab,I had to use Amazon Virtual Private Cloud (VPC) to create your own VPC and add additional components to produce a customized network for a Fortune 100 customer.
- I also had to create security groups for the EC2 instances. 
- I then had to configure and customize an EC2 instance to run a web server and launch it into the VPC that looks like the following customer diagram.

### Customer Diagram
The customer is requesting the build of this architecture to launch their web server successfully.
<img width="881" height="437" alt="Screenshot 2025-12-15 010928" src="https://github.com/user-attachments/assets/7ee21f69-e8be-4f6f-b5d3-b8354305dc9b" />

---

## Task 1: 

**For the fist task i had to create a VPC**

### Step 1: Accessing the AWS Management Console

- I opened the AWS consile and selected VPC.

### Step 2: Creating the VPC

- In the Amazon VPC dashboard, I chose the **Create VPC** button to launch the VPC wizard.

### Step 3: Setring Up the VPC

- Once in the VPC wizard,I used the following parameters to configure the VPC settings.

### Step 4: I checked the Created VPC Workflow.

- Once I had successfully created the VPC, I saw a Success message in the Create VPC workflow.

 <img width="748" height="862" alt="image" src="https://github.com/user-attachments/assets/d5ba0f35-2c60-4289-ba3a-462199a13a1f" />


### Step 5: I reviewed the VPC

- I navigated to the Amazon VPC dashboard and selected **Your VPCs** to verify that the  VPC was available.
- I saw the  VPC as listed.
<img width="1017" height="108" alt="image" src="https://github.com/user-attachments/assets/005fbb98-4c88-4567-a02d-cf5c84fd8a73" />

---

## Task 2: 

**I Created Additional Subnets**

### Step 1: Creating More Subnets

- I navigated to the **Subnets** section and selected **Create subnet**.

### Step 2: Created a Second Public Subnet

-I used the following parameters to configure the subnet settings.
<img width="937" height="804" alt="Screenshot 2025-12-15 012411" src="https://github.com/user-attachments/assets/68b45759-e605-4fb8-b5c4-608200a08e9c" />


### Step 3: I Reviewed the New Subnets

I created the subnets and navigated to the Subnets section to verify that the new subnets were available.

<img width="1311" height="256" alt="image" src="https://github.com/user-attachments/assets/e6a987ca-c134-4215-b013-f455465450ce" />


---

## Task 3: 

**I associated the Subnets and Added Routes**

### Step 1: I associated the New Subnets.

- I navigated to the **Route Tables** section.
- Then ensured that each route table is currently associated with one subnet.

### Step 2: Associated the Public Subnet 2

- In the Subnet associations tab, I associated the **Public subnet 2** to the Public route table and clicked **Save associations**.

### Step 3: I associated the Private Subnet 2

- In the Subnet associations tab,I associated the **Private subnet 2** to the Private route table and clicked **Save associations**.

### Step 4: Reviewed Associations
In the Route Tables section, I ensured that each route table is now associated with two subnets.

<img width="1176" height="162" alt="image" src="https://github.com/user-attachments/assets/1fd078d3-967c-4838-83b8-3a3c1d1b5563" />


---

## Task 4: 

**Created a VPC Security Group**

### Step 1: Creating a Security Group

I navigated to the **Security Groups** section and selected **Create security group**.

### Step 2: I Set Up the Security Group

Use the following parameters to configure the security group basic details.

<img width="772" height="601" alt="image" src="https://github.com/user-attachments/assets/3c858e03-c38b-4835-8e08-6e35928afd5b" />


### Step 3: Set Up Security Group Inbound Rules
Configured the following inbound rules for the security group to permit incoming HTTP requests.

<img width="1084" height="197" alt="Screenshot 2025-12-15 014734" src="https://github.com/user-attachments/assets/213dce0e-112b-49df-b782-09946bf1d2ed" />


### Step 4: I set Up Security Group Outbound Rules
-I configured the following outbound rules for the security group to allow all types of outgoing traffic.

<img width="1092" height="182" alt="image" src="https://github.com/user-attachments/assets/4e32a1d0-9519-433b-9f30-8c9a98ccbec8" />


---

## Task 5: 

**I launched a Web Server Instance**

### Step 1: Accessing the EC2 Management Console

- I opened the AWS Management Console, and selected **EC2**.

### Step 2: Launching Instances
- I navigated to the **Instances** section and selected **Launch instances**.

### Step 3: Setting Up the Instance.

I used the following parameters to configure the instance settings.

<img width="930" height="747" alt="image" src="https://github.com/user-attachments/assets/6deb90a0-3dc8-4bf6-bdce-1d5a6c9cdb87" />


<img width="1033" height="456" alt="image" src="https://github.com/user-attachments/assets/b991a7fb-97b6-464f-9df0-e2eb73446637" />


### Step 4: Reviewed the Instance
After having created the instance, I navigated to the **Instances** section verifed that the instance is now running.

### Step 5: Connected to the Web Server
I opened a new browser tab and entered the Public IPv4 DNS of the instance to connect to the web server running on the instance.

---
## Conclusion

- VPC Launch Wizard helps you quickly set up AWS resources inside a Virtual Private Cloud.

- Additional Subnets improve organization, security, and network segmentation.

- Route Table Associations control how traffic moves between subnets.

- Security Groups act like firewalls to manage access to your instances.

- Web Server Instances can be securely deployed in the VPC using these components for scalable hosting.

