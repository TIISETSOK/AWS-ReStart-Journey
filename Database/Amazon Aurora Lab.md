# Amazon Aurora Fundermentals

This lab introduces Amazon Aurora and shows my understanding of how to use Aurora. 

# Task 1: Create an Aurora Instance

1. **Access RDS Service**  
   - Open the AWS Management Console → Select **RDS**.

2. **Create Database**  
   - Navigate to **Databases** → Click **Create database**.

3. **Choose Creation Method**  
   - Select **Standard create**.

4. **Engine Options**  
   - Engine type: **Aurora (MySQL Compatible)**  
   - Engine version: Default for MySQL 8.0.

5. **Templates**  
   - Choose **Dev/Test**.

6. **Settings**  
   - DB cluster identifier: `aurora`  
   - Master username: `admin`  
   - Master password: `admin123`

7. **Instance Configuration**  
   - DB instance class: `db.t3.medium` (2 vCPUs, 4 GiB RAM).

8. **Availability & Durability**  
   - Multi‑AZ deployment: **Don’t create Aurora Replica**.

9. **Connectivity**  
   - VPC: `LabVPC`  
   - Subnet group: `dbsubnetgroup`  
   - Public access: **No**  
   - Security group: `DBSecurityGroup`

10. **Monitoring**  
    - Disable **Enhanced Monitoring**.

11. **Additional Configuration**  
    - Initial database name: `world`  
    - Encryption: Disabled  
    - Auto minor version upgrade: Disabled

12. **Review & Launch**  
    - Verify `aurora-instance-1` is **Available**.
!!!!!!will insert picture!!!!!!
---

## Task 2: Connect to an Amazon EC2 Linux Instance

1. **Access EC2 Service**  
   - Open AWS Console → Select **EC2**.

2. **Review Running Instances**  
   - Confirm `Command Host` EC2 instance is running.

3. **Connect to Instance**  
   - Use **Session Manager** to connect.

4. **Verify Connection**  
   - Ensure shell prompt (`sh-4.2$`) is available.
   - 
!!!!!!!will insert oicture!!!!!!!
---

## Task 3: Configure EC2 to Connect to Aurora

1. **Install DB Client**  
   ```bash
   sudo yum install mariadb -y
   ```

2. **Review Aurora DB Cluster**  
   - In RDS Console, select `aurora`.

3. **Copy Endpoint**  
   - Writer endpoint:  
     ```
     aurora.cluster-c7ewsm2ky6s6.us-west-2.rds.amazonaws.com
     ```

4. **Connect to Aurora**  
   ```bash
   mysql -u admin --password='admin123' \
     -h aurora.cluster-c7ewsm2ky6s6.us-west-2.rds.amazonaws.com
   ```
!!!!!!!will insert picture!!!!!
---

## Task 4: Create Table, Insert & Query Records

1. **Switch to Database**  
   ```sql
   SHOW DATABASES;
   USE world;
   ```

2. **Create Table**  
   ```sql
   CREATE TABLE country (
     Code CHAR(3) NOT NULL,
     Name CHAR(52) NOT NULL,
     Continent ENUM('Asia','Europe','North America','Africa','Oceania','Antarctica','South America') NOT NULL,
     Region CHAR(26) NOT NULL,
     SurfaceArea FLOAT(10,2) NOT NULL,
     IndepYear SMALLINT,
     Population INT NOT NULL,
     LifeExpectancy FLOAT(3,1),
     GNP FLOAT(10,2),
     GNPOld FLOAT(10,2),
     LocalName CHAR(45) NOT NULL,
     GovernmentForm CHAR(45) NOT NULL,
     Capital INT,
     Code2 CHAR(2) NOT NULL,
     PRIMARY KEY (Code)
   );
   ```

3. **Insert Records**  
   ```sql
   INSERT INTO country VALUES ('AUS','Australia','Oceania','Australia and New Zealand',7741220.00,1901,18886000,79.8,351182.00,392911.00,'Australia','Constitutional Monarchy, Federation',135,'AU');
   INSERT INTO country VALUES ('THA','Thailand','Asia','Southeast Asia',513115.00,1350,61399000,68.6,116416.00,153907.00,'Prathet Thai','Constitutional Monarchy',3320,'TH');
   -- Add more records as needed
   ```

4. **Query Records**  
   ```sql
   SELECT * FROM country
   WHERE GNP > 35000 AND Population > 10000000;
   ```
   !!!!!!will insert picture!!!!!!!!
