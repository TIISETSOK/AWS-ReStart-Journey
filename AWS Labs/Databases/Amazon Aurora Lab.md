

aws re/start

# Overview

Aurora is a fully managed, MySQL-compatible, relational database engine that combines the performance and reliability of high-end commercial databases with the simplicity and cost-effectiveness of open-source databases. It delivers up to five times the performance of MySQL without requiring changes to most of your existing applications that use MySQL databases.

Amazon Aurora offers high-performance and scalable database solutions. Creating an Aurora instance allows efficient data management, while connecting to Amazon EC2 instances streamlines integration. Configuring EC2 to connect to Aurora ensures smooth data communication, enabling seamless querying for valuable insights and informed decision-making. Overall, Aurora's advanced features and architecture simplify database administration and enhance performance, making it a top choice for scalable and reliable data solutions.

## Topics covered

- Create an Aurora instance
- Connect to a pre-created Amazon Elastic Compute Cloud (Amazon EC2) instance
- Configure the Amazon EC2 instance to connect to Aurora Query the Aurora instance

# Task 1

Create an Aurora instance

**Step 1: Access the RDS database service**

Open the AWS Management Console, and select RDS.

---

### Step 2: Create database

Navigate to the Databases section, and select Create database.

---

#### Databases (0)

- [ ] Group resources
- [x] Modify
- [ ] Actions
- [ ] Restore from S3
- [ ] Create database

---

#### Database
- [x] Database
- [ ] DynamoDB
- [ ] Manager HMOS, Database
- [ ] ElastCache
- [ ] In-Memory Code
- [ ] RDS
- [ ] Manager Relational Database Service

# Task 1

Create an Aurora instance

**Step 3: Choose a database creation method**

In the **Choose** a database creation method section, choose Standard create.

---

### Choose a database creation method
Info

- Standard create
  You can all of the configuration options, including ones for availability, security, backup, and maintenance.
- Easy create
  Use recommended best-practice configurations. Some configurations options can be changed after the database is created.

---

**Step 4: Engine options**

In the **Engine options** section, for Engine type, choose Aurora (MySQL Compatible), for Engine version, choose the default for major version 8.0.

---

### Engine options
Engine type Info

- Aurora (MySQL Compatible)
- Aurora (PostgreSQL Compatible)
- Engine Version
- Aurora MySQL 5.0.2 (Compatible with MySQL 8.0.28) - default for major version 8.0

# Task 1

Create an Aurora instance

## Step 5: Templates
In the Templates section, choose Dev/Test.

**Templates**
Choose a sample template to meet your use case.

- [ ] Production
  Use details for high availability and fast, consistent performance.
- [x] Dev/Test
  This instance is intended for development use outside of a production environment.

---

## Step 6: Settings
In the Settings section, configure the following options.

**Settings**

DB cluster identifier info
Enter a name for your DB cluster.

[aurora]

- [x] Credentials Settings
Master username info
Type Login ID for the master user of your DB instance.

[admin]

Master password info

[admin123]

Confirm master password info

[admin123]

aws re/start

# Task 1

Create an Aurora instance

## Step 7: Instance configuration

In the **Instance configuration** section, for DB instance class, configure the following settings.

- **Instance configuration**
  The DB instance configuration options below are limited to these supported by the engine that you selected above.

- DB instance class: info
  - Standard classes (includes m classes)
  - Memory optimized classes (includes r and x classes)
  - Burstable classes (includes t classes)

- db.t3.medium
  2 x CPU/s   4 GB RAM    Network: 2.0BS Mbps

---

## Step 8: Availability & durability

In the **Availability & durability** section, for Multi-AZ deployment, choose Don't create an Aurora Replica.

- **Availability & durability**

- Multi-AZ deployment: info
  - Create an Aurora Replica or Reader node in a different AZ (recommended for scaled availability)
  - Create an Aurora Replica for fast follower and high availability.
  - Don't create an Aurora Replica

aws re/start

# Task 1

Create an Aurora instance

## Step 9: Connectivity
In the Connectivity section, configure the following options.

Connectivity info

Virtual private cloud (VPC) info
Choose the VPC The VPC defines the virtual networking environment for this DB cluster.

LabVPC (vpc-0f15b5c6a9+cf1ff)
2 Subnets, 2 Availability Zones

DB subnet group info
Choose the DB subnet group. The DB subnet group defines which subnets and IP ranges the DB cluster can use in the VPC that you selected.

dbsubnetgroup
2 Subnets, 2 Availability Zones

Public access info

Yes
PUB assigns a public IP address to the cluster. Amazon EC2 instances and other resources outside of the VPC can connect to your cluster.
Resource inside the VPC can also connect to the cluster. Choose one or more VPC security groups that specify which resources can connect to the cluster.

No
PUB doesn't assign a public IP address to the cluster. Only Amazon EC2 instances and other resources inside the VPC can connect to your cluster. Choose one or more VPC security groups that specify which resources can connect to the cluster.

