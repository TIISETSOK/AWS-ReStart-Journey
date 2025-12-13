
# AWS Identity and Access Management (IAM): RBAC & Least Privilege

In many companies, you only need one username and password to log in.

Once you’re in, you can use everything connected to the company’s network like the personal files, shared folders, the company’s internal website, printers, and other devices.

This is risky because if the login system isn’t set up properly, a bad actor (hacker or unauthorized person) could sneak in.

### In this project i will showcase how i can:

- Create and apply an IAM password policy

- Explore pre-created IAM users and user groups

- Inspect IAM policies as applied to the pre-created user groups

- Add users to user groups with specific capabilities active

- Locate and use the IAM sign-in URL

- Experiment with the effects of policies on service access

**to enhance netwok security and enforce the principle of least privilege, ensuring that only authorized users receive appropriate access while reducing the risk of unauthorized exploitation.**

---

##  Architecture & Business Scenario

This diagram of the current environment with the listed IAM users and IAM groups.

<img width="753" height="385" alt="Screenshot 2025-12-10 133832" src="https://github.com/user-attachments/assets/c7416147-550d-4cd7-b693-c11e69461c40" />


---

# Task 1; Creating a Custom Account Password Policy  
The first task is to strengthen the password requirements by creating a custom password policy. I added password options to make the passwords that the users create much more difficult to crack.

### **Step 1; I Accessed IAM services**
- I logged in to the AWS Console. 
- Opened the IAM service  
- Reviewed the dashboard and security status  

### **Step 2; Review Default Password Policy**
- I Navigated to **Account Settings**  
- Viewed the default account password policy  
- And then selected **Edit** to create a new custom policy  

### **Step 3; I configured a New Password Policy**
I applied a secure password policy that included:  
- Minimum password length  
- Required password complexity  
- Password expiration rules  
- Password reuse prevention  

This will ensure strong access security measures are required from all IAM users.

---

# Task 2.

- **Exploring IAM Users and Groups**

In this task i reviewed pre-created users along with the pre-created user groups. I Checked the attached polices to the user groups and what the differences between the user groups and their permissions are.

### **Step 1; Review IAM Users**
I navigated to **IAM services** and clicked on **Users**, to observe:  
- that three users existed  
- that each user had no permissions assigned  
- that no group memberships were active  
- that users had console passwords configured  

### **Step 2; Reviewing IAM Groups ** 
Navigated to **IAM services** and selected **User Groups**, ensure the existance of: 
- **EC2 Support**  
- **S3 Support**  
- **EC2 Admin**

Groups allow scalable permission management for multiple users.

---

# Task 3

- **Assigning Users to Groups** 

### Step 1; I reviewed user group memhe user groups and had  to tbers.

- There were no members in any of the user groups so i had to associate one user with each group.

### Step 2; I added user1 to the S3 support group

<img width="1277" height="431" alt="Screenshot 2025-12-13 192408" src="https://github.com/user-attachments/assets/db24f89c-174a-4fe4-a63a-5afcdc9de215" />

### Step 3; I added user-2 to EC2- support

---

# Task 4.

- **Here i will be:**

- testing User Permissions.

- Validating that all permissions were applied correctly.

### Step 1; Logged in as user-1

- I logged in as each user using the IAM User Sign-In URL IAM users.
<img width="819" height="784" alt="Screenshot 2025-12-13 221948" src="https://github.com/user-attachments/assets/09ad7e10-df9a-427a-a1e5-755d2ffcba66" />

### Step 1; Testing user-1 (S3-Support)**  
**Allowed:**  
- View S3 bucket list  
- View bucket contents and objects  

### **Step 2; Testing user-2 (EC2-Support)**  
**Allowed:**  
- View EC2 instances (read-only)  
<img width="694" height="723" alt="Screenshot 2025-12-13 221831" src="https://github.com/user-attachments/assets/34ef51b4-2c41-4bdb-8c89-6c7516ad9cb0" />

**Denied:**  
- Stopping EC2 instances

<img width="1304" height="258" alt="Screenshot 2025-12-13 222207" src="https://github.com/user-attachments/assets/84f6b5f1-4236-49eb-80ca-af8ed036b3bb" />


- Accessing S3 buckets  

Permission errors confirmed that read-only restrictions were in place.

---

### **Step 3 Testing user-3 (EC2-Admin)**  
**Allowed:**  
- View EC2 instances  
- Stop EC2 instances (admin permissions)  

---

# Conclusions  
AWS Identity and Access Management (IAM) helps securely manage who can access AWS resources and what actions they can perform. It uses users, groups, roles, and policies to organize permissions and control access efficiently across services.

