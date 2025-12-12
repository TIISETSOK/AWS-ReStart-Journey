# Amazon Aurora

- Aurora is a fully managed, MySQL-compatible, relational database engine..

- It combines the performance and reliability of high-end commercial databases with the simplicity and cost-effectiveness of open-source databases.

- It delivers up to five times the performance of MySQL without requiring changes to most of your existing applications that use MySQL databases.

## What i did in this Lab:

- I created an Aurora instance
- I connected to a pre-created Amazon Elastic Compute Cloud (Amazon EC2) instance
- And configured the Amazon EC2 instance to connect to Aurora Query the Aurora instance

## Task 1

Create an Aurora instance

### **Step 1, I accessed the RDS database service**

- I opened the AWS Management Console, and selected the RDS.

### **Step 2, I Created a database**

- By navigating to the Databases section, and selecting Create database.

### **Step 3, I chose a database creation method**

- I went to the **Choose** a database creation method section and choose Standard create.

- I chose **Standard create** so that i can set all of the configuration options, including the ones for availability, security, backup, and maintenance.

### **Step 4, choosing an engine option**

- In the **Engine options** section, for Engine type, I chose Aurora (MySQL Compatible).
  
- For Engine version I chose the default for major version 8.0.

### **Step 5, I chose a templates**
- In the Templates section, I chose the Dev/Test option.

- I chose this instance is beacuse it is intended for development use outside of a production environment.

### **Step 6, I configured Settings**

I went into the Settings section to configure the following options:

- The **DB cluster identifier** info, i set its name to "aurora"

- **Credentials Settings**, for the masaster username (admin), I typed a Login ID for the master user of the  DB instance.

- I then set the **master password** and confirmed it


### **Step 7, here I configured the insstance***

In the **Instance configuration** section, for DB instance class, I configureD the following settings.
<img width="1523" height="1013" alt="Screenshot 2025-12-11 140856 copy" src="https://github.com/user-attachments/assets/4ba162ac-f7be-420a-a461-afbfe234dd6f" />


## Step 8, Reviewd Availability & durability

In the **Availability & durability** section, for Multi-AZ deployment,I chose Don't create an Aurora Replica.


## Step 9, I Customized Connectivity
In the Connectivity section, I configured the following options.
- For **Virtual private cloud (VPC)**, I chose **LabVPC**.
- For **Subnet group**, I chose **dbsubnetgroup**.
- For **Public access**, I selected **No**.
- For **VPC security group**, I selected **Choose existing**.
- For **Existing VPC security groups**, i removed the **default** security group.
- From the **Existing VPC security groups** dropdown list, i choose **DBSecurityGroup**.


## Step 10: Monitoring
- In the Monitoring section, for Additional configuration, clear the check box for Enable Enhanced Monitoring.

- And for  Additional configuration i kept it at enhanced Monitoring

- This is because enabling Enhanced Monitoring metrics are enabled when you want to see how different processes or threads use the CPU.


## Step 11, I added Additional configuration

In the **Additional configuration** section, i  named the initial database "world" and De-selected the rest of the options.

## Step 12, I reviewed database instance creation

Verified the availability of the aurora-instance-1 database.

<img width="1920" height="1020" alt="Screenshot 2025-12-11 141706" src="https://github.com/user-attachments/assets/913e5ac2-f5ff-482c-b501-5caad027b652" />


# Task 2

Connect to an Amazon EC2 Linux instance

### **Step 1, I Access the EC2 Management Console**

In the AWS Management Console, I selected EC2.
<img width="1920" height="1080" alt="Screenshot 2025-12-11 141923" src="https://github.com/user-attachments/assets/0b491946-3665-4e33-860e-af6c1fa11700" />


### **Step 2, I reviewed the running EC2 instances**

I navigated to the Instances section and saw that the running Command Host EC2 instance is listed.


### **Step 3, I connected to the instance***
Connect to the Command Host EC2 instance using Session Manager.

<img width="1920" height="1020" alt="Screenshot 2025-12-11 142025" src="https://github.com/user-attachments/assets/153692cb-0149-43c4-9bba-a15647ee27d4" />


### **Step 4, I reviewed connection**
it showedd that i have successfully connected to the Amazon EC2 instance named **Command Host** by launching the Command line.

<img width="1543" height="1020" alt="Screenshot 2025-12-11 142147" src="https://github.com/user-attachments/assets/5b3c5ef5-e32f-4111-8c1c-d100cf7130a0" />


# Task 3

**I configured the Amazon EC2 Linux instance to connect to Aurora**

## Step 1: Install the DB client
I used the mysql -u admin --password='admin123' -h aurora.cluster-cu2lcxfwmcve.us-west-2.rds.amazonaws.com command to install the Maria DB client.

<img width="1920" height="1080" alt="Screenshot 2025-12-11 142451" src="https://github.com/user-attachments/assets/cc344b0e-8558-4a96-b8bb-a6e05972d9f8" />



## Step 2: I reviewed the Aurora DB cluster

i went back to the RDS Management Console, navigated to the Databases section, and selected the aurora DB cluster.


# Task 3

## Configure the Amazon EC2 Linux instance to connect to Aurora

### Step 3: Review Endpoints
I choose the Connectivity & Security tab, and in the Endpoints section, copy the Endpoint name for the Writer instance.


### Step 4: Connect to Aurora
To connect to the Aurora instance, i had to run the following command.

sh-4.25 mysql -u admin --password='admin123' -h aurora.cluster-c7ewsm2ky6s6.us-west-2.rds.amazonaws.com
Welcome to the Mariano monitor. Commands end with ; or \q.
Your MySQL connection is 104
Server version: 8.0.28 Source distribution

# Task 4


**Created a table and insert and query records**

## Step 1: Switch to the world database

To list the available databases and switch to the world database, I run the following command.

```sql
USE world;
```

## Step 2, I ceated a new table

To create a new table in the world database, run the following command.


CREATE TABLE `country` (
`Code` CHAR(3) NOT NULL DEFAULT '',
`Name` CHAR(52) NOT NULL DEFAULT '',
`Continent` enum('Asia','Europe','North America','Africa','Oceania','Antarctica','South America') NOT NULL DEFAULT 'Asia',
`Region` CHAR(26) NOT NULL DEFAULT '',
`SurfaceArea` FLOAT(10,2) NOT NULL DEFAULT '0.00',
`IndepYear` SMALLINT(6) DEFAULT NULL,
`Population` INT(11) NOT NULL DEFAULT '0',
`LifeExpectancy` FLOAT(3,1) DEFAULT NULL,
`GNP` FLOAT(10,2) DEFAULT NULL,
`GNPOld` FLOAT(10,2) DEFAULT NULL,
`LocalName` CHAR(45) NOT NULL DEFAULT '',
`GovernmentForm` CHAR(45) NOT NULL DEFAULT '',
`Capital` INT(11) DEFAULT NULL,
`Code2` CHAR(2) NOT NULL DEFAULT '',
PRIMARY KEY (`Code`)
);
Query OK, 0 rows affected, 7 warnings (0.04 sec)


# Conclusions

-Amazon Aurora offers high-performance and scalable database solutions. Creating an Aurora instance allows efficient data management, while connecting to Amazon EC2 instances streamlines integration.

-Configuring EC2 to connect to Aurora ensures smooth data communication, enabling seamless querying for valuable insights and informed decision-making.

Overall, Aurora's advanced features and architecture simplify database administration and enhance performance, making it a top choice for scalable and reliable data solutions.

