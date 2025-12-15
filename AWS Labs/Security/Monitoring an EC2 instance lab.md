
# AWS EC2 Instance Monitoring Lab

## Overview
Logging and monitoring are techniques that are implemented to achieve a common goal. They work together to help ensure that a system's performance baselines and security guidelines are always met.

**Logging** refers to recording and storing data events as log files. Logs contain low-level details that can give you visibility into how your application or system performs under certain circumstances. From a security standpoint, logging helps security administrators identify red flags that are easily overlooked in their system.

**Monitoring** is the process of analyzing and collecting data to help ensure optimal performance. Monitoring helps detect unauthorized access and helps align your services' usage with organizational security.

## What i will be doing in this lab.

- In this lab, I will create an Amazon CloudWatch alarm that initiates when the Amazon Elastic Compute Cloud (Amazon EC2) instance exceeds a specific central processing unit (CPU) utilization threshold.
- I will  create a subscription using Amazon Simple Notification Service (Amazon SNS) that sends an email to you if this alarm goes off.
- I logged in to the EC2 instance and ran a stress test command that causes the CPU utilization of the EC2 instance to reach 100 percent.
- This test simulates a malicious actor gaining control of the EC2 instance and spiking the CPU. CPU spiking has various possible causes, one of which is malware.

## Task 1:

**Configure Amazon SNS**

### Step 1: Accessing the Simple Notification Service

- I opened the AWS Management Console, and selected Simple Notification Service.

### Step 2: I createed a topic

- I did this by navigating to the Topics section and selected Create topic.

### Step 3: Setting up Topic Details

- in the Create topic page in the Details section, I configured the following options.

<img width="1010" height="462" alt="image" src="https://github.com/user-attachments/assets/194d6e65-8fd7-43c8-8169-44a80e34bf0a" />

### Step 4: Creating subscription
- On the MyCwAlarm details page, I chose the Subscriptions tab, and then chose Create subscription.

### Step 5: Setting up Subscription Details

- On the Create subscription page in the Details section, I configured the **Details** by choosing a Topic ARN
`arn:aws:sns:us-west-2:590185674979:MyCwAlarm`
- The Protocol thar i chose was email and i enterd my personal email

### Step 6: Subscription Confirmation

- I opened the email that i received with the Amazon SNS subscription notification, and choose Confirm subscription.

<img width="906" height="240" alt="image" src="https://github.com/user-attachments/assets/721605fb-bf52-4db9-a01b-b32e1c2052f0" />


## Task 2: 

**I created a CloudWatch alarm**

### Step 1: Accessing the CloudWatch console

- I opened the AWS Management Console, and select CloudWatch.

### Step 2: Reviewing Metrics

- In the Metrics page,i chose EC2, and Per-instance Metrics. 
- I selected the CPUUtilization metric for the Stress Test EC2 instance.

### Step 3: Creating alarm

- I navigated to the Alarms section and selected Create alarm.

### Step 4: Selected a  metric

- I navigated to the Metric section, chose EC2, and chose Per-Instance Metrics. - I selected the CPUUtilization metric for the Stress Test EC2 instance.

### Step 5: Specified metrics and conditions

- On the Specify metric and conditions page, I configured the following options.

<img width="917" height="642" alt="image" src="https://github.com/user-attachments/assets/3555eea6-d4a6-410c-b617-b11065559a10" />


<img width="927" height="462" alt="image" src="https://github.com/user-attachments/assets/c1aae26c-d66d-4077-9c27-dc19404e3b45" />

### Step 6: Configured actions

- In the Notification section, I configured the following options.

<img width="911" height="530" alt="Screenshot 2025-12-15 025224" src="https://github.com/user-attachments/assets/000a7041-9075-4f05-bde9-686101976439" />


### Step 7: Adding name and description

- In the Name and description section, configure the following options.

  <img width="815" height="412" alt="image" src="https://github.com/user-attachments/assets/9596bc50-ad78-4a17-9315-1aa6be5d53a5" />

## Task 3: Tested the CloudWatch alarm

### Step 1: I increased the CPU load
- I logged in to the Stress Test EC2 instance and ran the following command to manually stress the CPU load to 100 percent.

- **stress --cpu 8 --io 4 --vm 2 --vm-bytes 128M --timeout 400s***

### Step 2: Reviewed CPU usage

- Ran the **top** command to show the live CPU usage.

<img width="914" height="417" alt="Screenshot 2025-12-15 025956" src="https://github.com/user-attachments/assets/7f400e91-37b9-4618-8886-47212b749d0a" />


### Step 3: Reviewed alarm state

- Reviewed the LabCPUUtilizationAlarm.
-<img width="837" height="348" alt="image" src="https://github.com/user-attachments/assets/63b6e600-8d1c-4994-a751-e16470ee4266" />

- The alarm state is In alarm.

### Step 4: Verified the alarm notification.

- Reviewed the new email from AWS Notifications in your inbox.

## Task 4

**Created a CloudWatch dashboard**

### Step 1: Created the  dashboard
Navigatde to the Dashboards section and select Create dashboard.

### Step 2: Create new dashboard
For Dashboard name, I entered LabEC2Dashboard.

### Step 3: Add widget
For Widget type, choose Line. For Metrics, choose EC2, and choose Per-Instance Metrics. Select the CPUUtilization metric for the Stress Test EC2 instance.
<img width="1010" height="333" alt="image" src="https://github.com/user-attachments/assets/0e17f6cb-11ee-4601-8908-0f05af5f4afc" />

### Step 4: Reviewed dashboard
Now I have created a quick access shortcut to view the CPUUtilization metric for the Stress Test instance.

<img width="577" height="533" alt="image" src="https://github.com/user-attachments/assets/8874d443-eb01-4e42-b9dc-ed273ec1e1b9" />


## Conclusions

### Simple Notification Service
Simple Notification Service (SNS) facilitates seamless communication by sending notifications via email, SMS, or other messaging protocols.
### - CloudWatch
CloudWatch serves as a monitoring and management service, providing insights into AWS resources and applications through logs, metrics, and alarms.
### CloudWatch Metrics
CloudWatch Metrics collect and visualize data points for AWS resources, enabling real-time monitoring and analysis of performance metrics.
### CloudWatch Alarms
CloudWatch Alarms notify users of specific conditions or thresholds within metrics, allowing for proactive response to potential issues or anomalies.
### CloudWatch Dashboards
CloudWatch Dashboards provide customizable views and visualizations of metrics and alarms, offering a centralized platform for monitoring and analysis.
