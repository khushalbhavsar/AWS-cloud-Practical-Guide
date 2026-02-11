# ☁️ AWS Cloud Practical Guide

A comprehensive, step-by-step guide to AWS services for DevOps engineers and cloud practitioners.

---

## 📑 Table of Contents

1. [EC2 (Elastic Compute Cloud)](#-aws-ec2-elastic-compute-cloud)
2. [IAM (Identity and Access Management)](#-aws-iam-identity-and-access-management)
3. [VPC (Virtual Private Cloud)](#-aws-vpc-virtual-private-cloud)
4. [EBS (Elastic Block Store)](#-aws-ebs-elastic-block-store)
5. [S3 (Simple Storage Service)](#-aws-s3-simple-storage-service)
6. [RDS (Relational Database Service)](#-aws-rds-relational-database-service)
7. [DynamoDB](#-aws-dynamodb)
8. [Lambda](#-aws-lambda)
9. [ALB & Auto Scaling](#-aws-alb-application-load-balancer--auto-scaling)
10. [Route 53](#-aws-route-53)
11. [CloudFront](#-aws-cloudfront)
12. [CloudFormation](#-aws-cloudformation)
13. [CloudWatch (Monitoring)](#-aws-monitoring-amazon-cloudwatch)
14. [EKS & ECR (Containers)](#-aws-eks-elastic-kubernetes-service--ecr)
15. [ECS (Elastic Container Service)](#-aws-ecs-elastic-container-service)
16. [Amplify](#-aws-amplify)
17. [AMI (Amazon Machine Image)](#-aws-ami-amazon-machine-image)

---

# 🖥️ AWS EC2 (Elastic Compute Cloud)

## 📚 Theory & Concepts

### ✅ 1. Definition (VERY IMPORTANT – Memorize)
1️⃣ Amazon EC2 is a web service that provides resizable virtual servers in the cloud to run applications.
2️⃣ It eliminates the need for physical hardware.
3️⃣ It is part of Infrastructure as a Service (IaaS).
👉 Write this in exams for full marks.

### ✅ 2. Key Features of EC2
1️⃣ Scalable → Increase or decrease servers anytime.
2️⃣ Pay-as-you-go → Pay only for what you use.
3️⃣ Highly available → Runs across multiple Availability Zones.
4️⃣ Secure → Uses Security Groups and Key Pairs.
5️⃣ Fast deployment → Launch server in minutes.

### ✅ 3. What is an EC2 Instance?
1️⃣ A virtual machine in AWS.
2️⃣ Can run Linux or Windows.
3️⃣ Used to host:
- Websites
- APIs
- Databases
- Backend systems

👉 One AMI → Launch multiple instances.

### ✅ 4. AMI (Amazon Machine Image)
1️⃣ A pre-configured template used to launch EC2.
2️⃣ Contains:
- Operating System
- Software
- Configuration

🚨 Exam Trap:
👉 Cannot launch EC2 without AMI.

### ✅ 5. EC2 Pricing Models (HIGH PROBABILITY QUESTION)
| Model | Description |
|-------|-------------|
| On-Demand | No commitment, Pay per hour/second |
| Reserved Instances | Long-term usage, Cheaper |
| Spot Instances | Cheapest, AWS can terminate anytime |
| Dedicated Hosts | Physical server for one customer |

⭐ Most asked: 👉 Cheapest → Spot Instances

### ✅ 6. Storage in EC2
| Storage Type | Description |
|--------------|-------------|
| EBS (Elastic Block Store) | Persistent storage, Data remains after stopping |
| Instance Store | Temporary storage, Data lost if instance stops |

⭐ VERY COMMON QUESTION.

### ✅ 7. Security in EC2
👉 Security Group
1️⃣ Acts as a firewall.
2️⃣ Controls inbound & outbound traffic.
3️⃣ Allows rules only — NO deny.
4️⃣ Stateful (return traffic allowed automatically).

🚨 Professors LOVE this question.

### ✅ 8. Key Pair
1️⃣ Used for secure login via SSH.
2️⃣ Includes:
- Public key (AWS stores)
- Private key (You keep)

⚠️ Lose private key → Cannot access server.

### ✅ 9. Elastic IP
1️⃣ Static public IP address.
2️⃣ Does NOT change after restart.
3️⃣ Useful for production servers.

### ✅ 10. Stop vs Terminate (VERY FREQUENT)
| Action | Description |
|--------|-------------|
| Stop | Instance can restart, Data remains |
| Terminate | Instance deleted permanently, Data lost |

### ✅ 11. Auto Scaling
1️⃣ Automatically adds/removes instances based on traffic.
2️⃣ Prevents server overload.
3️⃣ Improves availability.
4️⃣ Saves cost.
👉 Preferred scaling → Horizontal scaling (add servers).

### ✅ 12. Load Balancer
1️⃣ Distributes traffic across multiple servers.
2️⃣ Prevents crashes.
3️⃣ Improves performance.

⭐ Architecture professors LOVE:
👉 User → Load Balancer → EC2

### ✅ 13. Regions and Availability Zones
1️⃣ Region → Geographic location (Example: Mumbai).
2️⃣ Availability Zone → Isolated data center inside region.
👉 Using multiple AZ = High availability.

### ✅ 14. Placement Groups
| Type | Use Case |
|------|----------|
| Cluster | Low latency |
| Spread | Fault tolerance |
| Partition | Big data workloads |

⭐ Lowest latency → Cluster

### ✅ 15. User Data
1️⃣ Script that runs automatically when instance launches.
2️⃣ Used to:
- Install software
- Update packages

👉 Saves manual work.

---

## 🔧 Practical Steps: Create an EC2 Instance

### 1️⃣ Login to AWS Console
- Go to **AWS Console**
- Sign in to your **Amazon Web Services** account

### 2️⃣ Open EC2 Service
- Search **EC2** in the search bar
- Click **EC2 → Instances**
- Click **Launch instance**

### 3️⃣ Name Your Instance
- Example: `My-First-EC2`
- This helps you identify the server later

### 4️⃣ Choose an AMI (Operating System)
Common options:
- **Amazon Linux 2023** ✅ (recommended for beginners)
- Ubuntu 20.04 / 22.04
- Red Hat / Windows

👉 Select **Amazon Linux** → Click **Select**

### 5️⃣ Choose Instance Type
- **t2.micro** or **t3.micro**
  - Free Tier eligible
  - 1 vCPU, 1 GB RAM

👉 Click **Next**

### 6️⃣ Create or Select Key Pair (VERY IMPORTANT 🔐)
- Key pair is used to **SSH into EC2**
- Click **Create new key pair**
  - Name: `ec2-key`
  - Type: RSA
  - Format: `.pem`
- Download & **store safely**

⚠️ Without this key, you **cannot log in**

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

### 8️⃣ Configure Storage
- Default: **8 GB gp3** (enough for practice)
- You can increase later

### 9️⃣ Review & Launch
- Review all settings
- Click **Launch instance**

🎉 Your EC2 instance is created!

### 🔟 Check Instance Status
- Go to **EC2 → Instances**
- Wait until:
  - **Instance state:** Running
  - **Status check:** 2/2 checks passed

### 🔑 Connect to EC2 (Linux)
```bash
chmod 400 ec2-key.pem
ssh -i ec2-key.pem ec2-user@<PUBLIC-IP>
```

### 🧠 Important Tips
- ✅ Always stop instances when not in use
- ✅ Never expose SSH to `0.0.0.0/0`
- ✅ Keep your `.pem` file safe
- ✅ Use IAM roles instead of access keys (advanced)

---

# 🔐 AWS IAM (Identity and Access Management)

## 📚 Theory & Concepts

### ✅ 1. Definition (MEMORIZE THIS)
1️⃣ AWS IAM is a service that securely controls access to AWS resources by managing users, permissions, and roles.
2️⃣ It helps decide:
- Who can access AWS
- What they can access
- How they can access

👉 Write this in exams → Direct marks.

### ✅ 2. Key Features of IAM
1️⃣ Centralized access control.
2️⃣ Enhanced security.
3️⃣ Supports Multi-Factor Authentication (MFA).
4️⃣ Fine-grained permissions.
5️⃣ Works across all AWS services.

⭐ Important:
👉 IAM is a GLOBAL service (Not region-based).
VERY COMMON MCQ.

### ✅ 3. Core Components of IAM (VERY HIGH PROBABILITY)

#### ⭐ 1. IAM User
1️⃣ Represents a single person or application.
2️⃣ Has login credentials:
- Password (Console)
- Access Keys (CLI/API)

👉 Example: Developer account.

#### ⭐ 2. IAM Group
1️⃣ Collection of users.
2️⃣ Permissions applied to groups → automatically apply to users.
👉 Example: Developers group → gets S3 access.
⭐ Saves management effort.

#### ⭐ 3. IAM Role (EXTREMELY IMPORTANT)
1️⃣ Temporary permissions.
2️⃣ No password or access keys.
3️⃣ Assumed by:
- AWS services (EC2, Lambda)
- External users

👉 Example: EC2 accessing S3.
🚨 Professors LOVE role-based questions.

#### ⭐ 4. IAM Policy
1️⃣ Document that defines permissions.
2️⃣ Written in JSON format.
3️⃣ Specifies:
- Allow
- Deny
- Resources
- Actions

👉 Without policy → No permissions.

### ✅ 4. Types of Policies
| Type | Description |
|------|-------------|
| Managed Policies | Created by AWS or user, Reusable |
| Inline Policies | Attached to one user/group, Not reusable |

⭐ Exam Favorite.

### ✅ 5. Principle of Least Privilege (VERY VERY IMPORTANT)
1️⃣ Give ONLY the permissions required.
2️⃣ Avoid full admin access.
3️⃣ Reduces security risk.
👉 Write this in descriptive answers — examiners LOVE it.

### ✅ 6. Multi-Factor Authentication (MFA)
1️⃣ Adds extra security layer.
2️⃣ Requires: Password + OTP/device code.
👉 Must enable for root user.
HIGH probability question.

### ✅ 7. Root User (VERY FREQUENT)
1️⃣ Created when AWS account is opened.
2️⃣ Has FULL access.

⚠️ Best Practices:
- Do NOT use daily.
- Enable MFA.
- Create IAM users instead.

### ✅ 8. Authentication vs Authorization
| Concept | Description |
|---------|-------------|
| Authentication | Verifies identity (Username + Password) |
| Authorization | Determines permissions (Can user access S3?) |

⭐ VERY COMMON THEORY QUESTION.

### ✅ 9. Access Keys
1️⃣ Used for programmatic access.
2️⃣ Includes:
- Access Key ID
- Secret Access Key

⚠️ Never share secret keys.

### ✅ 10. Explicit Deny Rule (EXAM TRAP)
👉 Deny ALWAYS overrides Allow.
Remember this line.
Guaranteed MCQ potential.

### ✅ 11. IAM Roles vs Users (SUPER COMMON)
| IAM User | IAM Role |
|----------|----------|
| Permanent | Temporary |
| Has password | No password |
| For people | For services |

👉 Expect this question.

### ✅ 12. Security Best Practices
1️⃣ Enable MFA.
2️⃣ Avoid root usage.
3️⃣ Rotate access keys regularly.
4️⃣ Use roles instead of sharing keys.
5️⃣ Apply least privilege.

Write ANY 4 → Full marks.

### ✅ 13. IAM is Free
👉 No extra charge.
⭐ Often asked in MCQs.

### ✅ 14. Federation (Advanced but Scoring)
1️⃣ Allows login using external providers.
Example: Google, Facebook, Corporate login
👉 No need to create IAM users.

### ✅ 15. Temporary Credentials
Provided via:
👉 STS (Security Token Service)
Used for: Roles, Short-term access

---

## 🔧 Practical Steps: Create IAM User / Role

### 1️⃣ Login to AWS Console
- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

### 2️⃣ Open IAM Service
- Search **IAM** in the search bar
- Click **IAM (Identity and Access Management)**

### 👤 A. Steps to Create an IAM User

### 3️⃣ Go to Users
- IAM Dashboard → **Users**
- Click **Create user**

### 4️⃣ Enter User Details
- **User name**: `devops-user` (example)
- Select access type:
  - ✅ **AWS Management Console access** (UI login)
  - ✅ **Programmatic access** (CLI / SDK)

👉 Set **custom password** or auto-generate

### 5️⃣ Attach Permissions
Choose **one** option:

🔹 **Attach policies directly** (most common)
- Examples:
  - `AdministratorAccess` (learning only ⚠️)
  - `AmazonEC2FullAccess`
  - `ReadOnlyAccess`

🔹 **Add user to group** (best practice)
- Example group: `DevOps-Team`

### 6️⃣ Review & Create User
- Review details
- Click **Create user**

### 7️⃣ Save Credentials (IMPORTANT)
- Download:
  - **Access Key ID**
  - **Secret Access Key**
- Or download `.csv` file

⚠️ Secret key is shown **only once**

### 🔁 B. Steps to Create IAM Role (Recommended for EC2)

### 8️⃣ Go to Roles
- IAM → **Roles**
- Click **Create role**

### 9️⃣ Select Trusted Entity
- Choose **AWS service**
- Select **EC2**
- Click **Next**

### 🔟 Attach Permissions to Role
- Example policies:
  - `AmazonS3FullAccess`
  - `AmazonEC2ReadOnlyAccess`
- Click **Next**

### 1️⃣1️⃣ Name & Create Role
- Role name: `EC2-S3-Access-Role`
- Click **Create role**

### 1️⃣2️⃣ Attach Role to EC2
- EC2 → Instances
- Select instance
- Actions → Security → Modify IAM role
- Attach the role

✅ No access keys needed (BEST PRACTICE)

### 🔐 IAM Best Practices (Interview ⭐)
- ✔ Never use **root account** for daily work
- ✔ Use **IAM roles** instead of access keys
- ✔ Follow **Least Privilege Principle**
- ✔ Enable **MFA**
- ✔ Rotate access keys regularly

### 🧠 IAM in One Line (Interview)
> IAM allows you to **securely manage users, roles, permissions, and access to AWS resources**.

---

# 🌐 AWS VPC (Virtual Private Cloud)

## 📚 Theory & Concepts

### ✅ 1. Definition (VERY IMPORTANT – Memorize)
1️⃣ Amazon VPC is a logically isolated virtual network in AWS where you can launch resources securely.
2️⃣ It gives full control over:
- IP addresses
- Subnets
- Routing
- Security

👉 Write this definition → Easy marks.

### ✅ 2. Why VPC is Used?
1️⃣ Provides network isolation.
2️⃣ Improves security.
3️⃣ Allows custom network configuration.
4️⃣ Supports public and private resources.
5️⃣ Enables hybrid cloud (connect on-premise to AWS).

### ✅ 3. Key Components of VPC (VERY HIGH PROBABILITY)

#### ⭐ 1. CIDR Block
1️⃣ Defines IP address range of VPC.
Example: 10.0.0.0/16
👉 Without CIDR → Cannot create VPC.

#### ⭐ 2. Subnets
1️⃣ Subdivision of a VPC.
2️⃣ Each subnet exists in ONE Availability Zone only.

🚨 Exam Trap:
👉 Subnets cannot span multiple AZs.

### ✅ 4. Types of Subnets
| Type | Description |
|------|-------------|
| Public Subnet | Has route to Internet Gateway, Used for Web servers, Load balancers |
| Private Subnet | No direct internet access, More secure, Used for Databases, Internal apps |

⭐ VERY FREQUENT QUESTION.

### ✅ 5. Internet Gateway (IGW)
1️⃣ Allows communication between VPC and the internet.
2️⃣ Attached to VPC.
3️⃣ Only ONE IGW per VPC.
👉 Needed for public subnet.

### ✅ 6. NAT Gateway
1️⃣ Allows private subnet instances to access the internet.
2️⃣ Prevents inbound internet traffic.
3️⃣ Must be placed in a public subnet.
⭐ Professors LOVE this.

### ✅ 7. Route Table
1️⃣ Contains rules that control network traffic.
2️⃣ Every subnet must be associated with a route table.
👉 Example rule:
`0.0.0.0/0 → Internet Gateway` (means allow internet traffic)

### ✅ 8. Security in VPC (VERY IMPORTANT)

#### ⭐ Security Group
1️⃣ Firewall at instance level.
2️⃣ Stateful → Return traffic allowed automatically.
3️⃣ Supports allow rules only.

#### ⭐ Network ACL (NACL)
1️⃣ Firewall at subnet level.
2️⃣ Stateless → Must define inbound & outbound rules.
3️⃣ Supports allow AND deny.

### ✅ Security Group vs NACL (SUPER COMMON QUESTION)
| Security Group | NACL |
|----------------|------|
| Instance level | Subnet level |
| Stateful | Stateless |
| Allow only | Allow + Deny |

👉 Expect this in exams.

### ✅ 9. Public vs Private Architecture (Understand This Flow)
👉 User → Internet Gateway → Public Subnet → Private Subnet (Database)
⭐ This is my favorite scenario question.

### ✅ 10. VPC Peering
1️⃣ Connect two VPCs privately.
2️⃣ Traffic does NOT go through the internet.

🚨 Exam Trap:
👉 No transitive routing.
(A → B and B → C does NOT mean A → C)

### ✅ 11. NAT vs Internet Gateway
| Internet Gateway | NAT Gateway |
|------------------|-------------|
| Public access | Private outbound only |
| Bidirectional | Outbound only |

### ✅ 12. Availability & Reliability
1️⃣ VPC spans multiple Availability Zones.
2️⃣ Improves fault tolerance.
3️⃣ Supports high availability architecture.

### ✅ 13. Bastion Host
1️⃣ Special EC2 instance in public subnet.
2️⃣ Used to securely SSH into private instances.
👉 Acts as a gateway.

### ✅ 14. VPC Endpoints
1️⃣ Connect privately to AWS services.
2️⃣ No internet required.
Example: 👉 Access S3 from private subnet.
⭐ Increasingly asked in exams.

### ✅ 15. VPC Flow Logs
1️⃣ Capture network traffic information.
2️⃣ Helps in:
- Monitoring
- Troubleshooting
- Security analysis

Stored in: 👉 CloudWatch or S3.

---

## 🔧 Practical Steps: Create AWS VPC

### 1️⃣ Login to AWS Console
- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

### 2️⃣ Open VPC Service
- Search **VPC**
- Click **VPC Dashboard**

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

### 5️⃣ Create Internet Gateway (IGW)
- Go to **Internet Gateways**
- Click **Create internet gateway**
- Name: `my-igw`
- Attach to **my-vpc**

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

### 7️⃣ Enable Auto-Assign Public IP
- Go to **Subnets**
- Select public subnet
- Edit settings
- Enable **Auto-assign public IPv4**

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

### 🧠 VPC Key Points (Interview ⭐)
- ✔ VPC is a **virtual network**
- ✔ CIDR defines IP range
- ✔ Public subnet → IGW
- ✔ Private subnet → NAT Gateway
- ✔ Security via **Security Groups + NACLs**

### 🎯 VPC in One Line (Interview)
> Amazon VPC allows you to **launch AWS resources in an isolated virtual network**.

### 🔥 Real DevOps Architecture
```
VPC
├── Public Subnet → ALB, Bastion
├── Private Subnet → EC2, RDS
├── IGW → Internet access
└── NAT → Outbound internet for private subnet
```

---

# 💾 AWS EBS (Elastic Block Store)

## 📚 Theory & Concepts

### ✅ 1. Definition (MEMORIZE THIS)
1️⃣ Amazon EBS is a persistent block storage service used with EC2 instances to store data permanently.
2️⃣ Works like a virtual hard disk for servers.
👉 Write this → Direct marks.

### ✅ 2. What Type of Storage is EBS?
👉 Block Storage
Means:
1️⃣ Data stored in blocks.
2️⃣ Similar to a traditional hard drive.
3️⃣ Can be mounted to EC2.

🚨 Exam Trap:
❌ EBS is object storage
✅ EBS is block storage
(S3 = Object storage)

### ✅ 3. Key Features of EBS
1️⃣ Persistent storage → Data remains after instance stops.
2️⃣ High performance.
3️⃣ Scalable storage.
4️⃣ Secure encryption support.
5️⃣ Automatic backups via snapshots.

### ✅ 4. Why Use EBS?
1️⃣ Store operating system files.
2️⃣ Store databases.
3️⃣ Keep application data.
4️⃣ Suitable for workloads needing frequent updates.
⭐ Very common theory question.

### ✅ 5. EBS Volume
1️⃣ A storage unit attached to an EC2 instance.
2️⃣ Can be detached and reattached to another instance.
👉 Think: External hard drive.

### ✅ 6. EBS Snapshot (VERY IMPORTANT)
1️⃣ Backup of an EBS volume.
2️⃣ Stored automatically in Amazon S3 (internally).
3️⃣ Used for disaster recovery.
⭐ Professors LOVE snapshot questions.

### ✅ 7. Types of EBS Volumes (Know Basic Idea)

#### ⭐ SSD (Solid State Drive)
Used for high performance.
Types:
1️⃣ General Purpose SSD
2️⃣ Provisioned IOPS SSD

Best for: Databases, Boot volumes

#### ⭐ HDD (Hard Disk Drive)
Used for large data.
Types:
1️⃣ Throughput Optimized HDD
2️⃣ Cold HDD

Best for: Big data, Log storage

👉 Exam tip: SSD → Speed | HDD → Capacity

### ✅ 8. Encryption in EBS
1️⃣ Supports automatic encryption.
2️⃣ Protects sensitive data.
3️⃣ Uses AWS Key Management Service (KMS).

### ✅ 9. EBS is AZ-Specific (VERY IMPORTANT)
👉 Volume is tied to ONE Availability Zone.

🚨 Exam Trap:
❌ EBS is regional
✅ EBS is AZ-based

### ✅ 10. Can One EBS Attach to Multiple EC2?
👉 Normally ❌ No.
(Except special multi-attach volumes — rarely asked.)

### ✅ 11. Root Volume
1️⃣ Default storage attached when EC2 launches.
2️⃣ Usually an EBS volume.
⭐ HIGH probability MCQ.

### ✅ 12. Stop vs Terminate Impact on EBS
| Action | Impact |
|--------|--------|
| Stop Instance | Data remains safe |
| Terminate Instance | Root volume deleted by default |

👉 Important exam point.

### ✅ 13. Scaling EBS
1️⃣ Increase volume size anytime.
2️⃣ Change volume type.
3️⃣ No downtime in most cases.

### ✅ 14. Difference: EBS vs Instance Store (SUPER COMMON)
| EBS | Instance Store |
|-----|----------------|
| Persistent | Temporary |
| Data safe | Data lost on stop |
| Network attached | Physically attached |

⭐ Expect this question.

### ✅ 15. EBS vs S3 (VERY FREQUENT)
| EBS | S3 |
|-----|-----|
| Block storage | Object storage |
| Attached to EC2 | Accessed via internet |
| Fast | Massive storage |
| Limited size | Virtually unlimited |

---

## 🔧 Practical Steps: Create Elastic Block Store (EBS)

### 1️⃣ Login to AWS Console
- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

### 2️⃣ Open EC2 Service
- Search **EC2**
- Go to **EC2 Dashboard**

### 3️⃣ Go to Volumes (EBS)
- In left sidebar → **Elastic Block Store**
- Click **Volumes**
- Click **Create volume**

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

### 5️⃣ Create Volume
- Click **Create volume**
- Status will be **Available**

### 🔗 Attach EBS Volume to EC2

### 6️⃣ Attach Volume
- Select the volume
- Click **Actions → Attach volume**
- Select:
  - Instance ID
  - Device name (e.g. `/dev/xvdf`)
- Click **Attach**

### 7️⃣ Connect to EC2 Instance
```bash
ssh -i ec2-key.pem ec2-user@<PUBLIC-IP>
```

### 8️⃣ Check New Disk
```bash
lsblk
```
Example output:
```
xvdf   10G
```

### 9️⃣ Format the Volume
```bash
sudo mkfs -t ext4 /dev/xvdf
```

### 🔟 Mount the Volume
```bash
sudo mkdir /data
sudo mount /dev/xvdf /data
```
Verify:
```bash
df -h
```

### 1️⃣1️⃣ Auto-Mount on Reboot (IMPORTANT)
Edit fstab:
```bash
sudo nano /etc/fstab
```
Add:
```
/dev/xvdf  /data  ext4  defaults,nofail  0  2
```

### 🧠 EBS Key Points (Interview ⭐)
- ✔ EBS is **persistent block storage**
- ✔ EBS is **AZ-specific**
- ✔ Can be **attached/detached**
- ✔ Supports **snapshots** (backup)
- ✔ Used for **OS disk & data disk**

### 🎯 EBS in One Line (Interview)
> Amazon EBS provides **persistent, high-performance block storage** for EC2 instances.

---

# 🪣 AWS S3 (Simple Storage Service)

## 📚 Theory & Concepts

### ✅ 1. Definition (MEMORIZE THIS)
1️⃣ Amazon S3 is a scalable object storage service used to store and retrieve any amount of data from anywhere on the internet.
2️⃣ It is designed for:
- High durability
- High availability
- Security

👉 Write this in exam → Direct marks.

### ✅ 2. What Type of Storage is S3?
👉 Object Storage
Stores data as:
1️⃣ Objects (files)
2️⃣ Buckets (containers)
3️⃣ Metadata (data about data)

⭐ Exam Trap:
❌ S3 is NOT block storage.
✅ It is object storage.

### ✅ 3. Key Features of S3
1️⃣ Unlimited storage capacity.
2️⃣ 99.999999999% durability (11 nines).
3️⃣ Highly scalable.
4️⃣ Secure with encryption & policies.
5️⃣ Accessible from anywhere.
VERY COMMON THEORY QUESTION.

### ✅ 4. What is a Bucket?
1️⃣ A container used to store objects.
2️⃣ Bucket name must be globally unique.
3️⃣ Created inside a specific AWS region.

🚨 Exam Trap:
👉 Two buckets cannot have the same name worldwide.

### ✅ 5. What is an Object?
1️⃣ A file stored inside a bucket.
2️⃣ Can be: Image, Video, Document, Backup
👉 Maximum object size = 5 TB
HIGH probability MCQ.

### ✅ 6. S3 Storage Classes (VERY IMPORTANT)
| Class | Description |
|-------|-------------|
| S3 Standard | For frequently accessed data, Low latency |
| S3 Intelligent-Tiering | Automatically moves data to cheaper tier |
| S3 Standard-IA | Lower cost, Used for backups |
| Glacier | Very low cost, Used for archival, Retrieval is slow |

⭐ Exam Favorite: 👉 Cheapest storage → Glacier

### ✅ 7. Versioning
1️⃣ Keep multiple versions of a file.
2️⃣ Protect from accidental deletion.
3️⃣ Enables recovery.
👉 Once enabled → Cannot be fully disabled (only suspended).
VERY COMMON QUESTION.

### ✅ 8. Lifecycle Policy
1️⃣ Automatically moves objects between storage classes.
2️⃣ Can delete old files.
👉 Helps reduce cost.

### ✅ 9. Security in S3

#### ⭐ Bucket Policy
1️⃣ Controls access to bucket.
2️⃣ Written in JSON.

#### ⭐ Encryption
Protects stored data.
Types:
1️⃣ SSE-S3 → Managed by AWS
2️⃣ SSE-KMS → Uses AWS Key Management
3️⃣ SSE-C → Customer-managed keys
👉 Expect MCQ.

### ✅ 10. Public vs Private Buckets
1️⃣ By default → Buckets are private.
2️⃣ Public access must be enabled manually.

🚨 EXAM TRAP:
👉 S3 is NOT public by default.

### ✅ 11. Pre-Signed URL
1️⃣ Provides temporary access to private objects.
2️⃣ Used for secure file sharing.

### ✅ 12. Static Website Hosting
1️⃣ S3 can host static websites.
2️⃣ Supports: HTML, CSS, JS
❌ Cannot run backend code.

### ✅ 13. S3 Event Notifications
Triggers actions when events occur.
Example: 👉 Upload file → Trigger Lambda.
Common integrations: Lambda, SNS, SQS

### ✅ 14. Data Consistency
👉 Modern S3 provides strong read-after-write consistency.
Means:
1️⃣ Upload file
2️⃣ Immediately accessible.

### ✅ 15. Replication
Cross-Region Replication (CRR)
1️⃣ Automatically copies data to another region.
2️⃣ Used for disaster recovery.

### 🔥 S3 vs EBS (SUPER COMMON)
| S3 | EBS |
|-----|-----|
| Object storage | Block storage |
| Unlimited | Limited |
| Serverless | Attached to EC2 |
| Best for files | Best for OS |

👉 Expect this question.

---

## 🔧 Practical Steps: Create Amazon S3 Bucket

### 1️⃣ Login to AWS Console
- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

### 2️⃣ Open S3 Service
- Search **S3** in the search bar
- Click **S3** → **Create bucket**

### 3️⃣ Configure Bucket Details
Fill the basic details:

#### 🔹 Bucket Name
- Must be **globally unique**
- Example: `my-devops-project-bucket-123`

#### 🔹 AWS Region
- Choose region close to you
  Example: `ap-south-1 (Mumbai)`

### 4️⃣ Object Ownership
- Select **ACLs disabled (recommended)**
- Object ownership: **Bucket owner enforced**

### 5️⃣ Block Public Access (IMPORTANT ⚠️)
- ✅ Keep **Block all public access ON** (recommended)
- If hosting a website → you may disable later carefully

### 6️⃣ Bucket Versioning (Optional but Best Practice)
- Enable **Versioning** (recommended)
- Helps recover deleted/overwritten files

### 7️⃣ Encryption
- Enable **Server-side encryption**
- Choose:
  - SSE-S3 (default)
  - SSE-KMS (advanced)

### 8️⃣ Create Bucket
- Review settings
- Click **Create bucket**

🎉 Your S3 bucket is created!

### 📤 Upload Files to S3

### 9️⃣ Upload Object
- Open your bucket
- Click **Upload**
- Add files / folders
- Click **Upload**

### 🔐 (Optional) Make Object Public
⚠️ Use only if required (e.g., static website)
- Select object → **Actions → Make public**
- Or configure **Bucket Policy**

### 🧠 S3 Key Points (Interview ⭐)
- ✔ Object storage (not block/file)
- ✔ Unlimited storage capacity
- ✔ Highly durable (11 nines – 99.999999999%)
- ✔ Used for backups, logs, static websites
- ✔ Global service (but buckets are region-based)

### 🎯 S3 in One Line (Interview)
> Amazon S3 is a **highly durable, scalable object storage service** used to store and retrieve any amount of data.

---

# 🗄️ AWS RDS (Relational Database Service)

## 📚 Theory & Concepts

### ✅ 1. Definition (MEMORIZE THIS)
1️⃣ Amazon RDS is a fully managed service that makes it easy to set up, operate, and scale relational databases in the cloud.
2️⃣ It automates:
- Hardware provisioning
- Database setup
- Backups
- Patching

👉 Write this definition → Direct marks.

### ✅ 2. What Type of Database is RDS?
👉 Relational Database (SQL-based)
Supports:
1️⃣ MySQL
2️⃣ PostgreSQL
3️⃣ Oracle
4️⃣ SQL Server
5️⃣ MariaDB
6️⃣ Amazon Aurora

⭐ VERY COMMON MCQ.

### ✅ 3. Why Use RDS?
1️⃣ Fully managed → No manual maintenance.
2️⃣ Automatic backups.
3️⃣ High availability.
4️⃣ Easy scaling.
5️⃣ Strong security.

### ✅ 4. Key Features of RDS

#### ⭐ Automated Backups
1️⃣ Creates daily snapshots.
2️⃣ Supports point-in-time recovery.
👉 Protects against data loss.

#### ⭐ Multi-AZ Deployment (VERY IMPORTANT)
1️⃣ Creates a standby replica in another Availability Zone.
2️⃣ Automatically switches if primary DB fails.
👉 Improves fault tolerance.
🚨 Exam Favorite.

#### ⭐ Read Replicas
1️⃣ Copies of database used for read traffic.
2️⃣ Improves performance.
👉 Used when application has heavy reads.

### ✅ 5. Storage Scaling
1️⃣ Can increase storage without downtime.
2️⃣ Supports SSD for better performance.

### ✅ 6. Security in RDS
1️⃣ Runs inside VPC.
2️⃣ Use Security Groups to control access.
3️⃣ Supports encryption.
4️⃣ IAM authentication available.

⭐ Best Practice:
👉 Place RDS in Private Subnet.
VERY HIGH probability question.

### ✅ 7. RDS Architecture (Understand This)
👉 User → Application (EC2) → RDS Database
🚨 Database should NOT be public.

### ✅ 8. Multi-AZ vs Read Replica (SUPER COMMON)
| Multi-AZ | Read Replica |
|----------|--------------|
| For high availability | For performance |
| Automatic failover | No automatic failover |
| Disaster recovery | Handles read traffic |

👉 Expect this in exams.

### ✅ 9. Vertical Scaling in RDS
1️⃣ Increase CPU
2️⃣ Increase RAM
3️⃣ Upgrade instance type
👉 Unlike DynamoDB, RDS mainly uses vertical scaling.

### ✅ 10. Snapshots
1️⃣ Manual backups of database.
2️⃣ Stored in S3 internally.
3️⃣ Used for recovery.

### ✅ 11. Maintenance & Patching
1️⃣ AWS automatically updates database software.
2️⃣ Reduces admin workload.

### ✅ 12. Failover
1️⃣ If primary DB crashes → standby becomes primary.
2️⃣ Happens automatically in Multi-AZ.
⭐ Professors LOVE failover questions.

### ✅ 13. RDS is NOT Serverless
👉 You must choose instance size.

🚨 Exam Trap:
❌ RDS is serverless
✅ DynamoDB is serverless
(Note: Aurora Serverless exists, but basic RDS is instance-based.)

### ✅ 14. When Should You Use RDS?
Best for:
1️⃣ Banking systems
2️⃣ ERP applications
3️⃣ E-commerce platforms
4️⃣ Applications requiring SQL
5️⃣ Structured data

### ✅ 15. When NOT to Use RDS?
1️⃣ Massive real-time apps.
2️⃣ Flexible schema requirements.
👉 Use DynamoDB instead.

### 🔥 RDS vs DynamoDB (EXTREMELY IMPORTANT)
| RDS | DynamoDB |
|-----|----------|
| Relational | NoSQL |
| Fixed schema | Flexible schema |
| Vertical scaling | Horizontal scaling |
| SQL queries | Key-value queries |
| Instance-based | Serverless |

⭐ HIGH probability question.

---

## 🔧 Practical Steps: Create Amazon RDS

### 1️⃣ Login to AWS Console
- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

### 2️⃣ Open RDS Service
- Search **RDS**
- Click **RDS → Create database**

### 3️⃣ Choose Database Creation Method
- Select **Standard create** (recommended)

### 4️⃣ Select Database Engine
Choose one:
- **MySQL** ✅ (beginner-friendly)
- PostgreSQL
- MariaDB
- Oracle
- SQL Server

👉 Example used: **MySQL**

### 5️⃣ Choose Template
- **Free Tier** (learning/practice)
- Production (real workloads)
- Dev/Test

👉 Select **Free Tier**

### 6️⃣ Configure Database Settings
- **DB instance identifier**: `my-rds-db`
- **Master username**: `admin`
- **Password**: set a strong password

### 7️⃣ Instance Configuration
- **DB instance class**: `db.t3.micro` (Free Tier)
- **Storage type**: gp3
- **Allocated storage**: 20 GB (default)

### 8️⃣ Connectivity Settings
- **VPC**: Default VPC (or your custom VPC)
- **Public access**:
  - ✅ Yes (learning)
  - ❌ No (production best practice)
- **VPC security group**:
  - Allow inbound **DB port**
    - MySQL → `3306`
    - PostgreSQL → `5432`

### 9️⃣ Database Options
- Database name: `mydatabase`
- Backup retention: default
- Monitoring: disable for free tier

### 🔟 Create Database
- Review all settings
- Click **Create database**

⏳ Status: **Creating → Available**

### 🔗 Connect to RDS

### 1️⃣1️⃣ Get Endpoint
- RDS → Databases → Select DB
- Copy **Endpoint**

### 1️⃣2️⃣ Connect from EC2
```bash
mysql -h <endpoint> -u admin -p
```
(Ensure EC2 security group is allowed in RDS SG)

### 🧠 RDS Key Points (Interview ⭐)
- ✔ Managed relational database
- ✔ Automated backups & patching
- ✔ Supports Multi-AZ
- ✔ Highly available & scalable
- ✔ No OS-level access

### 🎯 RDS in One Line (Interview)
> Amazon RDS is a **fully managed relational database service** that simplifies setup, scaling, and maintenance.

---

# 🔷 AWS DynamoDB

## 📚 Theory & Concepts

### ✅ 1. Definition (MEMORIZE THIS)
1️⃣ Amazon DynamoDB is a fully managed NoSQL database service that provides fast and predictable performance with seamless scalability.
2️⃣ It is a serverless database — no infrastructure management required.
👉 Write this line in exam → Direct marks.

### ✅ 2. Type of Database
👉 NoSQL Database
Means:
1️⃣ No fixed schema.
2️⃣ Stores non-relational data.
3️⃣ Highly flexible.

🚨 Exam Trap:
❌ DynamoDB is relational
✅ DynamoDB is NoSQL

### ✅ 3. Key Features (VERY IMPORTANT)
1️⃣ Fully managed by AWS.
2️⃣ Serverless (no servers to manage).
3️⃣ Automatic scaling.
4️⃣ Ultra-fast performance (single-digit milliseconds).
5️⃣ Built-in security.
6️⃣ Automatic backup.

### ✅ 4. How DynamoDB Stores Data
| SQL Term | DynamoDB Term |
|----------|---------------|
| Table | Table |
| Row | Item |
| Column | Attribute |

⭐ VERY COMMON MCQ.

### ✅ 5. Primary Key (SUPER IMPORTANT)
Used to uniquely identify each item.

#### ⭐ 1. Partition Key
1️⃣ Unique identifier.
2️⃣ Example: UserID

#### ⭐ 2. Composite Key (Partition Key + Sort Key)
Example:
- UserID → Partition
- OrderID → Sort

👉 Allows multiple records for one user.
🚨 Professors LOVE this concept.

### ✅ 6. Capacity Modes
| Mode | Description |
|------|-------------|
| On-Demand Mode | Auto scales, Pay per request, Best for unpredictable traffic |
| Provisioned Mode | Set read/write capacity manually, Cheaper for steady workloads |

👉 Expected MCQ.

### ✅ 7. Secondary Indexes
Used to query data using different attributes.
Types:
1️⃣ Global Secondary Index (GSI)
2️⃣ Local Secondary Index (LSI)
👉 Improves query flexibility.

### ✅ 8. DynamoDB Streams
1️⃣ Captures table activity.
2️⃣ Shows changes like: Insert, Update, Delete
👉 Often used with AWS Lambda.

### ✅ 9. TTL (Time To Live)
1️⃣ Automatically deletes expired items.
2️⃣ Helps reduce storage cost.

### ✅ 10. Security
1️⃣ Encryption enabled by default.
2️⃣ Integrated with IAM for access control.
3️⃣ Supports VPC endpoints.

### ✅ 11. Backup & Restore
1️⃣ Automatic backups available.
2️⃣ Supports point-in-time recovery.
👉 Protects from data loss.

### ✅ 12. Scaling Type
👉 Horizontal Scaling
Means:
1️⃣ Handles millions of requests.
2️⃣ No downtime.

🚨 Exam Trap:
👉 RDS → Vertical scaling
👉 DynamoDB → Horizontal scaling

### ✅ 13. Is DynamoDB Serverless?
👉 ✅ YES.
No instance selection required.

### ✅ 14. When Should You Use DynamoDB?
Best for:
1️⃣ Real-time applications.
2️⃣ Gaming apps.
3️⃣ IoT systems.
4️⃣ Chat applications.
5️⃣ E-commerce carts.

### ✅ 15. When NOT to Use DynamoDB?
1️⃣ Complex joins required.
2️⃣ Structured relational data needed.
👉 Use RDS instead.

### 🔥 DynamoDB vs RDS (EXTREMELY IMPORTANT)
| DynamoDB | RDS |
|----------|-----|
| NoSQL | Relational |
| Flexible schema | Fixed schema |
| Horizontal scaling | Vertical scaling |
| Serverless | Instance-based |
| Faster for large traffic | Better for structured data |

⭐ HIGH probability question.

---

# ⚡ AWS Lambda

## 📚 Theory & Concepts

### ✅ 1. Definition (MEMORIZE THIS – VERY IMPORTANT)
1️⃣ AWS Lambda is a serverless compute service that allows you to run code without provisioning or managing servers.
2️⃣ Code runs only when triggered.
3️⃣ You pay only for execution time.
👉 Write this → Direct marks.

### ✅ 2. What Does "Serverless" Mean?
1️⃣ No server management required.
2️⃣ No infrastructure setup.
3️⃣ Automatic scaling.
4️⃣ Fully managed by AWS.

🚨 Exam Trap:
❌ Serverless means no servers exist
✅ Servers are managed by AWS

### ✅ 3. How Lambda Works (Understand This Flow)
👉 Trigger → Lambda Function → Execute Code → Return Response

Example:
1️⃣ Upload file to S3
2️⃣ Lambda runs automatically
3️⃣ Processes file

⭐ Professors LOVE flow-based questions.

### ✅ 4. Key Features of Lambda
1️⃣ Automatic scaling.
2️⃣ High availability.
3️⃣ Pay-per-use pricing.
4️⃣ Supports multiple programming languages.
5️⃣ Integrates with many AWS services.

### ✅ 5. Supported Languages
1️⃣ Python
2️⃣ Node.js
3️⃣ Java
4️⃣ C#
5️⃣ Go
6️⃣ Ruby
👉 Expected MCQ sometimes.

### ✅ 6. What is a Lambda Function?
1️⃣ A piece of code executed when triggered.
2️⃣ Performs a specific task.
3️⃣ Stateless (does not store data between executions).

### ✅ 7. Common Lambda Triggers (VERY HIGH PROBABILITY)
1️⃣ S3 → File upload
2️⃣ API Gateway → HTTP request
3️⃣ DynamoDB → Data change
4️⃣ CloudWatch → Scheduled job
5️⃣ SNS → Notifications
⭐ Memorize at least 3.

### ✅ 8. Lambda + API Gateway Architecture (SUPER IMPORTANT)
👉 Client → API Gateway → Lambda → DynamoDB

Used for:
- Serverless web apps
- REST APIs

🚨 Expect scenario questions.

### ✅ 9. Execution Time Limit
👉 Maximum execution time = 15 minutes
⭐ Common MCQ.

### ✅ 10. Stateless Nature
1️⃣ Each execution is independent.
2️⃣ No memory of previous runs.
👉 Store data in: DynamoDB, S3

### ✅ 11. Scaling in Lambda
1️⃣ Automatically scales with incoming requests.
2️⃣ Can handle thousands of executions.
👉 No manual scaling needed.

### ✅ 12. Security in Lambda
1️⃣ Uses IAM Roles for permissions.
2️⃣ No need to store access keys.

🚨 VERY IMPORTANT SCENARIO:
👉 How should Lambda access S3 securely?
✅ Attach IAM Role.

### ✅ 13. Pricing Model
You pay for:
1️⃣ Number of requests
2️⃣ Execution duration
3️⃣ Memory used
👉 No charge when not running.

### ✅ 14. When Should You Use Lambda?
Best for:
1️⃣ Real-time file processing.
2️⃣ API backends.
3️⃣ Automation tasks.
4️⃣ Scheduled jobs.
5️⃣ Event-driven apps.

### ✅ 15. When NOT to Use Lambda?
1️⃣ Long-running applications.
2️⃣ Heavy computing tasks.
3️⃣ Applications needing persistent servers.

### 🔥 Lambda vs EC2 (EXTREMELY IMPORTANT)
| Lambda | EC2 |
|--------|-----|
| Serverless | Server-based |
| Auto scaling | Manual scaling |
| Pay per execution | Pay per running server |
| No management | Requires management |

⭐ HIGH probability question.

---

## 🔧 Practical Steps: Create AWS Lambda Function

### 1️⃣ Login to AWS Console
- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

### 2️⃣ Open Lambda Service
- Search **Lambda**
- Click **AWS Lambda**
- Click **Create function**

### 3️⃣ Choose Function Creation Method
Select:
- ✅ **Author from scratch** (recommended for beginners)

### 4️⃣ Configure Basic Function Settings
- **Function name**: `my-first-lambda`
- **Runtime**:
  - Python 3.12 / Node.js 18 / Java 17 (choose one)
- **Architecture**: x86_64 (default)

### 5️⃣ Create Execution Role (IAM)
- Select **Create a new role with basic Lambda permissions**
- This allows logging to **CloudWatch**

👉 Click **Create function**

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

### 7️⃣ Test Lambda Function
- Click **Test**
- Create a test event:
  - Name: `test-event`
  - Keep default JSON
- Click **Test**

✅ Output should show **StatusCode: 200**

### 🔗 (Optional) Add Trigger to Lambda

### 8️⃣ Add Trigger
- Click **Add trigger**
- Choose service:
  - API Gateway (HTTP API)
  - S3 (file upload trigger)
  - EventBridge (cron jobs)
- Configure settings
- Click **Add**

### ⚙️ Configure Lambda Settings (Optional)
- **Memory**: 128 MB → 10 GB
- **Timeout**: Default 3 sec (max 15 min)
- **Environment variables**
- **Permissions**

### 🧠 Lambda Key Points (Interview ⭐)
- ✔ Serverless (no server management)
- ✔ Auto-scales automatically
- ✔ Pay only for execution time
- ✔ Event-driven
- ✔ Max execution time: 15 minutes

### 🎯 Lambda in One Line (Interview)
> AWS Lambda lets you **run code without provisioning or managing servers**, executing only when triggered.

---

# ⚖️ AWS ALB (Application Load Balancer) & Auto Scaling

## 📚 Theory & Concepts

### ✅ AWS ALB - Definition (MEMORIZE THIS)
1️⃣ Application Load Balancer distributes incoming application traffic across multiple targets such as EC2 instances to ensure high availability and reliability.
👉 Write this → Direct marks.

### ✅ What is a Load Balancer?
1️⃣ A service that spreads traffic across multiple servers.
2️⃣ Prevents server overload.
3️⃣ Improves performance.
4️⃣ Ensures fault tolerance.
👉 If one server fails → traffic goes to another.

### ✅ Types of AWS Load Balancers (COMMON MCQ)
| Type | Description |
|------|-------------|
| Application Load Balancer (ALB) | Layer 7, Handles HTTP/HTTPS/WebSockets, Best for web apps |
| Network Load Balancer (NLB) | Layer 4, Ultra-high performance, Handles TCP/UDP |
| Classic Load Balancer (CLB) | Older generation, Less flexible |

🚨 Exam Tip: 👉 ALB is the most commonly used today.

### ✅ Key Features of ALB
1️⃣ Route traffic based on URL path.
Example:
- /images → Server 1
- /videos → Server 2

2️⃣ Host-based routing.
3️⃣ Supports HTTPS.
4️⃣ Performs health checks.
5️⃣ Integrates with Auto Scaling.
⭐ VERY IMPORTANT.

### ✅ What are Target Groups?
1️⃣ Logical group of servers.
2️⃣ ALB routes traffic to these targets.
Targets can be: EC2, Containers, IP addresses
👉 Health checks decide which targets receive traffic.

### ✅ Health Checks
1️⃣ Monitor server health.
2️⃣ If instance fails → ALB stops sending traffic.
🚨 Professors LOVE this concept.

### ✅ Benefits of ALB
1️⃣ High availability.
2️⃣ Better fault tolerance.
3️⃣ Improved application performance.
4️⃣ Smart traffic routing.

---

### ✅ AWS Auto Scaling - Definition (MEMORIZE THIS)
1️⃣ Auto Scaling automatically adjusts the number of EC2 instances based on demand to maintain performance and reduce cost.
👉 Direct scoring line.

### ✅ Why Auto Scaling is Used?
1️⃣ Handles sudden traffic spikes.
2️⃣ Prevents server crashes.
3️⃣ Saves money by removing unused servers.
4️⃣ Maintains consistent performance.

### ✅ Types of Scaling
| Type | Description |
|------|-------------|
| Dynamic Scaling | Automatically adds/removes instances based on metrics |
| Scheduled Scaling | Scales at specific times |
| Predictive Scaling | Uses machine learning to forecast traffic |

### ✅ Scaling Directions
| Direction | Description |
|-----------|-------------|
| Scale Out | Add more instances, Handles high traffic |
| Scale In | Remove instances, Saves cost |

⭐ VERY COMMON MCQ.

### ✅ Auto Scaling Components
1️⃣ Launch Template → Defines instance configuration.
2️⃣ Auto Scaling Group (ASG) → Controls instance count.
3️⃣ Scaling Policies → Rules for scaling.
👉 Remember ASG — exam favorite.

### ✅ Minimum, Desired, Maximum Capacity
Example:
- Min = 2
- Desired = 4
- Max = 10

👉 AWS keeps instances between these limits.

---

## 🔧 Practical Steps: Create Load Balancer & Auto Scaling

### 🔹 PART A: Create Load Balancer (ALB)

### 1️⃣ Login to AWS Console
- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

### 2️⃣ Open EC2 Dashboard
- Search **EC2**
- Go to **EC2 → Load Balancers**
- Click **Create Load Balancer**

### 3️⃣ Choose Load Balancer Type
Select:
- ✅ **Application Load Balancer (ALB)** (Used for HTTP/HTTPS traffic)
Click **Create**

### 4️⃣ Configure Load Balancer
- **Name**: `web-alb`
- **Scheme**: Internet-facing
- **IP type**: IPv4

### 5️⃣ Network Mapping
- Select **VPC**
- Select **at least 2 public subnets** (different AZs)

### 6️⃣ Configure Security Group
- Allow:
  - HTTP → Port 80 → Anywhere
  - HTTPS → Port 443 → Anywhere (optional)

### 7️⃣ Create Target Group
- Target type: **Instance**
- Protocol: HTTP
- Port: 80
- Health check path: `/`

👉 Click **Create Load Balancer**

### 8️⃣ Register Targets
- Select EC2 instances
- Click **Include as pending**
- Click **Register targets**

✅ Load Balancer created

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

### 🔟 Create Auto Scaling Group
- Go to **EC2 → Auto Scaling Groups**
- Click **Create Auto Scaling Group**
- Select **Launch Template**

### 1️⃣1️⃣ Configure Network
- Select same **VPC**
- Choose **private or public subnets** (multiple AZs)

### 1️⃣2️⃣ Attach Load Balancer
- Select:
  - ✅ Attach to existing Load Balancer
  - Choose **Target Group**
- Enable **ELB health checks**

### 1️⃣3️⃣ Set Scaling Policy
Example:
- Desired capacity: **2**
- Minimum: **1**
- Maximum: **4**

Scaling policy:
- Scale out if **CPU > 70%**
- Scale in if **CPU < 30%**

### 1️⃣4️⃣ Review & Create
- Review configuration
- Click **Create Auto Scaling Group**

🎉 Auto Scaling is live!

### 🔍 Verify Setup
- EC2 instances auto-launch
- Load Balancer → **Targets → Healthy**
- Open **ALB DNS name** in browser

### 🧠 Key Interview Points ⭐
- ✔ Load Balancer distributes traffic
- ✔ Auto Scaling adjusts instance count
- ✔ Works across **multiple AZs**
- ✔ Improves **availability & scalability**
- ✔ Used in **production architectures**

### 🎯 One-Line Interview Answers
**Load Balancer:**
> Distributes incoming traffic across multiple EC2 instances to ensure high availability.

**Auto Scaling:**
> Automatically increases or decreases EC2 instances based on demand.

---

# 🌐 AWS Route 53

## 📚 Theory & Concepts

### ✅ 1. Definition (MEMORIZE THIS)
1️⃣ Amazon Route 53 is a highly available and scalable Domain Name System (DNS) web service that routes users to internet applications.
👉 Example: Converts www.google.com → IP address
👉 Write this line → Direct marks.

### ✅ 2. Why is it Called Route 53?
1️⃣ "Route" → Routes traffic.
2️⃣ "53" → DNS uses port 53.
⭐ Common MCQ.

### ✅ 3. What is DNS?
👉 Domain Name System converts human-readable domain names into machine-readable IP addresses.
Example: amazon.com → 192.0.2.1
VERY IMPORTANT theory question.

### ✅ 4. Key Functions of Route 53
1️⃣ Domain registration.
2️⃣ DNS routing.
3️⃣ Health checking.
4️⃣ Traffic management.

### ✅ 5. What is a Hosted Zone?
1️⃣ A container for DNS records.
2️⃣ Stores information about your domain.
Example records: IP address, Mail server
👉 Without hosted zone → Domain cannot route traffic.

### ✅ 6. Types of Hosted Zones
| Type | Description |
|------|-------------|
| Public Hosted Zone | Routes traffic on the internet |
| Private Hosted Zone | Used inside VPC, Enables internal communication |

⭐ Expected MCQ.

### ✅ 7. DNS Records (VERY IMPORTANT)
| Record | Description |
|--------|-------------|
| A Record | Maps domain → IPv4 address |
| AAAA Record | Maps domain → IPv6 address |
| CNAME | Maps domain → another domain |
| MX Record | Used for email servers |

👉 Professors often ask A vs CNAME.

### ✅ 8. Routing Policies (EXTREMELY IMPORTANT)
| Policy | Description |
|--------|-------------|
| Simple Routing | Routes traffic to a single resource |
| Weighted Routing | Splits traffic based on percentage |
| Latency-Based Routing | Sends users to the nearest server |
| Failover Routing | Switches to backup server if primary fails |
| Geolocation Routing | Routes traffic based on user location |

⭐ VERY FREQUENT.

### ✅ 9. Health Checks
1️⃣ Monitors application health.
2️⃣ If server fails → redirects traffic.
👉 Improves availability.
Professors LOVE this.

### ✅ 10. Route 53 Architecture (Understand This Flow)
👉 User → Route 53 → Load Balancer → EC2
⭐ Expect scenario questions.

### ✅ 11. Domain Registration
1️⃣ You can buy domains directly from Route 53.
Example: 👉 mywebsite.com

### ✅ 12. TTL (Time To Live)
1️⃣ Determines how long DNS info is cached.
2️⃣ Lower TTL → Faster updates.
Common MCQ.

### ✅ 13. Is Route 53 Global?
👉 ✅ YES — It is a global service.

🚨 Exam Trap:
❌ Route 53 is regional
✅ It is global.

### ✅ 14. Benefits of Route 53
1️⃣ Highly reliable.
2️⃣ Low latency.
3️⃣ Automatic failover.
4️⃣ Scalable.
5️⃣ Secure.

---

## 🔧 Practical Steps: Create Amazon Route 53 (DNS)

### 1️⃣ Login to AWS Console
- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

### 2️⃣ Open Route 53 Service
- Search **Route 53**
- Click **Route 53 Dashboard**

### 🏷️ PART A: Create Hosted Zone

### 3️⃣ Create Hosted Zone
- Click **Hosted zones**
- Click **Create hosted zone**

Fill details:
- **Domain name**: `example.com`
- **Type**: Public hosted zone
- Comment: optional

Click **Create hosted zone**

### 4️⃣ Note Name Servers
- After creation, Route 53 gives **NS records**
- Example:
  ```
  ns-123.awsdns-45.net
  ns-678.awsdns-90.org
  ```

⚠️ These must be added at your domain registrar

### 🔁 PART B: Point Domain to AWS (DNS Records)

### 5️⃣ Create Record
- Open your hosted zone
- Click **Create record**

### 6️⃣ Choose Record Type
Common records:
| Record | Use |
|--------|-----|
| A | Point domain to IP |
| CNAME | Alias domain |
| ALIAS | AWS resource (ALB, S3) |
| MX | Email routing |

Example:
- **Record type**: A
- **Value**: EC2 public IP

OR
- **Alias**: Application Load Balancer

Click **Create record**

### 🔗 Example: Connect Domain to ALB (Best Practice)

### 7️⃣ Create Alias Record
- Record name: `www`
- Type: A
- Enable **Alias**
- Choose:
  - Application Load Balancer
  - Select region & ALB

### 🧠 Route 53 Key Points (Interview ⭐)
- ✔ Highly available DNS service
- ✔ Supports routing policies
- ✔ Integrates with ALB, S3, CloudFront
- ✔ Health checks & failover
- ✔ Domain registration + DNS

### 🎯 Route 53 in One Line (Interview)
> Amazon Route 53 is a **highly available and scalable DNS service** that routes users to AWS resources.

---

# 🌍 AWS CloudFront

## 📚 Theory & Concepts

CloudFront is AWS's Content Delivery Network (CDN) that delivers content with low latency using edge locations worldwide.

### Key Features:
1️⃣ Caches content at edge locations
2️⃣ Reduces latency
3️⃣ Supports S3, ALB, EC2, APIs
4️⃣ Improves performance & security

---

## 🔧 Practical Steps: Create Amazon CloudFront (CDN)

### 1️⃣ Login to AWS Console
- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

### 2️⃣ Open CloudFront Service
- Search **CloudFront**
- Click **CloudFront**
- Click **Create a CloudFront distribution**

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

### 4️⃣ Configure Default Cache Behavior
Important settings:
- **Viewer protocol policy**: Redirect HTTP to HTTPS ✅
- **Allowed HTTP methods**: GET, HEAD (static content)
- **Cache policy**: Managed-CachingOptimized (recommended)

### 5️⃣ Security Settings (Optional but recommended)
- **Enable WAF** (advanced)
- **Enable HTTPS** (default)
- **Use default CloudFront certificate**
  - Or custom domain with ACM (advanced)

### 6️⃣ Distribution Settings
- **Price class**: Use all edge locations (best performance)
- **Default root object**: `index.html` (for websites)

### 7️⃣ Create Distribution
- Review settings
- Click **Create distribution**

⏳ Status: **Deploying** → **Enabled** (Takes 5–15 minutes)

### 8️⃣ Access CloudFront
- Copy **Distribution domain name**
  ```
  d123abcd.cloudfront.net
  ```
- Open in browser 🎉

### 🧠 CloudFront Key Points (Interview ⭐)
- ✔ Content Delivery Network (CDN)
- ✔ Caches content at **edge locations**
- ✔ Reduces latency & load on backend
- ✔ Supports S3, ALB, EC2, APIs
- ✔ Improves performance & security

### 🎯 CloudFront in One Line (Interview)
> Amazon CloudFront is a **global CDN service** that delivers content with **low latency and high performance** using edge locations.

---

# ☁️ AWS CloudFormation

## 📚 Theory & Concepts

### ✅ 1. Definition (MEMORIZE THIS)
1️⃣ AWS CloudFormation is an Infrastructure as Code (IaC) service that allows you to create and manage AWS resources using templates.
2️⃣ It automates infrastructure setup.
👉 Write this → Direct marks.

### ✅ 2. What is Infrastructure as Code (IaC)?
1️⃣ Managing infrastructure through code instead of manual setup.
2️⃣ Automatically provisions resources.
3️⃣ Reduces human errors.
Example: 👉 Launch EC2 + VPC + RDS using a template.
⭐ VERY COMMON THEORY QUESTION.

### ✅ 3. Why Use CloudFormation?
1️⃣ Automates resource creation.
2️⃣ Saves time.
3️⃣ Ensures consistent infrastructure.
4️⃣ Supports version control.
5️⃣ Enables easy rollback.

### ✅ 4. How CloudFormation Works (Understand This Flow)
👉 Template → Stack → Resources Created Automatically

Steps:
1️⃣ Write template (JSON/YAML).
2️⃣ Upload to CloudFormation.
3️⃣ Create stack.
4️⃣ AWS provisions resources.

⭐ Professors LOVE flow questions.

### ✅ 5. What is a Template?
1️⃣ A blueprint describing AWS resources.
2️⃣ Written in: JSON or YAML
Defines: EC2, VPC, S3, RDS
👉 No template → No stack.

### ✅ 6. What is a Stack? (VERY IMPORTANT)
1️⃣ A collection of AWS resources created together.
2️⃣ Managed as a single unit.
Example: 👉 One stack can include: EC2, Load Balancer, Database
⭐ HIGH probability MCQ.

### ✅ 7. Stack Operations
1️⃣ Create stack → Launch resources.
2️⃣ Update stack → Modify infrastructure.
3️⃣ Delete stack → Remove all resources.
👉 Makes management easy.

### ✅ 8. Rollback Feature (EXAM FAVORITE)
1️⃣ If stack creation fails → AWS automatically rolls back changes.
2️⃣ Prevents partial infrastructure.
👉 Improves reliability.

### ✅ 9. Benefits of CloudFormation
1️⃣ Fully automated deployment.
2️⃣ Consistent environments.
3️⃣ Reduces manual configuration.
4️⃣ Supports DevOps practices.
5️⃣ Faster infrastructure setup.

### ✅ 10. CloudFormation is Region-Based
👉 Templates run in a specific region.

🚨 Exam Trap:
❌ Global
✅ Regional

### ✅ 11. Change Sets
1️⃣ Preview changes before updating stack.
2️⃣ Shows what will be modified.
👉 Helps avoid mistakes.

### ✅ 12. Drift Detection
1️⃣ Detects manual changes made outside CloudFormation.
2️⃣ Keeps infrastructure consistent.

### ✅ 13. CloudFormation vs Manual Setup
| CloudFormation | Manual Setup |
|----------------|--------------|
| Automated | Time-consuming |
| Less error | Human errors |
| Repeatable | Hard to repeat |

⭐ Expected difference question.

### ✅ 14. CloudFormation vs Terraform (Sometimes Asked)
| CloudFormation | Terraform |
|----------------|-----------|
| AWS native | Multi-cloud |
| No extra tool | Third-party tool |
| Deep AWS integration | Works across providers |

### ✅ 15. When Should You Use CloudFormation?
1️⃣ Large infrastructure deployment.
2️⃣ DevOps automation.
3️⃣ Repeating environments.
4️⃣ CI/CD pipelines.

---

## 🔧 Practical Steps: Create AWS CloudFormation Stack

### 1️⃣ Login to AWS Console
- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

### 2️⃣ Open CloudFormation Service
- Search **CloudFormation**
- Click **CloudFormation**
- Click **Create stack**

### 3️⃣ Choose Stack Creation Method
Select **one** option:
- ✅ **Upload a template file** (YAML/JSON)
- Amazon S3 URL
- Use a sample template

👉 Common choice: **Upload a template file**

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

### 5️⃣ Specify Stack Details
- **Stack name**: `my-first-stack`
- Fill **parameters** (if any)
- Click **Next**

### 6️⃣ Configure Stack Options (Optional)
- Tags (Environment: Dev)
- IAM Role (optional)
- Rollback settings

Click **Next**

### 7️⃣ Review & Create Stack
- Review all settings
- Check **I acknowledge IAM resources** (if shown)
- Click **Create stack**

### 8️⃣ Monitor Stack Creation
- Status changes:
  - `CREATE_IN_PROGRESS`
  - `CREATE_COMPLETE` ✅
- Check **Events** tab for errors/logs

### 🔄 Update CloudFormation Stack
- Modify template
- Click **Update stack**
- Upload updated template
- Review → Update

### 🗑️ Delete Stack
- Select stack
- Click **Delete**
- All resources are deleted automatically

### 🧠 CloudFormation Key Points (Interview ⭐)
- ✔ Infrastructure as Code (IaC)
- ✔ Declarative (what, not how)
- ✔ Repeatable & version-controlled
- ✔ Automatic rollback on failure
- ✔ Supports YAML & JSON

### 🎯 CloudFormation in One Line (Interview)
> AWS CloudFormation lets you **model, provision, and manage AWS infrastructure using code**.

---

# 📊 AWS Monitoring (Amazon CloudWatch)

## 📚 Theory & Concepts

### ✅ 1. Definition (MEMORIZE THIS)
1️⃣ Amazon CloudWatch is a monitoring and observability service that tracks AWS resources and applications in real time.
2️⃣ It collects:
- Metrics
- Logs
- Events

👉 Write this → Direct marks.

### ✅ 2. Why Monitoring is Important?
1️⃣ Detect system failures early.
2️⃣ Improve performance.
3️⃣ Ensure high availability.
4️⃣ Automate responses.
5️⃣ Troubleshoot issues quickly.

### ✅ 3. What Does CloudWatch Monitor?
1️⃣ EC2 → CPU usage, memory.
2️⃣ RDS → DB connections.
3️⃣ Lambda → Execution time.
4️⃣ Auto Scaling → Instance count.
5️⃣ ELB/ALB → Traffic.
⭐ VERY COMMON MCQ.

### ✅ 4. Key Components of CloudWatch

#### ⭐ 1. Metrics
1️⃣ Numerical data showing system performance.
Examples: CPU utilization, Network traffic, Disk usage
👉 Think of metrics as performance numbers.

#### ⭐ 2. Logs
1️⃣ Records of events happening in the system.
2️⃣ Helps in debugging errors.
Example: 👉 Application crash logs.

#### ⭐ 3. Alarms (VERY IMPORTANT)
1️⃣ Trigger notifications when a threshold is crossed.
Example: 👉 CPU > 80% → Send alert.
🚨 Professors LOVE alarm-based questions.

#### ⭐ 4. Events (EventBridge)
1️⃣ Respond automatically to system changes.
2️⃣ Enables automation.
Example: 👉 Launch new EC2 if usage spikes.

### ✅ 5. CloudWatch Alarm Flow (Understand This)
👉 Metric → Threshold → Alarm → Action

Example:
1️⃣ CPU increases
2️⃣ Alarm triggers
3️⃣ Auto Scaling adds instance

⭐ HIGH probability scenario.

### ✅ 6. CloudWatch + Auto Scaling (SUPER IMPORTANT)
👉 CloudWatch detects load → triggers Auto Scaling.

Architecture:
👉 User Traffic ↑ → CloudWatch Alarm → Auto Scaling → New EC2

Expect scenario questions.

### ✅ 7. CloudWatch Logs
1️⃣ Central place to store logs.
2️⃣ Monitor application health.
3️⃣ Helps in troubleshooting.

### ✅ 8. Custom Metrics
1️⃣ You can create your own metrics.
2️⃣ Example: 👉 Track number of app users.

### ✅ 9. CloudWatch Dashboard
1️⃣ Visual display of metrics.
2️⃣ Shows system health in one place.
👉 Useful for operations teams.

### ✅ 10. Notifications with SNS
1️⃣ CloudWatch integrates with SNS (Simple Notification Service).
2️⃣ Sends alerts via: Email, SMS
⭐ Expected MCQ sometimes.

### ✅ 11. Is CloudWatch Regional?
👉 ✅ YES — operates at region level.

🚨 Exam Trap:
❌ CloudWatch is global
✅ It is regional.

### ✅ 12. CloudTrail vs CloudWatch (SUPER COMMON)
| CloudWatch | CloudTrail |
|------------|------------|
| Monitors performance | Tracks user activity |
| Metrics & logs | API calls |
| Operational data | Security auditing |

👉 Remember this difference!

### ✅ 13. Benefits of CloudWatch
1️⃣ Real-time monitoring.
2️⃣ Automated alerts.
3️⃣ Better reliability.
4️⃣ Improved security.
5️⃣ Faster troubleshooting.

---

## 🔧 Practical Steps: Create AWS Monitoring (CloudWatch)

### 1️⃣ Login to AWS Console
- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

### 2️⃣ Open CloudWatch Service
- Search **CloudWatch**
- Click **CloudWatch Dashboard**

### 🔹 PART A: Monitor Resources (Metrics)

### 3️⃣ View CloudWatch Metrics
- CloudWatch → **Metrics**
- Choose service: EC2, RDS, Lambda, ECS, ALB

Example:
- EC2 → **Per-Instance Metrics**
- Select **CPUUtilization**

📈 Metrics are enabled by default

### 🔹 PART B: Create CloudWatch Alarm (Very Important)

### 4️⃣ Create Alarm
- CloudWatch → **Alarms**
- Click **Create alarm**

### 5️⃣ Select Metric
Example:
- EC2 → Per-Instance → **CPUUtilization**
- Click **Select metric**

### 6️⃣ Configure Alarm Condition
Example:
- Threshold type: Static
- Condition: `CPUUtilization > 70%`
- Duration: 5 minutes

### 7️⃣ Configure Notification (SNS)
- Create new SNS topic:
  - Name: `cpu-alerts`
  - Email: your email
- Confirm email subscription

### 8️⃣ Create Alarm
- Review
- Click **Create alarm**

🚨 Alert triggers when threshold is crossed

### 🔹 PART C: Enable Log Monitoring (Logs)

### 9️⃣ Create Log Group
- CloudWatch → **Logs → Log groups**
- Click **Create log group**
- Name: `/ec2/application-logs`

### 🔟 Send Logs to CloudWatch
For EC2:
- Install **CloudWatch Agent**
```bash
sudo yum install amazon-cloudwatch-agent -y
```
- Start agent and configure logs

For Lambda:
- Logs are **automatic**

### 🔹 PART D: Create CloudWatch Dashboard

### 1️⃣1️⃣ Create Dashboard
- CloudWatch → **Dashboards**
- Click **Create dashboard**
- Name: `my-monitoring-dashboard`

### 1️⃣2️⃣ Add Widgets
- Line graph
- Number
- Text

Examples:
- EC2 CPU usage
- RDS connections
- Lambda invocations

📊 Single view for all monitoring

### 🧠 AWS Monitoring Key Points (Interview ⭐)
- ✔ CloudWatch is AWS native monitoring
- ✔ Metrics, Logs, Alarms, Dashboards
- ✔ Integrated with all AWS services
- ✔ SNS for alerting
- ✔ Near real-time visibility

### 🎯 AWS Monitoring in One Line (Interview)
> AWS monitoring uses **CloudWatch to collect metrics, logs, and events for observing and alerting on cloud resources**.

### 🔥 Real DevOps Use Cases
- CPU / Memory alerts
- Application log analysis
- Auto Scaling triggers
- Cost optimization
- Incident monitoring

### 📌 Typical Monitoring Architecture
```
AWS Resource → CloudWatch Metrics / Logs
           → CloudWatch Alarm
           → SNS (Email / SMS)
```

---

# 🐳 AWS EKS (Elastic Kubernetes Service) & ECR

## 📚 Theory & Concepts

### ✅ AWS EKS - Definition (MEMORIZE THIS)
1️⃣ Amazon EKS is a fully managed service that makes it easy to run Kubernetes on AWS without managing control plane infrastructure.
👉 Direct scoring line.

### ✅ What is Kubernetes?
1️⃣ An open-source platform used to manage containerized applications.
2️⃣ Automates: Deployment, Scaling, Management
⭐ Common theory question.

### ✅ Why Use EKS?
1️⃣ AWS manages Kubernetes control plane.
2️⃣ High availability.
3️⃣ Automatic updates & patching.
4️⃣ Scalable container orchestration.

### ✅ What Does EKS Manage?
👉 AWS manages:
1️⃣ Control plane
2️⃣ API servers
3️⃣ etcd database

👉 You manage:
- Worker nodes
- Applications

⭐ Expected MCQ.

### ✅ Key Components of EKS
| Component | Description |
|-----------|-------------|
| Cluster | Group of worker machines running containers |
| Node | EC2 instance that runs containers |
| Pod | Smallest deployable unit in Kubernetes |

🚨 Professors LOVE "Pod" questions.

### ✅ EKS Architecture Flow
👉 User → Load Balancer → EKS Cluster → Pods → Containers

Understand this once → Many questions solved.

### ✅ Benefits of EKS
1️⃣ Fully managed Kubernetes.
2️⃣ Highly secure.
3️⃣ Scales automatically.
4️⃣ Integrates with AWS services.

⚠️ Limitation: Requires Kubernetes knowledge.

---

### 🔥 AWS ECR - Definition (MEMORIZE THIS)
1️⃣ Amazon ECR is a fully managed Docker container registry used to store, manage, and deploy container images.
👉 Direct marks.

### ✅ What is a Container Image?
1️⃣ A file that contains: Application code, Libraries, Dependencies
👉 Used to run containers.

### ✅ Why Use ECR?
1️⃣ Secure image storage.
2️⃣ Highly scalable.
3️⃣ Integrated with EKS & ECS.
4️⃣ Private repositories.

### ✅ How ECR Works (Flow)
👉 Developer → Push Image → ECR → Pull Image → Deploy on EKS
⭐ VERY IMPORTANT flow-based question.

### ✅ Public vs Private Repository
| Type | Description |
|------|-------------|
| Private Repo | Only authorized users can access |
| Public Repo | Anyone can pull images |

Expected MCQ.

### ✅ Security in ECR
1️⃣ Uses IAM permissions.
2️⃣ Supports image scanning.
3️⃣ Encryption enabled.

### 🔥 EKS vs ECS (SUPER COMMON)
| EKS | ECS |
|-----|-----|
| Uses Kubernetes | AWS native container service |
| More flexible | Easier to use |
| Industry standard | AWS-specific |

👉 Expect this difference.

### 🔥 ECR vs Docker Hub
| ECR | Docker Hub |
|-----|------------|
| AWS managed | Third-party |
| Private & secure | Public by default |
| IAM integrated | Limited IAM |

---

# 🐳 AWS ECS (Elastic Container Service)

## 📚 Theory & Concepts

Amazon ECS is a fully managed container orchestration service for running Docker containers at scale.

### Key Features:
1️⃣ Container orchestration service
2️⃣ Supports Docker containers
3️⃣ Fargate = serverless containers
4️⃣ Integrates with ALB, IAM, CloudWatch
5️⃣ Used for microservices

---

## 🔧 Practical Steps: Create Amazon ECS (Container Service)

### 1️⃣ Login to AWS Console
- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

### 2️⃣ Open ECS Service
- Search **ECS**
- Click **Elastic Container Service**
- Click **Create cluster**

### 🔹 PART A: Create ECS Cluster

### 3️⃣ Choose Cluster Type
Select:
- ✅ **AWS Fargate** (serverless – recommended)
- EC2 instances (self-managed – advanced)

👉 Choose **AWS Fargate** → Next

### 4️⃣ Configure Cluster
- **Cluster name**: `my-ecs-cluster`
- Infrastructure: AWS Fargate
- Networking: Default VPC (or custom)

Click **Create**

✅ Cluster created

### 🔹 PART B: Create Task Definition

### 5️⃣ Create Task Definition
- ECS → **Task Definitions**
- Click **Create new task definition**
- Choose **AWS Fargate**

### 6️⃣ Configure Task Definition
- **Task definition name**: `my-app-task`
- **Task role**: None (or IAM role if needed)
- **Operating system**: Linux
- **CPU**: 0.5 vCPU
- **Memory**: 1 GB

### 7️⃣ Add Container
- **Container name**: `my-container`
- **Image**: `nginx:latest`
- **Port mappings**: Container port: 80
- Click **Add**

👉 Click **Create**

### 🔹 PART C: Create ECS Service

### 8️⃣ Create Service
- Go to **Clusters → my-ecs-cluster**
- Click **Create service**

### 9️⃣ Service Configuration
- Launch type: **Fargate**
- Task definition: `my-app-task`
- Service name: `my-ecs-service`
- Desired tasks: 1

### 🔟 Networking Configuration
- VPC: Default
- Subnets: Select **public subnets**
- Security group: Allow **HTTP (80)**
- Enable **Auto-assign public IP**

### 1️⃣1️⃣ (Optional) Load Balancer
- Choose **Application Load Balancer**
- Create new target group
- Listener: HTTP 80

### 1️⃣2️⃣ Create Service
- Review
- Click **Create service**

🎉 ECS service is running!

### 🔍 Verify ECS Deployment
- ECS → Cluster → Services
- Task status: **RUNNING**
- Open: `http://<Public-IP>` (or ALB DNS)

### 🧠 ECS Key Points (Interview ⭐)
- ✔ Container orchestration service
- ✔ Supports Docker containers
- ✔ Fargate = serverless containers
- ✔ Integrates with ALB, IAM, CloudWatch
- ✔ Used for microservices

### 🎯 ECS in One Line (Interview)
> Amazon ECS is a **fully managed container orchestration service** for running Docker containers at scale.

### 🔥 Real DevOps Use Cases
- Microservices deployment
- CI/CD container pipelines
- Blue-Green deployments
- Backend APIs & workers

### 📌 ECS Architecture (Simple)
```
Docker Image → ECS Task → ECS Service → ALB → Users
```

---

# 🚀 AWS Amplify

## 📚 Theory & Concepts

### ✅ 1. Definition (MEMORIZE THIS)
1️⃣ AWS Amplify is a development platform that helps developers build, deploy, and host full-stack web and mobile applications quickly.
2️⃣ It simplifies frontend + backend integration.
👉 Write this → Direct marks.

### ✅ 2. Why Use Amplify?
1️⃣ Speeds up app development.
2️⃣ Automates deployment.
3️⃣ Easily connects frontend to AWS backend.
4️⃣ No deep cloud knowledge required.
5️⃣ Supports CI/CD.

### ✅ 3. What Can You Build with Amplify?
1️⃣ Web applications.
2️⃣ Mobile apps.
3️⃣ Full-stack apps.
4️⃣ Serverless applications.

### ✅ 4. Key Features of Amplify

#### ⭐ 1. Hosting
1️⃣ Deploy websites quickly.
2️⃣ Provides global CDN for fast delivery.
3️⃣ Supports custom domains.

#### ⭐ 2. Backend Integration
Easily connects to AWS services like:
1️⃣ Lambda → Serverless functions
2️⃣ DynamoDB → Database
3️⃣ Cognito → Authentication
4️⃣ S3 → Storage
⭐ Expected MCQ.

#### ⭐ 3. Authentication
1️⃣ Built-in user login system.
2️⃣ Supports: Email/password, Google, Facebook
👉 Uses Amazon Cognito internally.

#### ⭐ 4. CI/CD Automation
1️⃣ Automatically builds and deploys apps when code changes.
2️⃣ Integrates with GitHub.

### ✅ 5. How Amplify Works (Flow)
👉 Developer → Push Code → Amplify Builds → Deploys App

Simple 🙂

### ✅ 6. Amplify vs Traditional Deployment
| Amplify | Traditional |
|---------|-------------|
| Automated | Manual setup |
| Faster | Slower |
| Beginner-friendly | Complex |

### ✅ 7. Amplify is Best For
1️⃣ Frontend developers.
2️⃣ Startups.
3️⃣ Rapid prototyping.
4️⃣ Serverless apps.

### ✅ 8. Amplify Supports Popular Frameworks
1️⃣ React
2️⃣ Angular
3️⃣ Vue
4️⃣ Flutter
5️⃣ iOS / Android
⭐ Sometimes asked in MCQs.

### ✅ 9. Is Amplify Serverless?
👉 ✅ YES — mostly uses serverless services behind the scenes.

### ✅ 10. Security in Amplify
1️⃣ Uses IAM roles.
2️⃣ Authentication via Cognito.
3️⃣ Secure API access.

---

## 🔧 Practical Steps: Create AWS Amplify App

### 1️⃣ Login to AWS Console
- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

### 2️⃣ Open AWS Amplify
- Search **Amplify**
- Click **AWS Amplify**
- Click **Get started** (or **Create new app**)

### 🔹 PART A: Deploy Frontend App (Most Common)

### 3️⃣ Choose App Type
- Select **Host web app**
- Click **Next**

### 4️⃣ Connect Source Code Repository
Choose repository provider:
- GitHub ✅ (most common)
- GitLab
- Bitbucket
- AWS CodeCommit

👉 Authorize Amplify to access your repo

### 5️⃣ Select Repository & Branch
- Choose **repository**
- Select **branch** (e.g., `main`)
- Click **Next**

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

### 7️⃣ Review & Deploy
- Review settings
- Click **Save and deploy**

⏳ Status: Provisioning → Build → Deploy → **Live** ✅

### 8️⃣ Access Your App
- Amplify provides a default URL:
```
https://main.d123abc.amplifyapp.com
```

🎉 Your app is live!

### 🔐 (Optional) Add Backend with Amplify
You can add:
- Authentication (Cognito)
- API (REST / GraphQL)
- Storage (S3)
- Functions (Lambda)

From Amplify console:
- **Backend environments → Create backend**

### 🧠 Amplify Key Points (Interview ⭐)
- ✔ Fully managed frontend hosting
- ✔ CI/CD built-in
- ✔ Supports modern frameworks
- ✔ Easy backend integration
- ✔ Scales automatically

### 🎯 Amplify in One Line (Interview)
> AWS Amplify is a **fully managed platform to build, deploy, and host scalable web and mobile applications**.

### 🔥 Real DevOps / Cloud Use Cases
- React / Next.js hosting
- Frontend CI/CD pipelines
- Serverless full-stack apps
- Startup MVP deployment

### 📌 Typical Architecture
```
GitHub → AWS Amplify → CloudFront → Users
                     → (Optional Backend: Lambda, API, Cognito)
```

---

# 🖼️ AWS AMI (Amazon Machine Image)

## 📚 Theory & Concepts

An AMI is a pre-configured template used to launch EC2 instances with the same OS, software, and settings.

### Key Points:
- ✔ AMI is a **template** for EC2
- ✔ Includes: OS, Installed software, EBS snapshots
- ✔ AMIs are **region-specific**
- ✔ Can be **copied to other regions**
- ✔ Used for **autoscaling & disaster recovery**

---

## 🔧 Practical Steps: Create AMI (Amazon Machine Image)

### 1️⃣ Login to AWS Console
- Open **AWS Management Console**
- Sign in to **Amazon Web Services**

### 2️⃣ Open EC2 Service
- Search **EC2**
- Go to **EC2 → Instances**

### 3️⃣ Select the EC2 Instance
- Choose the **running or stopped** EC2 instance
- This instance may already have:
  - OS updates
  - Applications (Docker, Jenkins, etc.)
  - Configuration

### 4️⃣ Create Image (AMI)
- Click **Actions**
- Go to **Image and templates**
- Click **Create image**

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

### 6️⃣ Create AMI
- Click **Create image**
- AMI creation starts in background

⏳ Status: **Pending → Available**

### 7️⃣ Check AMI Status
- Go to **EC2 → AMIs**
- Select **Owned by me**
- Wait until status is **Available**

### 🚀 Launch EC2 from AMI

### 8️⃣ Launch Instance Using AMI
- Select the AMI
- Click **Launch instance from AMI**
- Choose:
  - Instance type
  - Key pair
  - Security group

🎉 New EC2 is created with **same configuration**

### 🧠 Important AMI Concepts (Interview ⭐)
- ✔ AMI is a **template** for EC2
- ✔ Includes: OS, Installed software, EBS snapshots
- ✔ AMIs are **region-specific**
- ✔ Can be **copied to other regions**
- ✔ Used for **autoscaling & disaster recovery**

### 🎯 AMI in One Line (Interview)
> An AMI is a **pre-configured template** used to launch EC2 instances with the same OS, software, and settings.

---

# 📝 Quick Reference Cheat Sheet

## Storage Comparison
| Service | Type | Use Case |
|---------|------|----------|
| S3 | Object Storage | Files, Backups, Static websites |
| EBS | Block Storage | EC2 OS, Databases |
| Instance Store | Temporary Block | Cache, Temp data |

## Database Comparison
| Service | Type | Use Case |
|---------|------|----------|
| RDS | Relational (SQL) | Structured data, Transactions |
| DynamoDB | NoSQL | Real-time apps, Gaming |
| Redshift | Data Warehouse | Analytics |

## Compute Comparison
| Service | Type | Use Case |
|---------|------|----------|
| EC2 | Virtual Server | Full control, Long-running |
| Lambda | Serverless | Event-driven, Short tasks |
| ECS/EKS | Containers | Microservices |

## Global vs Regional Services
| Global | Regional |
|--------|----------|
| IAM | EC2 |
| Route 53 | VPC |
| CloudFront | RDS |
| S3 (bucket names) | EBS |

---

**End of Guide** 🎉