VPC security group (firewall) info
Choose one or more VPC security groups to allow access to your database. Make sure that the security group rules allow the appropriate incoming traffic.

Choose existing
Choose existing VPC security groups

Existing VPC security groups

Choose one or more options

D8SecurityGroup X

---

## Step 10: Monitoring
In the Monitoring section, for Additional configuration, clear the check box for Enable Enhanced Monitoring.

Monitoring

- Additional configuration
  Enhanced Monitoring

Enable Enhanced Monitoring
  Enabling Enhanced Monitoring metrics are enabled when you want to see how different processes or threads use the CPU.

aws re/start

# Task 1

Create an Aurora instance

## Step 11: Additional configuration

In the **Additional configuration** section, configure the following options.

- **Additional configuration**
  Database option, encryption time of, failure, backup turned on, backtrack turned off, maintenance. Coordination tags, delete protection turned off.

### Database options
Initial database name: info

| world |
|---|
| If you do not specify a database name, Amazon RDS does not create a database. |

### Encryption
- [ ] Enable encryption
  Choose to encrypt the given instance. Master key IDs and aliases appear in the list after they have been created using the AWS Key Management Service console. Info

### Maintenance
Auto minor version upgrade Info

- [ ] Enable auto minor version upgrade
  Enabling auto minor version upgrade will automatically upgrade to new minor versions as they are released. The automatic upgrade order during the maintenance window for this database.

---

## Step 12: Review database instance creation

Verify the availability of the aurora-instance-1 database.

---

### Databases (2)
- [x] Group resources
- [ ] Modify
- [ ] Actions
- [ ] Restore from S3
- [ ] Create database

[Filter by databases]

- [ ] DB identifier
- [ ] Status
- [ ] Role
- [ ] Engine
- [ ] Region & AZ
- [ ] Size
- [ ] VPC
- [ ] aurora
- [ ] Available
- [ ] Regional cluster
- [ ] Aurora MySQL
- [ ] us-west-2
- [ ] 1 instance
- [ ] - aurora-instance-1
- [ ] Available
- [ ] Writer instance
- [ ] Aurora MySQL
- [ ] us-west-2a
- [ ] db.ts.medium
- [ ] vpc-off3506cbd91cf1ff

# Task 2

Connect to an Amazon EC2 Linux instance

**Step 1: Access the EC2 Management Console**

In the AWS Management Console, select EC2.

---

### Security visited
- **Favorites**
- **All services**

- [ ] Analytics
- [x] Application Integration
- [ ] Blockchain
- [x] Business Applications
- [x] Cloud Financial Management
- [x] Compute

---

### Compute
- AWS App Runner
   Build and run production web applications at scale

- Batch
   Fully managed batch processing at any scale

- EC2
   Virtual Servers in the Cloud

- EC2 Image Builder
   A managed service to automate build, customize and deploy iOS images

---

**Step 2: Review running EC2 instances**

Navigate to the Instances section. The running Command Host EC2 instance is listed.

---

**Instances (1) info**

- [ ] Find instance by attribute or tag (core-sensitive)

- [ ] Name ▼ ▼ | Instance ID
- [ ] Command Host

- [ ] Instance state ▼ ▼ | Status check
- [ ] Running ▼ ▼ | 2/2 checks passed

- [ ] Connect
- [ ] Instance state ▼ ▼ | Actions ▼ ▼ | Launch instances ▼ ▼

- [ ] All states ▼ ▼ | < 1 ▼

- [ ] Availability Zone ▼ ▼ | Public IPv4 ... ▼ | Security group name ▼ ▼

- [ ] us-west-2a
- [ ] 35.93.177.207
- [ ] EC2SecurityGroup

# Task 2

Connect to an Amazon EC2 Linux instance

## Step 3: Connect to the instance
Connect to the Command Host EC2 instance using Session Manager.

---

### Connect to instance [n=6](#)

Connect to your instance i-00d6085e8b733521 (Command Host) using any of these options:

| EC2 Instance Connect | Session Manager | SSH client | EC2 serial console |
|---|---|---|---|
| Session Manager usage:    |    |    |    |

- Connect to your instance without SSH keys, a bastion host, or opening any inbound ports.
- Sessions are secured using an AWS Key Management Service key.
- You can log session commands and details in an Amazon S3 bucket or CloudWatch Logs log group.
- Configure sessions on the Session Manager Preferences page.

---

**Step 4: Review connection**
You have successfully connected to the Amazon EC2 instance named **Command Host**.

---

Session ID: user3195341=Cristihan_Becerra-009584b06f6a69107
instance ID: i-0031316fb49bbeae2

ah-4.25

# Task 3

**Configure the Amazon EC2 Linux instance to connect to Aurora**

---

## Step 1: Install the DB client

To install the MariaDB client, run the following command.

- **dn-4.26 sudo yum install mariadb -y**
  Loaded plugins: extra_augreations, langnacks, priorities, update-motd
  amzn2-core
  Resolving Dependencies
  → Running transaction check
  → Package mariadb.x86_64 i:5.5.66-1.amzn2.0.1 will be installed
  → Finished Dependency Resolution

