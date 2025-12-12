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

<img width="1666" height="235" alt="Screenshot 2025-12-12 050511" src="https://github.com/user-attachments/assets/eddbb1f8-cc4e-416b-8f49-be14f8d38079" />


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

### Step 7, settin up settings for Storage

In the Storage section, for Storage type, I selected General Purpose SSD (gp2).

### Step 8: Connectivity

In the Connectivity section, I configured the required settings.

<img width="749" height="753" alt="Screenshot 2025-12-12 052237" src="https://github.com/user-attachments/assets/e5b15b2f-2664-4f59-980a-f48079a89efb" />


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
