# Trouble Shooting a Network Issue

In this lab i help sort out an AWS infrastructure networking issue.

## First Task:

For the first task i used an SSH To connect an Amazon Linux EC2 Instance

### Steps i took

**for the initial step:**

I used the AWS Management Console, I first selected  the EC2 instance and 
made note of the Public IPv4 address. 

These are going to be of necassity when connecting to the instance

I also downloaded the private key file labsuser.pem.

Changed to the Downloads directory and modify the permissions on the key to 
be read-only .

**for the second step**

I had to connect to the instance  using SSH.

I established a connection to the EC2 instance using the sshcommand, the key and the instance’s public IPv4 address.

### Task 2

For the second task i installed http

**The fist step:**

I started the httpd service with the systemctl start command. 

**The second step**

I checked if the htto service was running using the id i reviewed in step 1 of task 1

### Task 3

For task 3 i had to investigate the customers VPCs configuration.

**For the first step**

I accessed the AWS Management console and selectin the VPC service

**For the second step**

I used the left navigation pane and check each service within the 
VPC to confirm that each resource is configured correctly

***For the third step:**

I investigated the instance and found that the commad instance is running in the public subnet 1 and is linked to the security group Linux instance SG

***for the fourth step:**

I investigated the VPC and found that the labs VPC is availabe and associated with a net work ACL.

**Step 5**

in the fifth step i investigated the subnet and found that the public subnet 1 was available in the lab VPC and is asociated with a net work ACL and with the public Route Table

**Step 6:**

here i had to investigate the route table, during the investigation i founf that the lab VPC and the route table where correctly linked.
I also had to ensure that thr route was directing all internet traffic to thr internet gateway.

And also found that the route table is explicitly associated eith the public subnet 1

***Step 10**
 for this second last step i had to test ICMP traffic , by pinging the apache HTTp server to verify its reachability.

**Step 11** 

 Here i had to open a new tab in anbrowser and visit the id tht we noted down ith step one of task 1.





