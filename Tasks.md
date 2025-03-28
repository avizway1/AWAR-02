## AWS CLI Task Guide
### Task 1: Launch an EC2 Instance Using AWS CLI  
**Objective:**  
Launch an EC2 instance with the following parameters using the AWS CLI:  
- AMI ID: Specify the desired AMI.  
- Instance Type: Choose an appropriate instance type (e.g., t2.micro).  
- Subnet ID: Define the target subnet.  
- Security Group ID: Provide the security group(s).  
- Key Pair: Specify the key pair for SSH access.  
- Number of Instances: Define the required number of instances.  

Verify the instance launch by describing the instance status:  

```
aws ec2 describe-instances --instance-ids <instance-id>
```

---

### Task 2: Automate Web Server Setup Using User Data and S3  
**Objective:**  
Set up an EC2 instance as a web server, download web content (index.html and status.html) from S3, and serve it using Apache.

**Instructions:**  

1. **Create the S3 Bucket:**  
- Upload `index.html` and `status.html` to the bucket.  

2. **Launch EC2 Instance with User Data:**  
- Use the following User Data script while launching the instance:  

```
#!/bin/bash
yum install httpd -y
service httpd start
chkconfig httpd on
aws s3 cp s3://<bucket-name>/index.html /var/www/html/index.html
aws s3 cp s3://<bucket-name>/status.html /var/www/html/status.html
```

3. **Verify the Setup:**  
- Access the public IP or domain of the instance to check if the web server is running and serving the files.  

---

### Task 3: Create IAM Users and Test AWS CLI Profiles  
**Objective:**  
Create two IAM users with specific permissions and test their access using the AWS CLI.  

**Instructions:**  

1. **Create IAM Users:**  
- User1: Grant AmazonS3FullAccess policy.  
- User2: Grant IAMFullAccess policy.  

2. **Generate Access Keys:**  
- Generate the Access Key and Secret Key for both users.  

3. **Configure CLI Profiles:**  
- Set up CLI profiles on your local machine:
  
```
aws configure --profile user1-profile
aws configure --profile user2-profile
```

4. **Test User Permissions:**  
- User1: Attempt to create an S3 bucket.  
```
aws s3 mb s3://<bucket-name> --profile user1-profile
```
- User2: Attempt to create an IAM user.  
```
aws iam create-user --user-name test-user --profile user2-profile
```
- Verify that each user has the expected permissions and no access beyond what is granted.  

---

### Task 4: Use the aws s3 sync Command for Incremental Updates from S3 to EC2  
**Objective:**  
Test incremental synchronization of web content between an S3 bucket and an EC2 instance using the aws s3 sync command.  

**Instructions:**  

1. **Prepare the S3 Bucket:**  
- Add the initial set of files (e.g., index.html and status.html) to your S3 bucket.  

2. **Launch EC2 and Configure Web Server:**  
- Set up the web server and sync data from the S3 bucket:  
```
aws s3 sync s3://<bucket-name>/ /var/www/html/
```

3. **Test Incremental Updates:**  
- Add a new file (e.g., about.html) or modify an existing file (e.g., index.html) in the S3 bucket.  
- Run the sync command again to pull only updated or new files:  
```
aws s3 sync s3://<bucket-name>/ /var/www/html/
```

4. **Verify Updates:**  
- Access the public IP or domain of the EC2 instance to confirm that the changes are reflected.  

---

### Task 5: Automate S3 to EC2 Synchronization Using a Cron Job  
**Objective:**  
Set up a cron job on an EC2 instance to automate regular synchronization of web content from an S3 bucket to the web server directory.  

**Instructions:**  

1. **Launch and Configure EC2 Instance:**  
- Launch an EC2 instance and install Apache.  
- Verify that the web server is running.  

2. **Perform Initial Synchronization:**  
- Manually run the aws s3 sync command to pull initial content:  
```
aws s3 sync s3://<bucket-name>/ /var/www/html/
```

3. **Install and Enable Cron:**  
- Ensure the cronie package is installed and the service is enabled:  

```
yum install cronie -y
service crond start
chkconfig crond on
```

4. **Create a Cron Job for Regular Synchronization:**  

- Open the crontab editor:  
```
crontab -e
```
- Add the following entry to synchronize every 2 minutes:  
```
*/2 * * * * aws s3 sync s3://<bucket-name>/ /var/www/html/
```

