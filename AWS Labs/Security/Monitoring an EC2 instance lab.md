
# AWS EC2 Instance Monitoring Lab

## Overview
Logging and monitoring are techniques implemented to achieve a common goal. They work together to help ensure that a system's performance baselines and security guidelines are always met.

**Logging** refers to recording and storing data events as log files. Logs contain low-level details that can give you visibility into how your application or system performs under certain circumstances. From a security standpoint, logging helps security administrators identify red flags that are easily overlooked in their system.

**Monitoring** is the process of analyzing and collecting data to help ensure optimal performance. Monitoring helps detect unauthorized access and helps align your services' usage with organizational security.

In this lab, you create an Amazon CloudWatch alarm that initiates when the Amazon Elastic Compute Cloud (Amazon EC2) instance exceeds a specific central processing unit (CPU) utilization threshold. You create a subscription using Amazon Simple Notification Service (Amazon SNS) that sends an email to you if this alarm goes off. You log in to the EC2 instance and run a stress test command that causes the CPU utilization of the EC2 instance to reach 100 percent.

This test simulates a malicious actor gaining control of the EC2 instance and spiking the CPU. CPU spiking has various possible causes, one of which is malware.

## Task 1: Configure Amazon SNS

### Step 1: Access the Simple Notification Service
Open the AWS Management Console, and select Simple Notification Service.

### Step 2: Create topic
Navigate to the Topics section and select Create topic.

### Step 3: Topic Details
On the Create topic page in the Details section, configure the following options.

**Details**
Type Info
Topic type cannot be modified after topic is created

- FIFO (first-in, first-out)
- Standard

**Name**
MyCwAlarm

### Step 4: Create subscription
On the MyCwAlarm details page, choose the Subscriptions tab, and then choose Create subscription.

### Step 5: Subscription Details
On the Create subscription page in the Details section, configure the following options.

**Details**

Topic ARN
arn:aws:sns:us-west-2:590185674979:MyCwAlarm

Protocol
The type of endpoint to subscribe

Email

Endpoint
An email address that can receive notifications from Amazon SNS.

cristhianbecerra99@gmail.com

### Step 6: Subscription Confirmation
Open the email that you received with the Amazon SNS subscription notification, and choose Confirm subscription.

## Task 2: Create a CloudWatch alarm

### Step 1: Access the CloudWatch console
Open the AWS Management Console, and select CloudWatch.

### Step 2: Review Metrics
On the Metrics page, choose EC2, and choose Per-instance Metrics. Select the CPUUtilization metric for the Stress Test EC2 instance.

### Step 3: Create alarm
Navigate to the Alarms section and select Create alarm.

### Step 4: Select metric
On the Metric section, choose EC2, and choose Per-Instance Metrics. Select the CPUUtilization metric for the Stress Test EC2 instance.

### Step 5: Specify metric and conditions
On the Specify metric and conditions page, configure the following options.

**Metric**

Namespace AWS/EC2
Metric name CPUUtilization
InstanceId i-0c9db06c2e8be5
Instance name Stress Test
Statistic Average
Period 1 minute

**Conditions**

Threshold type
- Static
- Anomaly detection

Whenever CPUUtilization is...
- Greater > threshold
- Greater/Equal >= threshold
- Lower/Equal <= threshold
- Lower < threshold

than...
60

### Step 6: Configure actions
On the Notification section, configure the following options.

**Notification**

Alarm state trigger
Define the alarm state that will trigger this action.

- In alarm
- OK
- Insufficient data

Send a notification to the following SNS topic
Define the SNS (Simple Notification Service) topic that will receive the notification.

- Select an existing SNS topic
- Create new topic
- Use topic ARN to notify other accounts

Send a notification to...

- MyCwAlarm

Email endpoints
cristhianbecerra99@gmail.com

### Step 7: Add name and description
On the Name and description section, configure the following options.

**Name and description**

Alarm name
LabCPUUtilizationAlarm

Alarm description - optional
CloudWatch alarm for Stress Test EC2 instance CPUUtilization

## Task 3: Test the CloudWatch alarm

### Step 1: Increase the CPU load
Log in to the Stress Test EC2 instance and run the following command to manually stress the CPU load to 100 percent.

stress --cpu 8 --io 4 --vm 2 --vm-bytes 128M --timeout 400s

### Step 2: Review CPU usage
Run the top command to show the live CPU usage.

top - 18:08:39 up 36 min, 0 users, load average: 9.19, 3.95, 1.50
Tasks: 100 total, 11 running, 89 sleeping, 0 stopped, 0 zombie
%Cpu(s): 100.0 us, 0.0 sy, 0.0 ni, 0.0 id, 0.0 wa, 0.0 hi, 0.0 si, 0.0 st
Mem: 993492 total, 433741 free, 100731 used, 459016 buff/cache
Swap: 0 total, 0 free, 0 used, 750566 avail Mem

### Step 3: Review alarm state
Review the LabCPUUtilizationAlarm. The alarm state is In alarm.

### Step 4: Verify alarm notification
Review the new email from AWS Notifications in your inbox.

## Task 4: Create a CloudWatch dashboard

### Step 1: Create dashboard
Navigate to the Dashboards section and select Create dashboard.

### Step 2: Create new dashboard
For Dashboard name, enter LabEC2Dashboard.

### Step 3: Add widget
For Widget type, choose Line. For Metrics, choose EC2, and choose Per-Instance Metrics. Select the CPUUtilization metric for the Stress Test EC2 instance.

### Step 4: Review dashboard
Now you have created a quick access shortcut to view the CPUUtilization metric for the Stress Test instance.

## Conclusions

### Simple Notification Service
Simple Notification Service (SNS) facilitates seamless communication by sending notifications via email, SMS, or other messaging protocols.

### CloudWatch
CloudWatch serves as a monitoring and management service, providing insights into AWS resources and applications through logs, metrics, and alarms.

### CloudWatch Metrics
CloudWatch Metrics collect and visualize data points for AWS resources, enabling real-time monitoring and analysis of performance metrics.

### CloudWatch Alarms
CloudWatch Alarms notify users of specific conditions or thresholds within metrics, allowing for proactive response to potential issues or anomalies.

### CloudWatch Dashboards
CloudWatch Dashboards provide customizable views and visualizations of metrics and alarms, offering a centralized platform for monitoring and analysis.
