# Introduction to Amazon EC2

## Overview

* **Amazon Elastic Compute Cloud (Amazon EC2)** is a web service that provides secure, resizable compute capacity in the cloud.
* It is designed to make web-scale cloud computing easier for developers. 
* Through Amazon EC2, users can deploy and manage virtual machines (VMs) on AWS infrastructure, supporting both Microsoft Windows and Linux environments.
* VMs are categorized into various **instance types**, each offering different combinations of CPU, memory, storage, and networking capacity.
* Amazon EC2 offers flexible pricing models that allow users to pay only for the compute resources they use.

## Topics I Covered in this Lab:

* Launched a web server with termination protection enabled.
* Monitored your EC2 instance.
* Modified the security group to allow HTTP access.
* Resized your Amazon EC2 instance to scale.
* Tested termination protection.
* Terminated your EC2 instance.

---

## Task 1:

**Launching Your EC2 Instance**

### Step 1: Open the Amazon EC2 Console

* In the AWS Management Console on the Services menu, I chose **EC2**.

### Step 2: Launched an Instance

* In the EC2 Dashboard page, I select **Launch Instance** button. 

### Step 3: Naming the EC2 Instance

* In the **Name and tags** section, I assigned a name (e.g., `MyWebServer`) to the instance.

### Step 4: I configured Instance Settings.

* **Application and OS Images (Amazon Machine Image)**: Select the Amazon Linux 2 AMI.
* **Instance type**: Choose a **t2.micro** instance type.
* **Key pair (login)**: Select an existing key pair or create a new one.

### Step 5: Configure Network Settings

* **VPC**: Select the appropriate Virtual Private Cloud (VPC).
* **Subnet**: Select a public subnet.
* **Auto-assign Public IP**: Enable this option.
* **Firewall (Security Groups)**: Create a new security group named `WebSecurityGroup`.

### Step 6: Configure Storage and Advanced Details

* **Storage (volumes)**: Leave the default settings for the root volume.
* **Advanced details**: Locate the **Termination protection** setting and **Enable** it.

### Step 7: Launch the Instance

* Review the configuration and select **Launch instance**.
<img width="738" height="147" alt="image" src="https://github.com/user-attachments/assets/34a3df6e-89af-45a0-b783-246f5b6a7ab4" />

---

## Task 2: Monitoring Your EC2 Instance

### Step 1: Review Instance Status

* After launching, view the instance details and ensure the **Instance state** is `running` and **Status check** passes (`2/2 checks passed`).

### Step 2: Testing Instance Reachability

* Pinged the instance's Private IP address from the AWS Command Line Interface (CLI) or another authorized host to confirm reachability.

---

## Task 3: 

**Modify the Security Group**

### Step 1: Accessed Security Groups

* In the EC2 console, I navigated to **Security Groups** under the **Network & Security** section.
* I selected the `WebSecurityGroup` created earlier.

### Step 2: I added an Inbound Rule (Allow HTTP)

* I selected the **Inbound rules** tab, and chose **Edit inbound rules**. 
* Added a new rule:
    * **Type**: `HTTP`
    * **Source**: `Anywhere` (`0.0.0.0/0`)
* Saved the rules.

### Step 3: Connect to the Web Server

* Use the instance's **Public IPv4 address** in a web browser to confirm that the web server is reachable via HTTP.

---

## Task 4:
**Resizing Your EC2 Instance**

### Step 1: Changed the Instance Type

* I selected the running instance.
* Went  to Actions option and clicked the Instance settings and changed the changed instance type. 
* Changed the instance type from `t2.micro` to `t2.small`.

### Step 2: I stopped and Started the Instance

* The instance must be stopped and restarted for the instance type change to take effect.
* From the actions i navigated to the  Instance state and clicked on Stop instance**.
* Once stopped, **Actions > Instance state > Start instance**.
* Verified the new instance type is now `t2.small`.
<img width="647" height="257" alt="image" src="https://github.com/user-attachments/assets/dbdd1477-f405-417c-9dea-d793ea79a0f9" />

---

## Task 5 & 6: Testing and Terminating Your Instance

### Step 1: Tested Termination Protection

* Selected the running instance.
* Go to **Actions > Instance state > Terminate instance**.
* I got and reviewd the error message: `Failed to terminate an instance: The instance may not be terminated. This is because it has termination protection enabled.`

### Step 2: Here i turned Off Termination Protection

* I selected the instance.
* Went to **Actions > Instance settings > Change termination protection**. 
* Disabled termination protection.

  <img width="502" height="312" alt="image" src="https://github.com/user-attachments/assets/4584010c-6f40-4f29-afe7-4fb5fadfd133" />


### Step 3: I terminated the Instance

* Selected the instance.
* Went to **Actions > Instance state > Terminate instance**.
* Confirmed the termination.
*  The instance state transitioned from `shutting-down`, and then to `terminated`.
<img width="568" height="108" alt="image" src="https://github.com/user-attachments/assets/ad8ddf8d-264f-4764-8e62-9312bc81682a" />

---

## Conclusions

* **Launching Your EC2 Instance**: The launch wizard allows quick deployment of an instance with customizable parameters tailored to various use cases.
* **Monitoring Your Instance**: Monitoring instances using AWS's tools is essential to ensure instance reachability and early identification of issues for troubleshooting purposes.
* **Security Groups**: A security group functions as a firewall, restricting the network traffic allowed in and out of an instance, enhancing security.
* **Resizing Your Instance**: You can modify multiple parameters of your instance, such as instance type, disk space, and network settings, as your computing requirements evolve.
* **Terminating Your Instance**: Termination protection prevents instances from being unintentionally terminated. Terminating an instance causes both the instance itself and its attached storage volume to be shut down, effectively ceasing cost consumption.
