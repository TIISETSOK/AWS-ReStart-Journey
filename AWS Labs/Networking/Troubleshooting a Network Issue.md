# Troubleshooting a Network Issue

Your role is a cloud support engineer at Amazon Web Services (AWS). During your shift, a consulting company has a networking issue within their AWS infrastructure. The following is the email and an attachment of their architecture.

### Ticket from Your Customer

""Hello, Cloud Support!

When I create an Apache server through the command line, I cannot ping it. I also get an error when I enter the IP address in the browser. Can you please help figure out what is blocking my connection?

Thanks!  
Ana Contractor""

<img width="954" height="754" alt="Screenshot 2025-12-13 022446" src="https://github.com/user-attachments/assets/35e84c7b-010b-4b72-b478-4feed878ccfc" />


---

## Task 1: 

- I used an SSH to connect to an Amazon Linux EC2 instance.
  
### **Step 1, I collected the necessary credentials**

- I opened the Details drop‑down and clicked Show.

- I downloaded the labsuser.ppk file and noted the PublicIP address.

### **Step 2; I connected with PuTTY**

- I installed PuTTY 

I opened putty.exe and configured the session using the .ppk file and PublicIP address (meeting  the PuTTY connection requirements).

<img width="819" height="388" alt="Screenshot 2025-12-13 025135" src="https://github.com/user-attachments/assets/5ab1b1bb-8b52-4cb4-bd0b-cc9be59e4ecd" />


---

## Task 2

- I installed httpd

### **Step 1; I starteed the Apache HTTP Server**

- Start the httpd service with the **systemctl start** command
  
### Step 2; I checked the httpd Service

- The httpd service wasrunning, but i coild not visit `http://34.219.182.160` in a browser, as the page will not load.

---

## Task 3:

- **I had to investigate the Customer's VPC Configuration**

### Step 1; I accessed the AWS Management Console

- i opened the AWS Management Console and selected **VPC**.

### Step 2; I used the VPCs Left Navigation Pane.

- I used the left navigation pane and checked each service within the VPC to confirm that each of the resources are configured correctly.

### Step 3; I had to investigate the Instance.

- The Command Host instance was running in the Public Subnet 1 and is linked to the security group **Linux instance SG**.

### Step 4; I investigated the VPC

- The Lab VPC was available and associated with a network ACL.

### Step 5; Investigated the Subnet

- The public Subnet 1 was available in the Lab VPC and is associated with a network ACL and the Public Route Table.

### Step 6: Investigate the Route Table

- The Public Route Table has been correctly linked to the Lab VPC.
- There is a route directing all internet traffic to the internet gateway.
- The route table is explicitly associated with Public Subnet 1.

### Step 7; I investigated the Internet Gateway

- The internet gateway has been properly attached to the Lab VPC.

### Step 8; I investigated the Network ACL

- The network ACL was correctly associated with Public Subnet 1.
- The current rules allow all inbound and outbound traffic.

### Step 9; I investigated the Security Group

- The Linux instance SG security group was linked to the Command Host instance.
- The inbound rules allow only SSH traffic.
- The outbound rules allow all traffic.
- I added new inbound rules to allow ICMP, HTTP, and HTTPS traffic.

### Step 10; I tested ICMP Traffic

- I had to ping the Apache HTTP server to verify its reachability.

### Step 11; I tested the  HTTP Traffic

- I opened a new tab in a browser to visit  **`http://34.219.182.160`** so that I can confirm that the Apache HTTP server is working.

---

## Conclusions

Subnets divide a virtual network into smaller sections to improve organization and security. Route tables control how traffic moves between subnets and external networks. Internet gateways allow resources in the network to send and receive data from the internet. Network ACLs add security by filtering traffic at the subnet level based on rules. Security groups act like firewalls, managing access to individual instances by controlling inbound and outbound traffic.

