# EC2 (Elastic Compute Cloud) - Linux Instance Lab

## Objective

Learn how to create, connect to, and terminate a Linux EC2 instance in AWS.

---

# Lab Setup

## Step 1: Launch a Linux EC2 Instance

Navigate to:

```text
AWS Console → EC2 → Instances → Launch Instance
```

### Instance Configuration

| Setting | Value |
|----------|---------|
| Name | MyLinux |
| AMI | Amazon Linux |
| Instance Type | t3.micro |
| Key Pair Name | test (or any preferred name) |
| Key Pair Format | .ppk |
| Security Group | Allow SSH (Port 22) |
| Storage | 8 GB |

---

## Step 2: Create a Key Pair

While launching the instance:

1. Click **Create New Key Pair**
2. Enter a key pair name

Example:

```text
test
```

3. Select:

```text
Format: .ppk
```

4. Download and save the file securely.

Example:

```text
test.ppk
```

> This key file is required to connect using PuTTY.

---

## Step 3: Configure Security Group

Allow SSH access:

| Type | Protocol | Port |
|--------|----------|------|
| SSH | TCP | 22 |

---

## Step 4: Configure Storage

Ensure storage is set to:

```text
8 GB
```

---

## Step 5: Launch Instance

Review the configuration and click:

```text
Launch Instance
```

Wait until the instance state becomes:

```text
Running
```

---

# Verify Instance Status

Navigate to:

```text
EC2 → Instances
```

Verify:

- Instance Name: MyLinux
- State: Running
- Public IPv4 Address available

---

# Connect to Linux EC2 Instance Using PuTTY

## Step 1: Install PuTTY

Download and install:

- PuTTY
- PuTTYgen (if needed)

---

## Step 2: Obtain Connection Information

1. Select the EC2 instance
2. Click **Connect**
3. Copy the connection information

Example:

```text
ec2-user@ec2-xx-xx-xx-xx.compute.amazonaws.com
```

---

## Step 3: Open PuTTY

Launch PuTTY and configure:

### Host Name

```text
ec2-user@<Public-DNS-Name>
```

Example:

```text
ec2-user@ec2-54-123-45-67.compute.amazonaws.com
```

---

### Configure Authentication

Navigate:

```text
Connection
 └── SSH
      └── Auth
```

Browse and select:

```text
test.ppk
```

under:

```text
Private key file for authentication
```

---

## Step 4: Connect

Click:

```text
Open
```

When prompted:

```text
PuTTY Security Alert
```

Click:

```text
Accept
```

You should now be connected to your Linux EC2 instance.

---

# Basic Linux Verification Commands

Verify the instance is working correctly.

### Check Current User

```bash
whoami
```

Expected Output:

```text
ec2-user
```

---

### Check Operating System

```bash
cat /etc/os-release
```

---

### Check Hostname

```bash
hostname
```

---

### Check Disk Space

```bash
df -h
```

---

### Check Memory

```bash
free -m
```

---

### Update Packages

```bash
sudo yum update -y
```

---

# Common Linux EC2 Use Cases

## 1. DevOps Tools Installation

Install and run tools such as:

- Jenkins
- Docker
- Kubernetes Components
- Ansible
- GitLab Runner
- Nexus Repository

---

## 2. Application Hosting

Host applications developed using:

- Java
- Spring Boot
- Python
- Node.js
- PHP
- Go

---

## 3. Application Testing

Used for:

- Functional Testing
- Performance Testing
- Integration Testing
- Load Testing

---

## 4. E-Commerce Platforms

Large retail and e-commerce organizations use Linux servers for:

- Product Catalog Management
- Order Processing
- Inventory Calculations
- Payment Services

---

## 5. Game Development & Hosting

Used for:

- Multiplayer Game Servers
- Matchmaking Services
- Backend APIs
- Real-Time Event Processing

---

## 6. Media Processing

Used for:

- Video Rendering
- Image Processing
- Animation Workloads
- Visual Effects (VFX)

---

## 7. Data Processing

Used for:

- Big Data Workloads
- ETL Pipelines
- Batch Processing
- Machine Learning Training

---

# Clean Up Resources

## Terminate the Instance

After completing the lab:

1. Select the EC2 instance
2. Click:

```text
Instance State → Terminate Instance
```

3. Confirm termination

---

> **Important:** Always terminate unused EC2 instances to avoid unnecessary AWS charges.

---

# Key Takeaways

- EC2 provides virtual servers in the AWS Cloud.
- Amazon Linux is a commonly used Linux AMI.
- SSH (Port 22) is required for Linux remote access.
- PuTTY uses `.ppk` key files for authentication.
- EC2 instances can be launched, managed, and terminated on demand.
- Linux EC2 instances are widely used for DevOps, application hosting, testing, gaming, media processing, and data analytics.