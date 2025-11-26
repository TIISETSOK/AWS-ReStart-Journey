#                                                              Amazon RDS Server                               
This project lab show my ability to leverage an AWS-managed database instance for solving relational database needs.

Amazon Relational Database Service (Amazon RDS) makes it easy to set up, operate, and scale a relational database in the cloud. It provides cost-efficient and resizable capacity while managing time-consuming database administration tasks, which allows you to focus on your applications and business. Amazon RDS provides you with six familiar database engines to choose from: Amazon Aurora, Oracle, Microsoft SQL Server, PostgreSQL, MySQL and MariaDB.

# The Challenge: Build and Access an Amazon RDS Server

## Overview

Amazon Relational Database Service (Amazon RDS) simplifies the process of setting up, operating, and scaling a relational database in the cloud. It provides cost-efficient, resizable capacity while managing time-consuming administrative tasks so you can focus on application development and business operations. 

---

## Challenge Requirements

* Launch an Amazon RDS DB instance using either the Amazon Aurora Provisioned or MySQL engine.
* Connect to a Linux EC2 instance using SSH.
* Install a MySQL-compatible client and connect to the RDS database.
* Create a table named **RESTART** with the following columns:

  * Student ID (Number)
  * Student Name
  * Restart City
  * Graduation Date (DateTime)
* Insert 10 sample records into the RESTART table and query all rows.
* Create a table named **CLOUD_PRACTITIONER** with the following columns:

  * Student ID (Number)
  * Certification Date (DateTime)
* Insert 5 sample records into the CLOUD_PRACTITIONER table and query all rows.
* Perform an INNER JOIN between both tables and display Student ID, Student Name, and Certification Date.


---

# Tasks

## Task 1: Create a Security Group for the RDS DB Instance

1. Open the AWS Management Console and navigate to the VPC service.
2. Go to **Security Groups** and select **Create security group**.
3. Configure the security group’s basic details.
4. Add an inbound rule that allows traffic on port **3306**, restricted to EC2 instances associated with the Web Security Group.


---

## Task 2: Create a DB Subnet Group

1. Open the RDS service in the AWS Management Console.
2. Navigate to **Subnet groups → Create DB subnet group**.
3. Configure the subnet group details.
4. Add the appropriate subnets.


---

## Task 3: Launch an Amazon RDS DB Instance

1. In the RDS service, go to **Databases → Create database**.
2. Select **MySQL** as the engine and choose the latest version.
3. Under Templates, select **Free tier**.
4. The deployment option is automatically set to **Single DB instance**.
5. Configure the database settings, including DB identifier and credentials.
6. Select an appropriate DB instance class.
7. Set the storage type to **General Purpose SSD (gp2)**.
8. Configure networking and connectivity settings.
9. Disable **Enhanced Monitoring** under the monitoring section.
10. After creation, confirm that the database is available and note its endpoint.


---

## Task 4: Connect to the Linux Server Using SSH

1. Locate the EC2 instance’s Public IPv4 address in the AWS Console.
2. Download the `labsuser.pem` key. Set its permissions to read-only:

   ```bash
   chmod 400 labsuser.pem
   ```
3. Connect to the EC2 instance using SSH:

   ```bash
   ssh -i labsuser.pem ec2-user@<public-ip>
   ```



---

## Task 5: Configure the EC2 Instance to Connect to the Database

1. Install MariaDB (MySQL client):

   ```bash
   sudo yum install mariadb -y
   ```
2. Connect to the RDS MySQL instance using the endpoint:

   ```bash
   mysql -h <db-endpoint> -u <username> -p
   ```



---

## Task 6: Interact with the Database

### Step 1: Create the Database

```sql
CREATE DATABASE challenge_lab;
USE challenge_lab;
```

### Step 2: Create the RESTART Table

```sql
CREATE TABLE RESTART (
  student_id INT,
  student_name VARCHAR(255),
  restart_city VARCHAR(255),
  graduation_date DATETIME
);
```

### Step 3: Insert Sample Rows

(Insert 10 sample records of your choice.)

### Step 4: Query RESTART

```sql
SELECT * FROM RESTART;
```

### Step 5: Create the CLOUD_PRACTITIONER Table

```sql
CREATE TABLE CLOUD_PRACTITIONER (
  student_id INT,
  certification_date DATETIME
);
```

### Step 6: Insert Sample Rows

(Insert 5 sample records of your choice.)

### Step 7: Query CLOUD_PRACTITIONER

```sql
SELECT * FROM CLOUD_PRACTITIONER;
```

### Step 8: Perform INNER JOIN

```sql
SELECT 
  r.student_id,
  r.student_name,
  c.certification_date
FROM RESTART r
INNER JOIN CLOUD_PRACTITIONER c
ON r.student_id = c.student_id;
```
