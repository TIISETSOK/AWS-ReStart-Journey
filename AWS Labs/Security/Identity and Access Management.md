
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

# Task 1. Creating a Custom Account Password Policy  
The first task is to strengthen the password requirements by creating a custom password policy. I added password options to make the passwords that the users create much more difficult to crack.

### **Step 1, I Accessed IAM services**
- I logged in to the AWS Console. 
- Opened the IAM service  
- Reviewed the dashboard and security status  

### **Step 2, Review Default Password Policy**
- I Navigated to **Account Settings**  
- Viewed the default account password policy  
- And then selected **Edit** to create a new custom policy  

### **Step 3, I configured a New Password Policy**
I applied a secure password policy that included:  
- Minimum password length  
- Required password complexity  
- Password expiration rules  
- Password reuse prevention  

This will ensure strong access security measures are required from all IAM users.

---

# Task 2. Exploring IAM Users and Groups

## Step 1, Review IAM Users
I navigated to **IAM services** and clicked on **Users**, to observe:  
- that three users existed  
- that each user had no permissions assigned  
- that no group memberships were active  
- that users had console passwords configured  

## Step 2 Reviewing IAM Groups  
Navigated to **IAM services** and selected **User Groups**, ensure the existance of: 
- **EC2 Support**  
- **S3 Support**  
- **EC2 Admin**

### Group Policy Details
- **EC2-Support:** AWS-managed EC2 read-only policy  
- **S3-Support:** AWS-managed S3 read-only policy  
- **EC2-Admin:** Custom inline policy with administrative EC2 permissions  

Groups allow scalable permission management for multiple users.

---

# 3. Assigning Users to Groups  

After analyzing group permissions, users were assigned as follows:

| User   | Group Assigned     | Purpose |
|--------|---------------------|---------|
| user-1 | S3-Support         | S3 read-only access |
| user-2 | EC2-Support        | EC2 read-only access |
| user-3 | EC2-Admin          | EC2 admin privileges |

Assignments were completed via:  
**IAM → Users → Select User → User Groups → Add to Group**

This implements the principle of least privilege effectively.

---

# 4. Testing User Permissions  

To validate that permissions were applied correctly, I logged in as each user using the IAM User Sign-In URL.

---

## **4.1 Testing user-1 (S3-Support)**  
**Allowed:**  
- View S3 bucket list  
- View bucket contents and objects  

**Denied:**  
- View EC2 instances  

---

## **4.2 Testing user-2 (EC2-Support)**  
**Allowed:**  
- View EC2 instances (read-only)  

**Denied:**  
- Stopping EC2 instances  
- Accessing S3 buckets  

Permission errors confirmed that read-only restrictions were in place.

---

## **4.3 Testing user-3 (EC2-Admin)**  
**Allowed:**  
- View EC2 instances  
- Stop EC2 instances (admin permissions)  

---

# 🧾 Conclusions  

* **Least Privilege:** Verified that users could only perform actions explicitly allowed by their group policies.
* **Scalability:** Demonstrated that managing permissions via Groups is significantly more efficient than managing individual users.
* **Security Posture:** Understood the importance of strong account-wide password policies.
* **Managed vs. Inline Policies:** Gained experience with AWS Managed policies for general use cases and custom Inline policies for specific admin rights.

