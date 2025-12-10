# AWS Challenge Lab

## Build and Access an RDS Server

### Overview

Amazon Relational Database Service (Amazon RDS) makes it easy to set up, operate, and scale a relational database in the cloud. It provides cost-efficient and resizable capacity while managing time-consuming database administration tasks, which allows you to focus on your applications and business.

---

## Your Challenge

1. Launch an Amazon RDS DB instance using either Amazon Aurora Provisioned DB or MySQL database engines.
2. Connect (SSH) to the Linux Server.
3. Install a MySQL client, and use it to connect to your DB.
4. Create a table `RESTART` with the following columns:
   - Student ID (Number)
   - Student Name
   - Restart City
   - Graduation Date (Date Time)
5. Insert 10 sample rows into this table.
6. Select all rows from this table.
7. Create a table `CLOUD_PRACTITIONER` with the following columns:
   - Student ID (Number)
   - Certification Date (Date Time)
8. Insert 5 sample rows into this table.
9. Select all rows from this table.
10. Perform an inner join between the 2 tables created above and display Student ID, Student Name, Certification Date.

---

## Task 1: Create a Security Group for the RDS DB Instance

### Step 1: Access the VPC management console

Open the AWS Management Console, and select VPC.

### Step 2: Create security group

Navigate to the Security Groups section, and select Create security group.

### Step 3: Basic details

In the Basic details section, configure the DB Security Group using the required settings.

### Step 4: Inbound rules

In the Inbound rules section, configure the DB Security Group to permit inbound traffic on port 3306 from any EC2 instance that is associated with the Web Security Group.

---

## Task 2: Create a DB Subnet Group

### Step 1: Access the RDS database service

In the AWS Management Console, select RDS.

### Step 2: Create DB subnet group

Navigate to the Subnet groups section, and select Create DB subnet group.

### Step 3: Subnet group details

In the Subnet group details section, configure the DB Subnet Group using the required settings.

### Step 4: Add subnets

In the Add subnets section, configure the required settings.

---

## Task 3: Launch an Amazon RDS DB instance

### Step 1: Create database

Navigate to the Databases section, and select Create database.

### Step 2: Engine options

In the Engine options section, for Engine type, choose MySQL, for Engine version, choose the latest version.

### Step 3: Templates

In the Templates section, choose Free tier.

### Step 4: Availability and durability

Notice that when you selected the Free tier template, the Single DB instance option was selected and locked as the default deployment option in the Availability and durability section.

### Step 5: Settings

In the Settings section, configure the required parameters.

### Step 6: Instance configuration

In the Instance configuration section, for DB instance class, configure the required settings.

### Step 7: Storage

In the Storage section, for Storage type, select General Purpose SSD (gp2).

### Step 8: Connectivity

In the Connectivity section, configure the required settings.

### Step 9: Monitoring

In the Monitoring section, for Additional configuration, uncheck Enable Enhanced Monitoring.

### Step 10: Review database creation

Verify the availability of the `challenge-lab-db` database and take note of its endpoint in the Connectivity & Security section.

---

## Task 4: Use SSH to connect to the Linux Server

### Initial Preparations

In the AWS Management Console, select the Linux Server EC2 instance and make note of the Public IPv4 address.

Download the private key file `labsuser.pem`. Change to the Downloads directory and modify the permissions on the key to be read-only (`r`).

### Connect to the Linux Server using SSH

Establish a connection to the Linux Server EC2 instance using the `ssh` command, the key, and the instance’s public IPv4 address.

---

## Task 5: Configure the EC2 instance to connect to the DB

### Step 1: Install the DB client

Run the command `sudo yum install mariadb –y` to install the MariaDB client.

### Step 2: Connect to the database

After installing a MySQL client, run the following command to connect to the database.

---

## Task 6: Interact With Your DB

### Step 1: Create a database

CREATE the `challenge_lab` database and switch to it.

### Step 2: Create the RESTART table

CREATE a table `RESTART` with the following columns:
- Student ID (Number)
- Student Name
- Restart City
- Graduation Date (Date Time)

### Step 3: Insert sample rows

INSERT 10 sample rows into the `RESTART` table.

### Step 4: Select all rows

SELECT all rows from the `RESTART` table.

---

### Step 5: Create the CLOUD_PRACTITIONER table

CREATE a table `CLOUD_PRACTITIONER` with the following columns:
- Student ID (Number)
- Certification Date (Date Time)

### Step 6: Insert sample rows

INSERT 5 sample rows into the `CLOUD_PRACTITIONER` table.

### Step 7: Select all rows

SELECT all rows from the `CLOUD_PRACTITIONER` table.

### Step 8: Perform an inner join

Perform an INNER JOIN between the 2 tables created above and display:
- Student ID
- Student Name
- Certification Date

---

## Conclusions

- **Amazon Relational Databases:** Amazon Relational Databases offer scalable and reliable solutions for managing structured data, catering to diverse business needs.
- **Amazon RDS DB Instances:** Amazon RDS DB Instances provide flexible configurations and high availability options, ensuring continuous access to databases.
- **Permitting connections to a DB instance:** Permitting connections to a DB instance allows seamless communication between applications and databases, facilitating real-time data interactions.
- **DB Subnet Groups:** DB Subnet Groups enable secure networking configurations, ensuring data privacy and compliance with regulatory requirements.
- **Interacting with a Database:** Interacting with a database through applications or query tools enables data retrieval, updates, and analysis, empowering informed decision-making and efficient data management.


```

You can copy this text into a file with the `.md` extension and upload it to your GitHub repository.
