---

### **Task 1: S3 Bucket Creation and Replication**
1. **Objective:**  
   - Create an S3 bucket in the **Mumbai (ap-south-1)** region. Enable versioning on the bucket.  
   - Create another S3 bucket in the same region (**Mumbai**) and configure **Same-Region Replication (SRR)** between these buckets.  

2. **Steps to Perform:**  
   - Create the source bucket and enable versioning.  
   - Create the destination bucket in the same region.  
   - Configure the replication rule to replicate objects from the source bucket to the destination bucket.  

3. **Validation:**  
   - Upload objects to the source bucket and verify they are replicated to the destination bucket.

---

### **Task 2: Lifecycle Management Rules**
1. **Objective:**  
   - Create lifecycle management rules for an S3 bucket to optimize storage.  

2. **Requirements:**  
   - For **current version objects**, transition them from **S3 Standard** to **Delete** after **2 days**.  
   - For **previous version objects**, transition them to **Delete** after **1 day**.

3. **Steps to Perform:**  
   - Create an S3 bucket and enable versioning.  
   - Add lifecycle rules for current and previous version objects as specified.  

4. **Validation:**  
   - Verify that objects transition and are deleted as per the configured lifecycle rules.

---

### **Task 3: IAM Policy for Region-Restricted Bucket Creation**
1. **Objective:**  
   - Create an IAM policy that allows all S3 actions but restricts the user to creating buckets **only in the Mumbai (ap-south-1) region**.  

2. **Steps to Perform:**  
   - Create a custom IAM policy by copying permissions from **S3FullAccess** and restricting bucket creation to the **Mumbai** region.  
   - Attach the policy to a newly created IAM user.  
   - Log in as the IAM user and attempt the following:  
     - Create a bucket in **Mumbai** – this should be allowed.  
     - Attempt to create a bucket in any other region – this should be denied.  

3. **Validation:**  
   - Ensure the policy behavior is as expected:  
     - Bucket creation is permitted only in the **Mumbai** region.  
     - Bucket creation in any other region results in an **Access Denied** error.

---

### **Task 4: Access S3 Using Third-Party Applications**
**Objective:** Use third-party applications to access S3. (Tools: S3 Browser, Cyberduck, Cloudberry Explorer, WinSCP)

**Steps:**
1. **Create an IAM User:**
   - Navigate to the AWS Management Console → IAM Service.
   - Create a new user with programmatic access.
2. **Generate Access Key and Secret Key:**
   - Download the credentials file.
3. **Configure Third-Party Tools:**
   - Open the chosen third-party application.
   - Enter the Access Key, Secret Key, and region to configure access.
4. **Validate Access:**
   - Perform operations such as uploading or downloading files.

---

#### **Task 5: Generate a Presigned URL**
**Objective:** Understand and use presigned URLs to provide temporary access to S3 objects.

**Steps:**
1. **What is a Presigned URL?**
   - A presigned URL is a temporary URL to access an S3 object without requiring authentication.
2. **Generate a Presigned URL:**
   - Use AWS Console and generate a Presigned URL
3. **Validate:**
   - Access the URL within 60 seconds and verify its functionality.

---

#### **Task 6: Restrict IAM User to Access a Specific Bucket**
**Objective:** Ensure that an IAM user can only access a designated S3 bucket.

**Requirement:**
- The user has access to their own bucket (e.g., `bucketname`, `2505-avinash`).
- Provide permissions for upload, download, and delete.

**Validate:**
   - Log in as the IAM user and verify access.

---

#### **Task 7: Restrict Specific Actions on a Bucket**
Create an IAM user.. Provide him S3FullAccess.. But on a specific bucket "Deny" him to perform "DeleteObject, DeleteBucket, PutObject, getbucketpolicy"

---

#### **Task 8: Configure S3 to Trigger SNS Notifications**
**Objective:** Set up S3 events to trigger an email notification via SNS.

**Steps:**
1. **Create an S3 Bucket:**
   - Create a bucket in the S3 console.
2. **Create an SNS Topic and Subscriber:**
   - Create a new SNS topic.
   - Add an email subscriber and confirm the subscription.
3. **Configure S3 Events:**
   - In the S3 console, go to bucket properties → Event notifications.
   - Add events for object creation and deletion.
   - Link the SNS topic.
4. **Test:**
   - Upload and delete objects to verify notifications.

---

#### **Task 9: Apply IP Restriction on Bucket Policy**
**Objective:** Restrict bucket access based on IP addresses using both IAM and bucket policies.

**Steps:**
1. **IAM Policy Approach:**
   - Create an IAM policy with IP restrictions:
2. **Bucket Policy Approach:**
   - Apply a bucket policy with IP restrictions:
3. **Test:**
   - Access the bucket from allowed and disallowed IPs to validate the restriction.

--- 

### **Task 1: Launch a Windows EC2 Instance and Connect Using Key Pair
**
---

###**Task 2: Change the Password of Administrator**

1. Change Password of Administrator:  
2. Test Login with New Password:  
   - Disconnect the RDP session.  
   - Reconnect using the new password instead of retrieving it from the key pair.  
   - Verify both methods:  Ans..???
     - Login using the key-pair-generated password.  
     - Login using the custom password.

---

###**Task 3: Create a New User with Administrator and Remote Desktop Permissions**

1. Create a New User:  
   - Open Computer Management → Local Users and Groups → Users.  
   - Right-click and select New User.  
   - Fill in the details (e.g., `Username: JohnDoe`, Password: `UserPassword123`).  
   - Uncheck User must change password at next logon.

2. Assign Local Administrator Rights:  
   - Go to Local Users and Groups → Groups.  
   - Double-click Administrators → Add the new user (`JohnDoe`) to the group.

3. Grant Remote Desktop Permissions:  
   - Go to System Properties → Remote Settings.  
   - Under Remote Desktop, click Select Users → Add the new user (`JohnDoe`).

4. Test Login with New User:  
   - Open a new RDP session.  
   - Login with the new user credentials (`JohnDoe` and `UserPassword123`).  
   - Verify simultaneous access with both the Administrator and the new user.

---

###**Task 4: Install IIS and Deliver a Web Page (Optional)**

1. Install IIS:  
   - Open Server Manager → Manage → Add Roles and Features.  
   - Select Role-based or feature-based installation.  
   - Choose the current server.  
   - Enable Web Server (IIS) and proceed with the default features.  
   - Complete the installation.

2. Deploy a Web Page:  
   - Open File Explorer → Navigate to `C:\inetpub\wwwroot`.  
   - Replace or edit the `index.html` file with your custom webpage content:  
   
     ```html
     <!DOCTYPE html>
     <html>
     <head>
         <title>IIS-Task </title>
     </head>
     <body>
         <h1>Welcome to "AWS with Avinash Reddy" Trainings. Mater your cloud skills.!</h1>
         <p>Delivered Webpage via AWS EC2 Instance</p>
     </body>
     </html>
     ```

3. Open Security Group for HTTP:  
   - Add a rule in the instance’s security group to allow HTTP (port 80) traffic from Anywhere.

4. Access the Web Page:  
   - Open a browser and navigate to the Public IP of the EC2 instance (e.g., `http://<Public-IP>`).  
   - The custom webpage should be displayed.


---
