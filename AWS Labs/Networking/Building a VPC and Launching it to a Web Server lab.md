# AWS Lab: Build Your VPC and Launch a Web Server

## Overview

### Customer Scenario
In this lab, you use Amazon Virtual Private Cloud (VPC) to create your own VPC and add additional components to produce a customized network for a Fortune 100 customer. You also create security groups for your EC2 instance. You then configure and customize an EC2 instance to run a web server and launch it into the VPC that looks like the following customer diagram.

### Customer Diagram
The customer is requesting the build of this architecture to launch their web server successfully.

---

## Task 1: Create Your VPC

### Step 1: Access the AWS Management Console
Open the AWS Management Console, and select VPC.

### Step 2: Creating the VPC
In the Amazon VPC dashboard, choose the **Create VPC** button to launch the VPC wizard.

### Step 3: Set Up Your VPC
Once in the VPC wizard, use the following parameters to configure the VPC settings.

### Step 4: Check the Create VPC Workflow
Once you have successfully created the VPC, you should see a Success message in the Create VPC workflow.

### Step 5: Review Your VPC
Navigate to the Amazon VPC dashboard and select **Your VPCs** to verify that your VPC is available. You should see your VPC listed.

---

## Task 2: Create Additional Subnets

### Step 1: Creating More Subnets
Navigate to the **Subnets** section and select **Create subnet**.

### Step 2: Create a Second Public Subnet
Use the following parameters to configure the subnet settings.

### Step 3: Create a Second Private Subnet
Use the following parameters to configure the subnet settings.

### Step 4: Review the New Subnets
Once you have created the subnets, navigate to the Subnets section to verify that your new subnets are available.

---

## Task 3: Associate the Subnets and Add Routes

### Step 1: Associate the New Subnets
Navigate to the **Route Tables** section. You should see that each route table is currently associated with one subnet.

### Step 2: Associate Public Subnet 2
In the Subnet associations tab, associate the **Public subnet 2** to the Public route table and click **Save associations**.

### Step 3: Associate Private Subnet 2
In the Subnet associations tab, associate the **Private subnet 2** to the Private route table and click **Save associations**.

### Step 4: Review Associations
In the Route Tables section, you should see that each route table is now associated with two subnets.

---

## Task 4: Create a VPC Security Group

### Step 1: Creating a Security Group
Navigate to the **Security Groups** section and select **Create security group**.

### Step 2: Set Up the Security Group
Use the following parameters to configure the security group basic details.

### Step 3: Set Up Security Group Inbound Rules
Configure the following inbound rules for the security group to permit incoming HTTP requests.

### Step 4: Set Up Security Group Outbound Rules
Configure the following outbound rules for the security group to allow all types of outgoing traffic.

---

## Task 5: Launch a Web Server Instance

### Step 1: Access the EC2 Management Console
Open the AWS Management Console, and select **EC2**.

### Step 2: Launch Instance
Navigate to the **Instances** section and select **Launch instances**.

### Step 3: Set Up the Instance
Use the following parameters to configure the instance settings.

### Step 4: Review the Instance
Once you have created the instance, navigate to the **Instances** section to verify that your instance is now running.

### Step 5: Connect to the Web Server
Open a new browser tab and enter the Public IPv4 DNS of the instance to connect to the web server running on the instance.

---
