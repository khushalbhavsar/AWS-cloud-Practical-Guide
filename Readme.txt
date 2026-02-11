# ☁️ AWS Cloud Practical Guide

A comprehensive, step-by-step guide to AWS services for DevOps engineers and cloud practitioners.

---

## 📑 Table of Contents

- [EC2 Instance](#-steps-to-create-an-ec2-instance)
- [IAM (User / Role)](#-steps-to-create-iam-user--role-in-aws)
- [Elastic Block Store (EBS)](#-steps-to-create-elastic-block-store-ebs)
- [AMI (Amazon Machine Image)](#️-steps-to-create-ami-amazon-machine-image)
- [Load Balancer & Auto Scaling](#️-steps-to-create-load-balancer--auto-scaling-in-aws)
- [S3 Bucket](#-steps-to-create-amazon-s3-bucket)
- [RDS (Relational Database)](#️-steps-to-create-amazon-rds)
- [CloudFormation](#️-steps-to-create-aws-cloudformation-stack)
- [Lambda](#-steps-to-create-aws-lambda-function)
- [Route 53](#-steps-to-create-amazon-route-53-dns)
- [CloudFront](#-steps-to-create-amazon-cloudfront-cdn)
- [VPC](#-steps-to-create-aws-vpc)
- [Amplify](#-steps-to-create-aws-amplify-app)
- [ECS](#-steps-to-create-amazon-ecs-container-service)
- [CloudWatch Monitoring](#-steps-to-create-aws-monitoring-cloudwatch)

---

## 🚀 Steps to Create an EC2 Instance

### 1️⃣ Login to AWS Console

- Go to **AWS Console**
- Sign in to your **Amazon Web Services** account

---

### 2️⃣ Open EC2 Service

- Search **EC2** in the search bar
- Click **EC2 → Instances**
- Click **Launch instance**

---

### 3️⃣ Name Your Instance

- Example: `My-First-EC2`
- This helps you identify the server later

---

### 4️⃣ Choose an AMI (Operating System)

Common options:

- **Amazon Linux 2023** ✅ (recommended for beginners)
- Ubuntu 20.04 / 22.04
- Red Hat / Windows

👉 Select **Amazon Linux** → Click **Select**

---

### 5️⃣ Choose Instance Type

- **t2.micro** or **t3.micro**
  - Free Tier eligible
  - 1 vCPU, 1 GB RAM

👉 Click **Next**

---

### 6️⃣ Create or Select Key Pair (VERY IMPORTANT 🔐)

- Key pair is used to **SSH into EC2**
- Click **Create new key pair**
  - Name: `ec2-key`
  - Type: RSA
  - Format: `.pem`
- Download & **store safely**

⚠️ Without this key, you **cannot log in**

---

### 7️⃣ Configure Network Settings (Security Group)

- Allow required traffic:
  - ✅ SSH → Port 22 → Source: My IP
  - ✅ HTTP → Port 80 → Anywhere (if web server)
  - ✅ HTTPS → Port 443 → Anywhere

Example:

```
SSH     TCP     22      My IP
HTTP    TCP     80      0.0.0.0/0
```

---

### 8️⃣ Configure Storage

- Default: **8 GB gp3** (enough for practice)
- You can increase later

---

### 9️⃣ Review & Launch

- Review all settings
- Click **Launch instance**

🎉 Your EC2 instance is created!

---

### 🔟 Check Instance Status

- Go to **EC2 → Instances**
- Wait until:
  - **Instance state:** Running
  - **Status check:** 2/2 checks passed

---

## 🔑 Connect to EC2 (Linux)

```bash
chmod 400 ec2-key.pem
ssh -i ec2-key.pem ec2-user@<PUBLIC-IP>
```

---

## 🧠 Important Tips

- ✅ Always stop instances when not in use
- ✅ Never expose SSH to `0.0.0.0/0`
- ✅ Keep your `.pem` file safe
- ✅ Use IAM roles instead of access keys (advanced)

---

## 🔐 Steps to Create IAM (User / Role) in AWS

### 1️⃣ Login to AWS Console

- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

---

### 2️⃣ Open IAM Service

- Search **IAM** in the search bar
- Click **IAM (Identity and Access Management)**

---

## 👤 A. Steps to Create an IAM User

### 3️⃣ Go to Users

- IAM Dashboard → **Users**
- Click **Create user**

---

### 4️⃣ Enter User Details

- **User name**: `devops-user` (example)
- Select access type:
  - ✅ **AWS Management Console access** (UI login)
  - ✅ **Programmatic access** (CLI / SDK)

👉 Set **custom password** or auto-generate

---

### 5️⃣ Attach Permissions

Choose **one** option:

🔹 **Attach policies directly** (most common)

- Examples:
  - `AdministratorAccess` (learning only ⚠️)
  - `AmazonEC2FullAccess`
  - `ReadOnlyAccess`

🔹 **Add user to group** (best practice)

- Example group: `DevOps-Team`

---

### 6️⃣ Review & Create User

* Review details
* Click **Create user**

---

### 7️⃣ Save Credentials (IMPORTANT)

* Download:

  * **Access Key ID**
  * **Secret Access Key**
* Or download `.csv` file

⚠️ Secret key is shown **only once**

---

## 🔁 B. Steps to Create IAM Role (Recommended for EC2)

### 8️⃣ Go to Roles

* IAM → **Roles**
* Click **Create role**

---

### 9️⃣ Select Trusted Entity

* Choose **AWS service**
* Select **EC2**
* Click **Next**

---

### 🔟 Attach Permissions to Role

* Example policies:

  * `AmazonS3FullAccess`
  * `AmazonEC2ReadOnlyAccess`
* Click **Next**

---

### 1️⃣1️⃣ Name & Create Role

* Role name: `EC2-S3-Access-Role`
* Click **Create role**

---

### 1️⃣2️⃣ Attach Role to EC2

* EC2 → Instances
* Select instance
* Actions → Security → Modify IAM role
* Attach the role

✅ No access keys needed (BEST PRACTICE)

---

## 🔐 IAM Best Practices (Interview ⭐)

- ✔ Never use **root account** for daily work
- ✔ Use **IAM roles** instead of access keys
- ✔ Follow **Least Privilege Principle**
- ✔ Enable **MFA**
- ✔ Rotate access keys regularly

---

## 🧠 IAM in One Line (Interview)

> IAM allows you to **securely manage users, roles, permissions, and access to AWS resources**.

---

---

## 💾 Steps to Create Elastic Block Store (EBS)

### 1️⃣ Login to AWS Console

* Open **AWS Management Console**
* Sign in to **Amazon Web Services**

---

### 2️⃣ Open EC2 Service

- Search **EC2**
- Go to **EC2 Dashboard**

---

### 3️⃣ Go to Volumes (EBS)

- In left sidebar → **Elastic Block Store**
- Click **Volumes**
- Click **Create volume**

---

### 4️⃣ Configure EBS Volume

Fill in the following details:

#### 🔹 Volume Type

- **gp3** ✅ (recommended – balanced & cost-effective)
- io1 / io2 (high IOPS – advanced)
- st1 / sc1 (HDD – low cost)

#### 🔹 Size

- Example: **10 GB**

#### 🔹 Availability Zone ⚠️

- Must be **same AZ as EC2**
  - Example: `ap-south-1a`

#### 🔹 Encryption

- Enabled by default (recommended)

---

### 5️⃣ Create Volume

- Click **Create volume**
- Status will be **Available**

---

## 🔗 Attach EBS Volume to EC2

### 6️⃣ Attach Volume

- Select the volume
- Click **Actions → Attach volume**
- Select:
  - Instance ID
  - Device name (e.g. `/dev/xvdf`)
- Click **Attach**

---

### 7️⃣ Connect to EC2 Instance

```bash
ssh -i ec2-key.pem ec2-user@<PUBLIC-IP>
```

---

### 8️⃣ Check New Disk

```bash
lsblk
```

Example output:

```
xvdf   10G
```

---

### 9️⃣ Format the Volume

```bash
sudo mkfs -t ext4 /dev/xvdf
```

---

### 🔟 Mount the Volume

```bash
sudo mkdir /data
sudo mount /dev/xvdf /data
```

Verify:

```bash
df -h
```

---

### 1️⃣1️⃣ Auto-Mount on Reboot (IMPORTANT)

Edit fstab:

```bash
sudo nano /etc/fstab
```

Add:

```
/dev/xvdf  /data  ext4  defaults,nofail  0  2
```

---

## 🧠 EBS Key Points (Interview ⭐)

- ✔ EBS is **persistent block storage**
- ✔ EBS is **AZ-specific**
- ✔ Can be **attached/detached**
- ✔ Supports **snapshots** (backup)
- ✔ Used for **OS disk & data disk**

---

## 🎯 EBS in One Line (Interview)

> Amazon EBS provides **persistent, high-performance block storage** for EC2 instances.

---

## 🖼️ Steps to Create AMI (Amazon Machine Image)

### 1️⃣ Login to AWS Console

- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

---

### 2️⃣ Open EC2 Service

- Search **EC2**
- Go to **EC2 → Instances**

---

### 3️⃣ Select the EC2 Instance

- Choose the **running or stopped** EC2 instance
- This instance may already have:
  - OS updates
  - Applications (Docker, Jenkins, etc.)
  - Configuration

---

### 4️⃣ Create Image (AMI)

- Click **Actions**
- Go to **Image and templates**
- Click **Create image**

---

### 5️⃣ Configure AMI Details

Fill in the details:

#### 🔹 Image Name

- Example: `devops-base-ami-v1`

#### 🔹 Image Description

- Example: `AMI with Docker, Git, Jenkins installed`

#### 🔹 Reboot Behavior

- ✅ **Reboot instance** (recommended – data safe)
- ❌ No reboot (risk of data inconsistency)

#### 🔹 Storage (Optional)

- Modify root volume size if needed

---

### 6️⃣ Create AMI

- Click **Create image**
- AMI creation starts in background

⏳ Status: **Pending → Available**

---

### 7️⃣ Check AMI Status

- Go to **EC2 → AMIs**
- Select **Owned by me**
- Wait until status is **Available**

---

## 🚀 Launch EC2 from AMI

### 8️⃣ Launch Instance Using AMI

- Select the AMI
- Click **Launch instance from AMI**
- Choose:
  - Instance type
  - Key pair
  - Security group

🎉 New EC2 is created with **same configuration**

---

## 🧠 Important AMI Concepts (Interview ⭐)

- ✔ AMI is a **template** for EC2
- ✔ Includes:
  - OS
  - Installed software
  - EBS snapshots
- ✔ AMIs are **region-specific**
- ✔ Can be **copied to other regions**
- ✔ Used for **autoscaling & disaster recovery**

---

## 🎯 AMI in One Line (Interview)

> An AMI is a **pre-configured template** used to launch EC2 instances with the same OS, software, and settings.

---

## ⚖️ Steps to Create Load Balancer & Auto Scaling in AWS

### 🔹 PART A: Create Load Balancer (ALB)

### 1️⃣ Login to AWS Console

- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

---

### 2️⃣ Open EC2 Dashboard

- Search **EC2**
- Go to **EC2 → Load Balancers**
- Click **Create Load Balancer**

---

### 3️⃣ Choose Load Balancer Type

Select:

- ✅ **Application Load Balancer (ALB)** (Used for HTTP/HTTPS traffic)

Click **Create**

---

### 4️⃣ Configure Load Balancer

- **Name**: `web-alb`
- **Scheme**: Internet-facing
- **IP type**: IPv4

---

### 5️⃣ Network Mapping

- Select **VPC**
- Select **at least 2 public subnets** (different AZs)

---

### 6️⃣ Configure Security Group

- Allow:
  - HTTP → Port 80 → Anywhere
  - HTTPS → Port 443 → Anywhere (optional)

---

### 7️⃣ Create Target Group

- Target type: **Instance**
- Protocol: HTTP
- Port: 80
- Health check path: `/`

👉 Click **Create Load Balancer**

---

### 8️⃣ Register Targets

- Select EC2 instances
- Click **Include as pending**
- Click **Register targets**

✅ Load Balancer created

---

### 🔹 PART B: Create Auto Scaling Group (ASG)

### 9️⃣ Create Launch Template

- Go to **EC2 → Launch Templates**
- Click **Create launch template**

Fill:

- **AMI**: Amazon Linux / Custom AMI
- **Instance type**: t2.micro
- **Key pair**
- **Security group** (allow HTTP + SSH)

Save template

---

### 🔟 Create Auto Scaling Group

- Go to **EC2 → Auto Scaling Groups**
- Click **Create Auto Scaling Group**
- Select **Launch Template**

---

### 1️⃣1️⃣ Configure Network

- Select same **VPC**
- Choose **private or public subnets** (multiple AZs)

---

### 1️⃣2️⃣ Attach Load Balancer

- Select:
  - ✅ Attach to existing Load Balancer
  - Choose **Target Group**
- Enable **ELB health checks**

---

### 1️⃣3️⃣ Set Scaling Policy

Example:

- Desired capacity: **2**
- Minimum: **1**
- Maximum: **4**

Scaling policy:

- Scale out if **CPU > 70%**
- Scale in if **CPU < 30%**

---

### 1️⃣4️⃣ Review & Create

- Review configuration
- Click **Create Auto Scaling Group**

🎉 Auto Scaling is live!

---

## 🔍 Verify Setup

- EC2 instances auto-launch
- Load Balancer → **Targets → Healthy**
- Open **ALB DNS name** in browser

---

## 🧠 Key Interview Points ⭐

- ✔ Load Balancer distributes traffic
- ✔ Auto Scaling adjusts instance count
- ✔ Works across **multiple AZs**
- ✔ Improves **availability & scalability**
- ✔ Used in **production architectures**

---

## 🎯 One-Line Interview Answers

**Load Balancer:**

> Distributes incoming traffic across multiple EC2 instances to ensure high availability.

**Auto Scaling:**

> Automatically increases or decreases EC2 instances based on demand.


## 🪣 Steps to Create Amazon S3 Bucket

### 1️⃣ Login to AWS Console

* Open **AWS Management Console**
* Sign in to **Amazon Web Services**

---

### 2️⃣ Open S3 Service

* Search **S3** in the search bar
* Click **S3** → **Create bucket**

---

### 3️⃣ Configure Bucket Details

Fill the basic details:

#### 🔹 Bucket Name

* Must be **globally unique**
* Example: `my-devops-project-bucket-123`

#### 🔹 AWS Region

* Choose region close to you
  Example: `ap-south-1 (Mumbai)`

---

### 4️⃣ Object Ownership

* Select **ACLs disabled (recommended)**
* Object ownership: **Bucket owner enforced**

---

### 5️⃣ Block Public Access (IMPORTANT ⚠️)

* ✅ Keep **Block all public access ON** (recommended)
* If hosting a website → you may disable later carefully

---

### 6️⃣ Bucket Versioning (Optional but Best Practice)

* Enable **Versioning** (recommended)
* Helps recover deleted/overwritten files

---

### 7️⃣ Encryption

* Enable **Server-side encryption**
* Choose:

  * SSE-S3 (default)
  * SSE-KMS (advanced)

---

### 8️⃣ Create Bucket

* Review settings
* Click **Create bucket**

🎉 Your S3 bucket is created!

---

## 📤 Upload Files to S3

### 9️⃣ Upload Object

* Open your bucket
* Click **Upload**
* Add files / folders
* Click **Upload**

---

## 🔐 (Optional) Make Object Public

⚠️ Use only if required (e.g., static website)

* Select object → **Actions → Make public**
* Or configure **Bucket Policy**

---

## 🧠 S3 Key Points (Interview ⭐)

✔ Object storage (not block/file)
✔ Unlimited storage capacity
✔ Highly durable (11 nines – 99.999999999%)
✔ Used for backups, logs, static websites
✔ Global service (but buckets are region-based)

---

## 🎯 S3 in One Line (Interview)

> Amazon S3 is a **highly durable, scalable object storage service** used to store and retrieve any amount of data.


Below are the **clear, step-by-step instructions to create Amazon RDS (Relational Database Service)** — simple, practical, and **interview-ready** 👇

---

## 🗄️ Steps to Create Amazon RDS

### 1️⃣ Login to AWS Console

- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

---

### 2️⃣ Open RDS Service

- Search **RDS**
- Click **RDS → Create database**

---

### 3️⃣ Choose Database Creation Method

- Select **Standard create** (recommended)

---

### 4️⃣ Select Database Engine

Choose one:

- **MySQL** ✅ (beginner-friendly)
- PostgreSQL
- MariaDB
- Oracle
- SQL Server

👉 Example used: **MySQL**

---

### 5️⃣ Choose Template

- **Free Tier** (learning/practice)
- Production (real workloads)
- Dev/Test

👉 Select **Free Tier**

---

### 6️⃣ Configure Database Settings

- **DB instance identifier**: `my-rds-db`
- **Master username**: `admin`
- **Password**: set a strong password

---

### 7️⃣ Instance Configuration

- **DB instance class**: `db.t3.micro` (Free Tier)
- **Storage type**: gp3
- **Allocated storage**: 20 GB (default)

---

### 8️⃣ Connectivity Settings

- **VPC**: Default VPC (or your custom VPC)
- **Public access**:
  - ✅ Yes (learning)
  - ❌ No (production best practice)
- **VPC security group**:
  - Allow inbound **DB port**
    - MySQL → `3306`
    - PostgreSQL → `5432`

---

### 9️⃣ Database Options

- Database name: `mydatabase`
- Backup retention: default
- Monitoring: disable for free tier

---

### 🔟 Create Database

- Review all settings
- Click **Create database**

⏳ Status: **Creating → Available**

---

## 🔗 Connect to RDS

### 1️⃣1️⃣ Get Endpoint

- RDS → Databases → Select DB
- Copy **Endpoint**

---

### 1️⃣2️⃣ Connect from EC2

```bash
mysql -h <endpoint> -u admin -p
```

(Ensure EC2 security group is allowed in RDS SG)

---

## 🧠 RDS Key Points (Interview ⭐)

- ✔ Managed relational database
- ✔ Automated backups & patching
- ✔ Supports Multi-AZ
- ✔ Highly available & scalable
- ✔ No OS-level access

---

## 🎯 RDS in One Line (Interview)

> Amazon RDS is a **fully managed relational database service** that simplifies setup, scaling, and maintenance.

---
## ☁️ Steps to Create AWS CloudFormation Stack

### 1️⃣ Login to AWS Console

- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

---

### 2️⃣ Open CloudFormation Service

- Search **CloudFormation**
- Click **CloudFormation**
- Click **Create stack**

---

### 3️⃣ Choose Stack Creation Method

Select **one** option:

- ✅ **Upload a template file** (YAML/JSON)
- Amazon S3 URL
- Use a sample template

👉 Common choice: **Upload a template file**

---

### 4️⃣ Upload CloudFormation Template

- Click **Choose file**
- Upload `template.yaml` or `template.json`

Example (EC2 sample):

```yaml
Resources:
  MyEC2:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: t2.micro
      ImageId: ami-0abcdef12345
```

Click **Next**

---

### 5️⃣ Specify Stack Details

- **Stack name**: `my-first-stack`
- Fill **parameters** (if any)
- Click **Next**

---

### 6️⃣ Configure Stack Options (Optional)

- Tags (Environment: Dev)
- IAM Role (optional)
- Rollback settings

Click **Next**

---

### 7️⃣ Review & Create Stack

- Review all settings
- Check **I acknowledge IAM resources** (if shown)
- Click **Create stack**

---

### 8️⃣ Monitor Stack Creation

- Status changes:
  - `CREATE_IN_PROGRESS`
  - `CREATE_COMPLETE` ✅
- Check **Events** tab for errors/logs

---

## 🔄 Update CloudFormation Stack

- Modify template
- Click **Update stack**
- Upload updated template
- Review → Update

---

## 🗑️ Delete Stack

- Select stack
- Click **Delete**
- All resources are deleted automatically

---

## 🧠 CloudFormation Key Points (Interview ⭐)

- ✔ Infrastructure as Code (IaC)
- ✔ Declarative (what, not how)
- ✔ Repeatable & version-controlled
- ✔ Automatic rollback on failure
- ✔ Supports YAML & JSON

---

## 🎯 CloudFormation in One Line (Interview)

> AWS CloudFormation lets you **model, provision, and manage AWS infrastructure using code**.

---

## ⚡ Steps to Create AWS Lambda Function

### 1️⃣ Login to AWS Console

- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

---

### 2️⃣ Open Lambda Service

- Search **Lambda**
- Click **AWS Lambda**
- Click **Create function**

---

### 3️⃣ Choose Function Creation Method

Select:

- ✅ **Author from scratch** (recommended for beginners)

---

### 4️⃣ Configure Basic Function Settings

- **Function name**: `my-first-lambda`
- **Runtime**:
  - Python 3.12 / Node.js 18 / Java 17 (choose one)
- **Architecture**: x86_64 (default)

---

### 5️⃣ Create Execution Role (IAM)

- Select **Create a new role with basic Lambda permissions**
- This allows logging to **CloudWatch**

👉 Click **Create function**

---

### 6️⃣ Write Lambda Code

Example (Python):

```python
def lambda_handler(event, context):
    return {
        "statusCode": 200,
        "body": "Hello from AWS Lambda!"
    }
```

Click **Deploy**

---

### 7️⃣ Test Lambda Function

- Click **Test**
- Create a test event:
  - Name: `test-event`
  - Keep default JSON
- Click **Test**

✅ Output should show **StatusCode: 200**

---

## 🔗 (Optional) Add Trigger to Lambda

### 8️⃣ Add Trigger

- Click **Add trigger**
- Choose service:
  - API Gateway (HTTP API)
  - S3 (file upload trigger)
  - EventBridge (cron jobs)
- Configure settings
- Click **Add**

---

## ⚙️ Configure Lambda Settings (Optional)

- **Memory**: 128 MB → 10 GB
- **Timeout**: Default 3 sec (max 15 min)
- **Environment variables**
- **Permissions**

---

## 🧠 Lambda Key Points (Interview ⭐)

- ✔ Serverless (no server management)
- ✔ Auto-scales automatically
- ✔ Pay only for execution time
- ✔ Event-driven
- ✔ Max execution time: 15 minutes

---

## 🎯 Lambda in One Line (Interview)

> AWS Lambda lets you **run code without provisioning or managing servers**, executing only when triggered.

---

## 🌐 Steps to Create Amazon Route 53 (DNS)

### 1️⃣ Login to AWS Console

- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

---

### 2️⃣ Open Route 53 Service

- Search **Route 53**
- Click **Route 53 Dashboard**

---

### 🏷️ PART A: Create Hosted Zone

### 3️⃣ Create Hosted Zone

- Click **Hosted zones**
- Click **Create hosted zone**

Fill details:

- **Domain name**: `example.com`
- **Type**: Public hosted zone
- Comment: optional

Click **Create hosted zone**

---

### 4️⃣ Note Name Servers

- After creation, Route 53 gives **NS records**
- Example:
  ```
  ns-123.awsdns-45.net
  ns-678.awsdns-90.org
  ```

⚠️ These must be added at your domain registrar

---

### 🔁 PART B: Point Domain to AWS (DNS Records)

### 5️⃣ Create Record

- Open your hosted zone
- Click **Create record**

---

### 6️⃣ Choose Record Type

Common records:

| Record | Use                    |
| ------ | ---------------------- |
| A      | Point domain to IP     |
| CNAME  | Alias domain           |
| ALIAS  | AWS resource (ALB, S3) |
| MX     | Email routing          |

Example:

- **Record type**: A
- **Value**: EC2 public IP

OR

- **Alias**: Application Load Balancer

Click **Create record**

---

## 🔗 Example: Connect Domain to ALB (Best Practice)

### 7️⃣ Create Alias Record

- Record name: `www`
- Type: A
- Enable **Alias**
- Choose:
  - Application Load Balancer
  - Select region & ALB

---

## 🧠 Route 53 Key Points (Interview ⭐)

- ✔ Highly available DNS service
- ✔ Supports routing policies
- ✔ Integrates with ALB, S3, CloudFront
- ✔ Health checks & failover
- ✔ Domain registration + DNS

---

## 🎯 Route 53 in One Line (Interview)

> Amazon Route 53 is a **highly available and scalable DNS service** that routes users to AWS resources.

---

## 🌍 Steps to Create Amazon CloudFront (CDN)

### 1️⃣ Login to AWS Console

- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

---

### 2️⃣ Open CloudFront Service

- Search **CloudFront**
- Click **CloudFront**
- Click **Create a CloudFront distribution**

---

### 3️⃣ Choose Origin (Source of Content)

You must choose **where CloudFront will fetch content from**:

#### Common Origins

- **Amazon S3 bucket** (static website / assets) ✅
- **Application Load Balancer**
- **EC2 public IP / domain**
- **Custom origin (API, backend)**

Example:

- **Origin domain**: `mybucket.s3.amazonaws.com`
- **Origin type**: Amazon S3

👉 Click **Use this origin**

---

### 4️⃣ Configure Default Cache Behavior

Important settings:

- **Viewer protocol policy**:
  - Redirect HTTP to HTTPS ✅
- **Allowed HTTP methods**:
  - GET, HEAD (static content)
- **Cache policy**:
  - Managed-CachingOptimized (recommended)

---

### 5️⃣ Security Settings

(Optional but recommended)

- **Enable WAF** (advanced)
- **Enable HTTPS** (default)
- **Use default CloudFront certificate**
  - Or custom domain with ACM (advanced)

---

### 6️⃣ Distribution Settings

- **Price class**:
  - Use all edge locations (best performance)
- **Default root object**:
  - `index.html` (for websites)

---

### 7️⃣ Create Distribution

- Review settings
- Click **Create distribution**

⏳ Status:

- **Deploying** → **Enabled**
- Takes **5–15 minutes**

---

### 8️⃣ Access CloudFront

- Copy **Distribution domain name**
  ```
  d123abcd.cloudfront.net
  ```
- Open in browser 🎉

---

## 🧠 CloudFront Key Points (Interview ⭐)

- ✔ Content Delivery Network (CDN)
- ✔ Caches content at **edge locations**
- ✔ Reduces latency & load on backend
- ✔ Supports S3, ALB, EC2, APIs
- ✔ Improves performance & security

---

## 🎯 CloudFront in One Line (Interview)

> Amazon CloudFront is a **global CDN service** that delivers content with **low latency and high performance** using edge locations.

---
## 🌐 Steps to Create AWS VPC

### 1️⃣ Login to AWS Console

- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

---

### 2️⃣ Open VPC Service

- Search **VPC**
- Click **VPC Dashboard**

---

### 🔹 METHOD 1: Create VPC (Manual – Best for Learning)

### 3️⃣ Create VPC

- Click **Your VPCs**
- Click **Create VPC**

Fill details:

- **Name tag**: `my-vpc`
- **IPv4 CIDR block**: `10.0.0.0/16`
- IPv6: Optional
- Tenancy: Default

👉 Click **Create VPC**

---

### 4️⃣ Create Subnets

Go to **Subnets → Create subnet**

Example:

- **Public Subnet**:
  - Name: `public-subnet`
  - CIDR: `10.0.1.0/24`
  - AZ: ap-south-1a

- **Private Subnet**:
  - Name: `private-subnet`
  - CIDR: `10.0.2.0/24`
  - AZ: ap-south-1b

---

### 5️⃣ Create Internet Gateway (IGW)

- Go to **Internet Gateways**
- Click **Create internet gateway**
- Name: `my-igw`
- Attach to **my-vpc**

---

### 6️⃣ Create Route Tables

#### Public Route Table

- Go to **Route Tables → Create**
- Name: `public-rt`
- Add route:
  ```
  Destination: 0.0.0.0/0
  Target: Internet Gateway
  ```
- Associate **public subnet**

#### Private Route Table

- Create `private-rt`
- Associate **private subnet**
- (Optional) NAT Gateway later

---

### 7️⃣ Enable Auto-Assign Public IP

- Go to **Subnets**
- Select public subnet
- Edit settings
- Enable **Auto-assign public IPv4**

---

### 🔹 METHOD 2: Create VPC (Quick Setup)

### 8️⃣ VPC Wizard (Fast Method)

- VPC Dashboard → **Create VPC**
- Select **VPC and more**

AWS auto-creates:

- VPC
- Public & Private subnets
- Route tables
- IGW
- NAT Gateway (optional)

👉 Click **Create VPC**

---

## 🧠 VPC Key Points (Interview ⭐)

- ✔ VPC is a **virtual network**
- ✔ CIDR defines IP range
- ✔ Public subnet → IGW
- ✔ Private subnet → NAT Gateway
- ✔ Security via **Security Groups + NACLs**

---

## 🎯 VPC in One Line (Interview)

> Amazon VPC allows you to **launch AWS resources in an isolated virtual network**.

---

## 🔥 Real DevOps Architecture

```
VPC
├── Public Subnet → ALB, Bastion
├── Private Subnet → EC2, RDS
├── IGW → Internet access
└── NAT → Outbound internet for private subnet
```

---
## 🚀 Steps to Create AWS Amplify App

### 1️⃣ Login to AWS Console

- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

---

### 2️⃣ Open AWS Amplify

- Search **Amplify**
- Click **AWS Amplify**
- Click **Get started** (or **Create new app**)

---

### 🔹 PART A: Deploy Frontend App (Most Common)

### 3️⃣ Choose App Type

- Select **Host web app**
- Click **Next**

---

### 4️⃣ Connect Source Code Repository

Choose repository provider:

- GitHub ✅ (most common)
- GitLab
- Bitbucket
- AWS CodeCommit

👉 Authorize Amplify to access your repo

---

### 5️⃣ Select Repository & Branch

- Choose **repository**
- Select **branch** (e.g., `main`)
- Click **Next**

---

### 6️⃣ Configure Build Settings

Amplify auto-detects framework:

- React
- Next.js
- Angular
- Vue
- Static HTML/CSS/JS

Example `amplify.yml` (auto-created):

```yaml
frontend:
  phases:
    build:
      commands:
        - npm install
        - npm run build
  artifacts:
    baseDirectory: build
    files:
      - '**/*'
```

👉 Click **Next**

---

### 7️⃣ Review & Deploy

- Review settings
- Click **Save and deploy**

⏳ Status:

- Provisioning
- Build
- Deploy
- **Live** ✅

---

### 8️⃣ Access Your App

- Amplify provides a default URL:

```
https://main.d123abc.amplifyapp.com
```

🎉 Your app is live!

---

## 🔐 (Optional) Add Backend with Amplify

You can add:

- Authentication (Cognito)
- API (REST / GraphQL)
- Storage (S3)
- Functions (Lambda)

From Amplify console:

- **Backend environments → Create backend**

---

## 🧠 Amplify Key Points (Interview ⭐)

- ✔ Fully managed frontend hosting
- ✔ CI/CD built-in
- ✔ Supports modern frameworks
- ✔ Easy backend integration
- ✔ Scales automatically

---

## 🎯 Amplify in One Line (Interview)

> AWS Amplify is a **fully managed platform to build, deploy, and host scalable web and mobile applications**.

---

## 🔥 Real DevOps / Cloud Use Cases

- React / Next.js hosting
- Frontend CI/CD pipelines
- Serverless full-stack apps
- Startup MVP deployment

---

## 📌 Typical Architecture

```
GitHub → AWS Amplify → CloudFront → Users
                     → (Optional Backend: Lambda, API, Cognito)
```

---

## 🐳 Steps to Create Amazon ECS (Container Service)

### 1️⃣ Login to AWS Console

- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

---

### 2️⃣ Open ECS Service

- Search **ECS**
- Click **Elastic Container Service**
- Click **Create cluster**

---

### 🔹 PART A: Create ECS Cluster

### 3️⃣ Choose Cluster Type

Select:

- ✅ **AWS Fargate** (serverless – recommended)
- EC2 instances (self-managed – advanced)

👉 Choose **AWS Fargate** → Next

---

### 4️⃣ Configure Cluster

- **Cluster name**: `my-ecs-cluster`
- Infrastructure: AWS Fargate
- Networking: Default VPC (or custom)

Click **Create**

✅ Cluster created

---

### 🔹 PART B: Create Task Definition

### 5️⃣ Create Task Definition

- ECS → **Task Definitions**
- Click **Create new task definition**
- Choose **AWS Fargate**

---

### 6️⃣ Configure Task Definition

- **Task definition name**: `my-app-task`
- **Task role**: None (or IAM role if needed)
- **Operating system**: Linux
- **CPU**: 0.5 vCPU
- **Memory**: 1 GB

---

### 7️⃣ Add Container

- **Container name**: `my-container`
- **Image**:
  ```
  nginx:latest
  ```
- **Port mappings**:
  - Container port: 80
- Click **Add**

👉 Click **Create**

---

### 🔹 PART C: Create ECS Service

### 8️⃣ Create Service

- Go to **Clusters → my-ecs-cluster**
- Click **Create service**

---

### 9️⃣ Service Configuration

- Launch type: **Fargate**
- Task definition: `my-app-task`
- Service name: `my-ecs-service`
- Desired tasks: 1

---

### 🔟 Networking Configuration

- VPC: Default
- Subnets: Select **public subnets**
- Security group:
  - Allow **HTTP (80)**
- Enable **Auto-assign public IP**

---

### 1️⃣1️⃣ (Optional) Load Balancer

- Choose **Application Load Balancer**
- Create new target group
- Listener: HTTP 80

---

### 1️⃣2️⃣ Create Service

- Review
- Click **Create service**

🎉 ECS service is running!

---

## 🔍 Verify ECS Deployment

- ECS → Cluster → Services
- Task status: **RUNNING**
- Open:

```
http://<Public-IP>
```

(or ALB DNS)

---

## 🧠 ECS Key Points (Interview ⭐)

- ✔ Container orchestration service
- ✔ Supports Docker containers
- ✔ Fargate = serverless containers
- ✔ Integrates with ALB, IAM, CloudWatch
- ✔ Used for microservices

---

## 🎯 ECS in One Line (Interview)

> Amazon ECS is a **fully managed container orchestration service** for running Docker containers at scale.

---

## 🔥 Real DevOps Use Cases

- Microservices deployment
- CI/CD container pipelines
- Blue-Green deployments
- Backend APIs & workers

---

## 📌 ECS Architecture (Simple)

```
Docker Image → ECS Task → ECS Service → ALB → Users
```

---
## 📊 Steps to Create AWS Monitoring (CloudWatch)

### 1️⃣ Login to AWS Console

- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

---

### 2️⃣ Open CloudWatch Service

- Search **CloudWatch**
- Click **CloudWatch Dashboard**

---

### 🔹 PART A: Monitor Resources (Metrics)

### 3️⃣ View CloudWatch Metrics

- CloudWatch → **Metrics**
- Choose service:
  - EC2
  - RDS
  - Lambda
  - ECS
  - ALB

Example:

- EC2 → **Per-Instance Metrics**
- Select **CPUUtilization**

📈 Metrics are enabled by default

---

### 🔹 PART B: Create CloudWatch Alarm (Very Important)

### 4️⃣ Create Alarm

- CloudWatch → **Alarms**
- Click **Create alarm**

---

### 5️⃣ Select Metric

Example:

- EC2 → Per-Instance → **CPUUtilization**
- Click **Select metric**

---

### 6️⃣ Configure Alarm Condition

Example:

- Threshold type: Static
- Condition:
  ```
  CPUUtilization > 70%
  ```
- Duration: 5 minutes

---

### 7️⃣ Configure Notification (SNS)

- Create new SNS topic:
  - Name: `cpu-alerts`
  - Email: your email
- Confirm email subscription

---

### 8️⃣ Create Alarm

- Review
- Click **Create alarm**

🚨 Alert triggers when threshold is crossed

---

### 🔹 PART C: Enable Log Monitoring (Logs)

### 9️⃣ Create Log Group

- CloudWatch → **Logs → Log groups**
- Click **Create log group**
- Name: `/ec2/application-logs`

---

### 🔟 Send Logs to CloudWatch

For EC2:

- Install **CloudWatch Agent**

```bash
sudo yum install amazon-cloudwatch-agent -y
```

- Start agent and configure logs

For Lambda:

- Logs are **automatic**

---

### 🔹 PART D: Create CloudWatch Dashboard

### 1️⃣1️⃣ Create Dashboard

- CloudWatch → **Dashboards**
- Click **Create dashboard**
- Name: `my-monitoring-dashboard`

---

### 1️⃣2️⃣ Add Widgets

- Line graph
- Number
- Text

Examples:

- EC2 CPU usage
- RDS connections
- Lambda invocations

📊 Single view for all monitoring

---

## 🧠 AWS Monitoring Key Points (Interview ⭐)

- ✔ CloudWatch is AWS native monitoring
- ✔ Metrics, Logs, Alarms, Dashboards
- ✔ Integrated with all AWS services
- ✔ SNS for alerting
- ✔ Near real-time visibility

---

## 🎯 AWS Monitoring in One Line (Interview)

> AWS monitoring uses **CloudWatch to collect metrics, logs, and events for observing and alerting on cloud resources**.

---

## 🔥 Real DevOps Use Cases

- CPU / Memory alerts
- Application log analysis
- Auto Scaling triggers
- Cost optimization
- Incident monitoring

---

## 📌 Typical Monitoring Architecture

```
AWS Resource → CloudWatch Metrics / Logs
           → CloudWatch Alarm
           → SNS (Email / SMS)
```