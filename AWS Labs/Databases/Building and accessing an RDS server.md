## Building and Accessing an RDS Server

- Amazon Relational Database Service (Amazon RDS) makes it easy to set up, operate, and scale a relational database in the cloud.
- It provides cost-efficient and resizable capacity while managing time-consuming database administration tasks, which allows you to focus on your applications and business.


## What i am doing in this lab

1. I launched an Amazon RDS DB instance using either Amazon Aurora Provisioned DB or MySQL database engine.
2. I connect (SSH) to the Linux Server.
3. I installed a MySQL client, and i used it to connect to DB.
4.  I created a table `RESTART` with the following columns:
   - Student ID (Number)
   - Student Name
   - Restart City
   - Graduation Date (Date Time)
5. Inserted 10 sample rows into this table.
6. Selected all rows from this table.
7. Created a table `CLOUD_PRACTITIONER` with the following columns:
   - Student ID (Number)
   - Certification Date (Date Time)
8. Inserted 5 sample rows into this table.
9. Selected all rows from this table.
10. Performed an inner join between the 2 tables created above and display Student ID, Student Name, Certification Date.

---

## Task 1

**I created a Security Group for the RDS DB Instance.**

### Step 1; Accessing the VPC management console

I opened the AWS Management Console, and selected VPC.

### Step 2; here i created security a group

I navigated to the Security Groups section, and selected Create security group.

### Step 3; i configured the basic details

In the Basic details section, I configured the DB Security Group using the required settings.

### Step 4; I set up  Inbound rules

In the Inbound rules section,I configured the DB Security Group to permit inbound traffic on port 3306 from any EC2 instance that is associated with the Web Security Group.

<img width="956" height="1020" alt="Screenshot 2025-12-13 143254" src="https://github.com/user-attachments/assets/b816468f-d4dd-47d3-94fc-88764354157b" />

<img width="657" height="395" alt="Screenshot 2025-12-13 143700" src="https://github.com/user-attachments/assets/c257a6dc-91e7-45d5-9e22-3f368698b7d6" />


---

## Task 2:

**Create a DB Subnet Group**

### Step 1; I went back to Access the RDS database service

In the AWS Management Console,I selected RDS.

### Step 2; I created a DB subnet group

I navigated to the Subnet groups section, and selected Create DB subnet group.

### Step 3; Updating Subnet group details

In the Subnet group details section, I configured the DB Subnet Group using the required settings.

### Step 4; Here I Added subnets

In the Add subnets section,I configurd the required settings.

<img width="810" height="557" alt="image" src="https://github.com/user-attachments/assets/b1309e01-6314-48a4-82ec-d2708e22857c" />

<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/c4c81d34-40eb-40e7-88ec-c7faf7ddf37f" />


---

## Task 3:

**Launch an Amazon RDS DB instance**

### Step 1; I Created a database

I navigated to the Databases section, and select Create database.

### Step 2; I set the engine options

In the Engine options section, for Engine type, I chose MySQL, for Engine version, and chose the latest version.

### Step 3; I had to choose a Template

In the Templates section,I chose Free tier.

### Step 4; Availability and durability

Notice that when you selected the Free tier template, the Single DB instance option was selected and locked as the default deployment option in the Availability and durability section.

### Step 5; Settings

In the Settings section, I configured the required parameters.

<img width="722" height="748" alt="Screenshot 2025-12-12 052430" src="https://github.com/user-attachments/assets/a3fb55f1-91e8-4b65-b145-c732934eff3b" />


### Step 6; Doing Instance configuration

In the Instance configuration section, for DB instance class, configured the required settings, which was selecting the bustable classed opton.

### Step 7, setting up settings for Storage

In the Storage section, for Storage type, I selected General Purpose SSD (gp2).

### Step 8; Setting up connectivity

In the Connectivity section, I configured the required settings.

<img width="749" height="753" alt="Screenshot 2025-12-12 052237" src="https://github.com/user-attachments/assets/e5b15b2f-2664-4f59-980a-f48079a89efb" />


### Step 9; Monitoring 

In the Monitoring section, i expaned Additional configuration, unchecked Enable Enhanced Monitoring.

### Step 10; Reviewing the databases creation.

I varified if the `database-challenge-lab-db` database was created sussessfully  and i also took note of its endpoint in the Connectivity & Security section.

<img width="1198" height="1020" alt="Screenshot 2025-12-13 150114" src="https://github.com/user-attachments/assets/c1cad181-44ff-48bb-b7d8-4fd387c36059" />


---

## Task 4: i used SSH to connect to the Linux Server

### Initial Preparations

Step 1; i collected all my necessary credentials

- I opened the Details drop‑down menu and clicked Show.

- Downloaded the labsuser.ppk file and noted the PublicIP address.

- I closed the Details panel.

Step 2; I connected via the use of PuTTY

- I installed PuTTY if you don’t already have it.

- I opened  putty.exe and configured the session using the .ppk file and PublicIP address (following the PuTTY connection guide).

---

## Task 5: 

- **Configure the EC2 instance to connect to the DB**

### Step 1; I installed the DB client

- Ran the command `sudo yum install mariadb –y` to install the MariaDB client.

### Step 2; I connected to the database

After installing a MySQL client, i ran the following command to connect to the database.

---

## Task 6: 

- **Interact With Your DB**

### Step 1; I Created a database

CREATED the `database-challenge_lab` database and switch to it.

### Step 2; I Created the RESTART table

CREATED a table `RESTART` with the following columns:
- Student ID (Number)
- Student Name
- Restart City
- Graduation Date (Date Time)

<img width="1334" height="374" alt="image" src="https://github.com/user-attachments/assets/fa60b04a-2d3f-41f4-8e93-540f92a7cade" />


### Step 3; I Insert sample rows

INSERTED 10 sample rows into the `RESTART` table.

### Step 4: Select all rows

I SELECTED all rows from the `RESTART` table.

<img width="826" height="439" alt="image" src="https://github.com/user-attachments/assets/63c396e3-37fb-4115-8d20-365f02794db5" />


### Step 5; I created the CLOUD_PRACTITIONER table

CREATED a table `CLOUD_PRACTITIONER` with the following columns:
- Student ID (Number)
- Certification Date (Date Time)

 <img width="1508" height="358" alt="Screenshot 2025-12-13 151048" src="https://github.com/user-attachments/assets/843cfd11-91f2-437e-87ae-b33997697852" />
 

### Step 6; I had to insert sample rows

INSERT 5 sample rows into the `CLOUD_PRACTITIONER` table.

### Step 7; I selected all rows

SELECTED all rows from the `CLOUD_PRACTITIONER` table.

<img width="1324" height="619" alt="Screenshot 2025-12-13 150844" src="https://github.com/user-attachments/assets/23974921-f695-4815-b5f0-9b9d93fb2447" />


### Step 8; I performed an inner join

Perform an INNER JOIN between the 2 tables created above and display:
- Student ID
- Student Name
- Certification Date
<img width="1419" height="520" alt="Screenshot 2025-12-13 150624" src="https://github.com/user-attachments/assets/82ce342f-1d6c-4aa0-8580-d95aff260f45" />

---

## Conclusions

- Amazon Relational Databases help businesses manage structured data reliably and at scale. 
- Amazon RDS DB Instances offer flexible setups and high availability to keep databases running smoothly.
- Allowing connections to a DB instance lets applications interact with the database in real time.
-  DB Subnet Groups provide secure network settings to protect data and meet compliance standards. Using query tools or applications to interact with databases enables efficient data access, updates, and analysis
