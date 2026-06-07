# EC2 Windows Lab

## Objective

In this lab, we will:

* Launch a Windows EC2 Instance
* Connect to the instance using Remote Desktop Protocol (RDP)
* Understand the purpose of each EC2 configuration
* Access a Windows Server running in AWS Cloud

---

# Prerequisites

Before starting this lab, ensure:

* AWS Account is available
* AWS Console access is available
* Basic understanding of EC2 concepts
* EC2.md has been completed

---

# Lab Architecture

```text
My Laptop
     |
Internet
     |
AWS EC2 (Windows Server 2022)
     |
Remote Desktop (RDP)
```

### What are we building?

We are creating a Windows Server in AWS and connecting to it remotely from our local machine.

---

# Step 1: Navigate to EC2 Service

1. Login to AWS Console
2. Search for **EC2**
3. Open the EC2 Dashboard
4. Click **Launch Instance**

---

# Step 2: Configure Basic Details

## Number of Instances

```text
1
```

### Why?

We only need one server for learning purposes.

---

## Name and Tags

```text
MyWindows
```

### Why?

The Name tag helps identify the instance in the AWS Console.

### Example

```text
MyWindows
SpringBootServer
DevelopmentServer
```

---

# Step 3: Select AMI

Choose:

```text
Windows Server 2022 Base
```

### What is an AMI?

AMI (Amazon Machine Image) is a template used to create an EC2 instance.

### Why?

The AMI determines which operating system will be installed on the server.

### Expected Result

AWS creates an EC2 instance with Windows Server 2022 installed.

---

# Step 4: Select Instance Type

Choose:

```text
t3.micro
```

### What is an Instance Type?

Instance Type determines:

* CPU
* Memory (RAM)
* Network Capacity

### Why?

For learning purposes, a small instance is sufficient.

### Expected Result

A low-cost Windows server suitable for practice.

---

# Step 5: Create Key Pair

Click:

```text
Create New Key Pair
```

Example:

```text
demo
```

Download:

```text
demo.pem
```

### Why?

AWS uses the key pair to securely generate the Windows Administrator password.

### Important

Store the `.pem` file safely.

Without it, you cannot retrieve the Windows password.

---

# Step 6: Configure Security Group

Allow:

```text
RDP - Port 3389
```

### What is RDP?

RDP (Remote Desktop Protocol) allows remote access to Windows machines.

### Why?

Without Port 3389, you cannot connect to the Windows server.

### Expected Result

Your laptop can establish a Remote Desktop connection to the EC2 instance.

---

# Step 7: Configure Storage

Set Storage:

```text
30 GB
```

### Why?

Storage is required for:

* Windows Operating System
* Applications
* Files
* Logs

### Expected Result

AWS creates an EBS volume attached to the instance.

---

# Step 8: Launch Instance

Click:

```text
Launch Instance
```

Then:

```text
View Instances
```

### Expected Result

Instance State:

```text
Running
```

Public IP Address should also be visible.

---

# Step 9: Connect to the Instance

Select the instance.

Click:

```text
Connect
```

Choose:

```text
RDP Client
```

---

# Step 10: Retrieve Windows Password

Click:

```text
Get Password
```

Upload:

```text
demo.pem
```

Click:

```text
Decrypt Password
```

### Why?

Windows uses a password for login.

AWS encrypts this password and allows only the key owner to decrypt it.

### Expected Result

You will receive:

```text
Username: Administrator
Password: ********
```

---

# Step 11: Download RDP File

Click:

```text
Download Remote Desktop File
```

This downloads:

```text
.rdp
```

file.

---

# Step 12: Connect Using Remote Desktop

Open the downloaded:

```text
.rdp
```

file.

Enter:

```text
Username: Administrator
Password: <Decrypted Password>
```

Click:

```text
Connect
```

If prompted:

```text
Yes
```

### Expected Result

Windows Server 2022 desktop appears.

---

# Verification

Successful lab completion means:

✅ EC2 Instance is running

✅ RDP connection is successful

✅ Windows desktop is visible

✅ Administrator access is available

---

# Troubleshooting

## Unable to Connect

Check:

```text
Security Group
```

Ensure:

```text
Port 3389
```

is allowed.

---

## Password Not Working

Verify:

```text
Correct PEM file used
```

when decrypting the password.

---

## Instance Not Reachable

Verify:

```text
Instance State = Running
```

and Public IP exists.

---

# Real World Use Cases

## DevOps Tools

Install:

* Jenkins
* TeamCity
* Build Tools

---

## Application Testing

Test applications on Windows environments.

Example:

```text
.NET Applications
Windows Services
Desktop Applications
```

---

## Enterprise Applications

Many enterprise applications require Windows Server.

---

## Gaming

High-performance game servers often run on Windows.

---

## Graphics and Rendering

Used for:

* Video Processing
* Rendering
* Visual Effects

---

# Cost Management

After completing the lab:

## Option 1: Stop Instance

```text
Can start again later
```

Good for learning environments.

---

## Option 2: Terminate Instance

```text
Permanently deletes the server
```

Use when the lab is no longer required.

---

# Key Learnings

After completing this lab, you should understand:

* How to launch a Windows EC2 Instance
* AMI selection
* Instance Types
* Key Pairs
* Security Groups
* RDP Access
* Windows Server administration basics
* Cost management using Stop and Terminate

---