5. **Test the Automation:**  
- Add or update files in the S3 bucket.  
- Wait for the cron job to trigger and verify the changes by accessing the instance’s public IP or domain.  

---

---
# AWS EventBridge Configuration Tasks

## Task-1: Configure EventBridge to Stop an EC2 Instance at a Specific Time (9:15 AM)
- Create an EventBridge rule to trigger an AWS Lambda function or Systems Manager Automation document to stop the EC2 instance.
- Set the schedule expression to `cron(15 9 * * ? *)` to run at 9:15 AM daily.

---

## Task-2: Configure to Stop an EC2 Instance After 5 Minutes and Trigger a Custom Email Notification
- Create an EventBridge rule with a delay of 5 minutes after the event is triggered.
- Use an **Input Transformer** to modify the event data before passing it to the target (SNS for email notification).
- Ensure the SNS topic is configured to send email notifications to the required recipients.

---

## Task-3: Send an SNS Notification When an IAM Policy is Modified
- Create an EventBridge rule to capture IAM policy modification events using the following **Event Pattern**:
```json
{
  "source": ["aws.iam"],
  "detail-type": ["AWS API Call via CloudTrail"],
  "detail": {
    "eventSource": ["iam.amazonaws.com"],
    "eventName": [
      "CreatePolicy",
      "DeletePolicy",
      "UpdatePolicy"
    ]
  }
}
```

- Configure the rule to send a notification using Amazon SNS.
- **Note:** This configuration has not been tested. Please verify and update the status after testing.

---

## Task-4: Get a Notification When Anyone Logs in to the AWS Account
- Create an EventBridge rule to capture AWS account login events using the following **Event Pattern**:
```json
{
  "source": ["aws.signin"],
  "detail-type": ["AWS Console Sign In via CloudTrail"],
  "detail": {
    "eventName": ["ConsoleLogin"],
    "additionalEventData": {
      "MFAUsed": ["Yes", "No"]
    }
  }
}
```
- Configure the rule to send a notification via Amazon SNS.
- **Note:** This configuration has not been tested. Please verify and update the status after testing.

---

#### **Task 1**: **Add load on ec2 instance and test the alarm
1. **Launch a Linux EC2 Instance**:  
   - Select the appropriate AMI and instance type.
   - Install stress package and install htop package
2. **Create Alarm**:  
   - Create an Alarm to "stop" an ec2 instance when the load is more than 70% for 300 seconds. 
   - Also, configure alerts to your email when above alarm triggered.  

#### **Task 1**: **Linux EC2 Instance Setup with Web Server and Custom Configuration**  
1. **Launch a Linux EC2 Instance**:  
   - Select the appropriate AMI and instance type.  
   - Configure security group rules to allow HTTP/HTTPS traffic.  
2. **Web Server Setup**:  
   - Install and configure a web server (e.g., Apache or Nginx).  
   - Add custom webpages and verify their accessibility via the public IP.  
3. **Volume Association**:  
   - Create a 2GB EBS volume.  
   - Attach the volume to the instance.  
   - Format, mount, and configure it for permanent mounting.  
4. **Golden AMI Creation**:  
   - Create an AMI of the configured instance.  
5. **Test Golden AMI**:  
   - Launch a new instance from the created AMI.  
   - Verify the web server and custom configurations are intact.  

---

#### **Task 2**: **Windows EC2 Instance Customization and Testing**  
1. **Launch a Windows EC2 Instance**:  
   - Select the appropriate AMI and instance type.  
   - Configure security group rules to allow RDP traffic.  
2. **Connect to the Instance**:  
   - Retrieve and decrypt the administrator password.  
   - Connect using an RDP client.  
3. **Perform Customizations**:  
   - Change the administrator password.  
   - Change the desktop wallpaper.  
   - Install PuTTY software.  
   - Install IIS and configure a custom webpage.  
4. **Golden AMI Creation**:  
   - Stop the instance and create an AMI.  
5. **Test Golden AMI**:  
   - Launch a new instance from the created AMI.  
   - Verify the customizations are preserved.  

---

#### **Task 3**: **Setup Password Authentication for EC2-User**  
1. Follow the steps in the provided [guide](https://comtechies.com/password-authentication-aws-ec2.html):  
   - Enable password authentication in the SSH configuration file.  
   - Restart the SSH service.  
   - Set a password for the `ec2-user`.  
2. Verify that password authentication works as expected.  

---




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