---

## Step 2: Review the Aurora DB cluster

Go back to the RDS Management Console, navigate to the Databases section, and select the aurora DB cluster.

---

### Databases (2)

- [ ] Group resources
- [x] Modify
- [ ] Actions
- [ ] Restore from S3
- [ ] Create database

---

### Filev by databases

| DB identifier | Status    | Role    | Engine    | Region & AZ    | Size    | VPC    |
|---|---|---|---|---|---|---|
| aurora    | Available    | Regional cluster | Aurora MySQL   | us-west-2    | 1 instance    | -    |
| aurora-instance-1 | Available    | Writer instance | Aurora MySQL   | us-west-2a    | db.t3.medium    | vpc-off35/6cbd9f1c7ff|

# Task 3

## Configure the Amazon EC2 Linux instance to connect to Aurora

### Step 3: Review Endpoints
Choose the Connectivity & Security tab, and in the Endpoints section, copy the Endpoint name for the Writer instance.

---

**Endpoints (2)**

- [ ] A. _Find resources_

- [x] **Endpoint name**
- [ ] aurora.cluster=_Crewsm2ky6s6.us-west-2.rds.amazonaws.com
- [ ] aurora.cluster=_To-Crewsm2ky6s6.us-west-2.rds.amazonaws.com

---

**Actions**
- Create custom endpoint

| Status    | Type    | Port    |
|---|---|---|
| Available   | Writer    | 3306    |
| Available   | Reader    | 3306    |

---

### Step 4: Connect to Aurora
To connect to the Aurora instance, run the following command.

sh-4.25 mysql -u admin --password='admin123' -h aurora.cluster-c7ewsm2ky6s6.us-west-2.rds.amazonaws.com
Welcome to the Mariano monitor. Commands end with ; or \q.
Your MySQL connection is 104
Server version: 8.0.28 Source distribution

Copyright (c) 2000, 2018, Oracle, Mariano Corporation Ab and others.

Type 'help:' or '\h' for help. Type '\v' to clear the current input statement.

MySQL [ (none)]>

# Task 4

---

**Create a table and insert and query records**

---

## Step 1: Switch to the world database

To list the available databases and switch to the world database, run the following commands.

[MySQL [{none}]> SHOW DATABASES;
+---+    +---+
| Database    |    |
+---+    +---+
| information_schema |    |
| mysql    |    |
| performance_schema |    |
| sys    |    |
| world    |    |
+---+    +---+

5 rows in set (0.00 sec)

[MySQL [{none}]> USE world;
Database changed
[MySQL [world]>

---

## Step 2: Create a new table

To create a new table in the world database, run the following command.

[MySQL [world]> CREATE TABLE 'country' {
    -> Code' CURR(3) NOT NULL DEFAULT '',
    -> 'Name' CHAR(3) NOT NULL DEFAULT '',
    -> 'Continent' enum('Asia', 'Europe', 'North America', 'Africa', 'Oceania', 'Antarctica', 'South America') NOT NULL DEFAULT 'Asia',
    -> 'Region' CHAR(26) NOT NULL DEFAULT '',
    -> 'Surfacebars' FLOAT(10,2) NOT NULL DEFAULT '0.00',
    -> 'Indeproxl' SHALLIFY(6) DEFAULT NULL,
    -> 'Population' INT(11) NOT NULL DEFAULT '0',
    -> 'Lifespectancy' FLOAT(3,1) DEFAULT NULL,
    -> 'CRP' FLOAT(10,2) DEFAULT NULL,
    -> 'GNDOld' FLOAT(10,2) DEFAULT NULL,
    -> 'LocalName' CHAR(45) NOT NULL DEFAULT '',
    -> 'GovernmentForm' CHAR(45) NOT NULL DEFAULT '',
    -> 'Capital' INT(11) DEFAULT NULL,
    -> 'Code2' CHAR(2) NOT NULL DEFAULT '',
    -> PRIMARY KEY ('Code')
    -> );
Query OK, 0 rows affected, 7 warnings (0.04 sec)

Task 4
Create a table and insert
and query records
To insert new records into the country table that you just
created, run the following commands.
Step 3: Insert new records
To query the table, run the following SELECT statement.
Step 4: Query the table

# Conclusions

## Amazon Aurora
Amazon Aurora offers high performance and scalability, making it an ideal choice for managing large datasets efficiently.

## Create an Aurora instance
Creating an Aurora instance provides users with a robust and reliable database solution tailored to their specific needs.

## Connect to an Amazon EC2 instance
Connecting to an Amazon EC2 instance enables seamless integration and utilization of Aurora's advanced features.

## Configure the EC2 instance to connect to Aurora
Configuring the EC2 instance to connect to Aurora ensures smooth communication and data accessibility between applications and databases.

## Query the Aurora instance
Querying the Aurora instance allows for extracting valuable insights and performing data analysis, supporting informed decision-making processes.

