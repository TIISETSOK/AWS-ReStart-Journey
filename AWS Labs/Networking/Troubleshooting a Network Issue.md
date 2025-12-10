# AWS Lab: Troubleshooting a Network Issue

## Overview

### Customer Scenario
Your role is a cloud support engineer at Amazon Web Services (AWS). During your shift, a consulting company has a networking issue within their AWS infrastructure. The following is the email and an attachment of their architecture.

### Ticket from Your Customer

""Hello, Cloud Support!

When I create an Apache server through the command line, I cannot ping it. I also get an error when I enter the IP address in the browser. Can you please help figure out what is blocking my connection?

Thanks!  
Ana Contractor""


---

## Task 1: Use SSH to Connect to an Amazon Linux EC2 Instance

### Initial Preparations
- In the AWS Management Console, select the EC2 instance and make note of the Public IPv4 address.
- Download the private key file `labsuser.pem`. Change to the Downloads directory and modify the permissions on the key to be read-only (`r`).

### Connect to the Instance Using SSH
- Establish a connection to the EC2 instance using the `ssh` command, the key, and the instance’s public IPv4 address.

---

## Task 2: Install httpd

### Step 1: Start the Apache HTTP Server
- Start the httpd service with the command: 
  ```
  sudo systemctl start httpd
  ```

### Step 2: Check the httpd Service
- The httpd service may be running, but if you attempt to visit `http://34.219.182.160` in a browser, the page will not load.

---

## Task 3: Investigate the Customer's VPC Configuration

### Step 1: Access the AWS Management Console
- Open the AWS Management Console and select **VPC**.

### Step 2: Use the VPC Left Navigation Pane
- Use the left navigation pane and check each service within the VPC to confirm that each resource is configured correctly.

### Step 3: Investigate the Instance
- The Command Host instance is running in the Public Subnet 1 and is linked to the security group **Linux instance SG**.

### Step 4: Investigate the VPC
- The Lab VPC is available and associated with a network ACL.

### Step 5: Investigate the Subnet
- Public Subnet 1 is available in the Lab VPC and is associated with a network ACL and the Public Route Table.

### Step 6: Investigate the Route Table
- The Public Route Table is correctly linked to the Lab VPC. There is a route directing all internet traffic to the internet gateway. The route table is explicitly associated with Public Subnet 1.

### Step 7: Investigate the Internet Gateway
- The internet gateway is properly attached to the Lab VPC.

### Step 8: Investigate the Network ACL
- The network ACL is correctly associated with Public Subnet 1. The current rules allow all inbound and outbound traffic.

### Step 9: Investigate the Security Group
- The Linux instance SG security group is linked to the Command Host instance. The current inbound rules allow only SSH traffic. The outbound rules allow all traffic.
- Add new inbound rules to allow ICMP, HTTP, and HTTPS traffic.

### Step 10: Test ICMP Traffic
- Ping the Apache HTTP server to verify its reachability.

### Step 11: Test HTTP Traffic
- Open a new tab in a browser and visit `http://34.219.182.160` to confirm that the Apache HTTP server is working.

---

## Conclusions



