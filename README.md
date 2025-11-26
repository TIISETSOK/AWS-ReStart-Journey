# AWS-ReStart-Journey
This repository documents my three-month journey of the AWS Restart program, which is designed to take students who are tech beginners to confident job ready cloud practitioners.

Below is a **professional, GitHub-ready README.md** written in the style and standards of the **AWS re/Start Programme**, reflecting its learning objectives, structure, and tone.

If you want it adjusted for a specific repository name, theme, or portfolio style, I can refine it further.

---

# Build and Access an Amazon RDS Server

### AWS re/Start – Challenge Lab

This repository documents the steps, commands, and SQL operations completed during the **AWS re/Start Challenge Lab: Build and Access an RDS Server**.
The objective of this lab is to demonstrate core AWS cloud skills, including VPC networking, database provisioning, Linux administration, and SQL data operations.

---

## Overview

The lab focuses on creating and managing a relational database using **Amazon RDS (MySQL)** and interacting with it from an **Amazon EC2 Linux instance**.
It reinforces key AWS re/Start competencies, such as:

* Foundational cloud architecture
* Networking and security group configuration
* Working with managed AWS databases
* Linux command-line proficiency
* SQL data manipulation and querying

---

## Lab Objectives

1. Create a Security Group for database access
2. Configure a DB Subnet Group
3. Launch an Amazon RDS MySQL instance
4. Connect to an EC2 instance using SSH
5. Install a database client on the EC2 instance
6. Connect to the RDS database using the client
7. Create two database tables and insert sample data
8. Query data and perform an INNER JOIN

---

## Technologies Used

* **Amazon EC2** (Linux Server)
* **Amazon RDS (MySQL)**
* **Amazon VPC** (Security Groups, Subnet Groups)
* **MariaDB / MySQL Client**
* **Linux CLI**
* **SQL**

---

# 1. AWS Configuration Steps

## 1.1 Create a Security Group for RDS

* Allow inbound MySQL traffic on **port 3306**
* Limit access to EC2 instances within the same VPC security group

## 1.2 Create a DB Subnet Group

* Select the appropriate VPC
* Add at least two subnets across different Availability Zones

## 1.3 Launch the RDS Instance

* Engine: **MySQL**
* Template: **Free Tier**
* Storage: **General Purpose SSD (gp2)**
* Deployment: **Single DB Instance**
* Disable enhanced monitoring
* Record the database **endpoint** for later use

---

# 2. EC2 Configuration and Connection

## 2.1 Connect to EC2 using SSH

```bash
chmod 400 labsuser.pem
ssh -i labsuser.pem ec2-user@<public-ip>
```

## 2.2 Install MariaDB Client

```bash
sudo yum install mariadb -y
```

## 2.3 Connect to the RDS Database

```bash
mysql -h <db-endpoint> -u <username> -p
```

---

# 3. SQL Operations

## 3.1 Create and Select Database

```sql
CREATE DATABASE challenge_lab;
USE challenge_lab;
```

## 3.2 Create RESTART Table

```sql
CREATE TABLE RESTART (
  student_id INT,
  student_name VARCHAR(255),
  restart_city VARCHAR(255),
  graduation_date DATETIME
);
```

### Insert Sample Data (10 rows)

```sql
INSERT INTO RESTART VALUES
(1, 'John Doe', 'Cape Town', '2024-03-01 10:00:00'),
(2, 'Sarah Smith', 'Johannesburg', '2024-03-02 10:00:00');
-- Add remaining rows as needed
```

### Query Table

```sql
SELECT * FROM RESTART;
```

---

## 3.3 Create CLOUD_PRACTITIONER Table

```sql
CREATE TABLE CLOUD_PRACTITIONER (
  student_id INT,
  certification_date DATETIME
);
```

### Insert Sample Data (5 rows)

```sql
INSERT INTO CLOUD_PRACTITIONER VALUES
(1, '2024-04-10 09:00:00'),
(2, '2024-04-12 11:00:00');
-- Add remaining rows as needed
```

### Query Table

```sql
SELECT * FROM CLOUD_PRACTITIONER;
```

---

## 3.4 INNER JOIN Query

```sql
SELECT 
  r.student_id,
  r.student_name,
  c.certification_date
FROM RESTART r
JOIN CLOUD_PRACTITIONER c
ON r.student_id = c.student_id;
```

---

# 📈 Key Learnings

* Gained practical experience provisioning managed databases using **Amazon RDS**
* Reinforced understanding of **VPC networking** and **security groups**
* Connected a Linux EC2 instance to a private database securely
* Practiced SQL commands essential for database management
* Strengthened cloud operational skills aligned with AWS re/Start programme outcomes

---

# 📄 About AWS re/Start

**AWS re/Start** is a full-time, classroom-based skills development program preparing individuals for cloud careers.
It covers cloud fundamentals, Linux, networking, security, Python, databases, and hands-on AWS labs.
This repository showcases one of the many hands-on challenge labs completed during the program.

---


