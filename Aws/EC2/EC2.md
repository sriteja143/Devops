# Amazon EC2 (Elastic Compute Cloud)

## What is EC2?

Amazon EC2 (Elastic Compute Cloud) is an AWS service that allows you to create and run virtual servers in the cloud.
*  EC2 is a popular AWS service that allows you to quickly launch
virtual servers, known as instances, with your required
configuration within minutes.

*  You can modify the configuration, such as CPU and RAM, even
after launching the instances, without needing to stop them.
* EC2 is widely used in companies for a variety of purposes.

### Why do we need it?

Instead of buying and maintaining physical servers, AWS provides servers on demand that can be launched within minutes.

### Example

If you want to deploy a Spring Boot application, you can launch an EC2 instance, install Java, and run your application.

---

# What is Cloud Computing?

Cloud Computing is the delivery of computing resources such as servers, storage, databases, and networking over the internet.
Cloud computing refers to the on-demand delivery of IT resources
such as compute power, storage, and applications via the internet

through a cloud services platform like AWS. It follows a pay-as-
you-go pricing model.

• Users can access these IT resources provided by a cloud provider
like AWS through a web interface.
• Key Concepts:
1. On-Demand: Instantly access the resources you need
   whenever required.
2. Scalable: Adjust the configuration (e.g., CPU, RAM) up or
   down based on your needs.
3. Pay-as-You-Go: Pay only for the resources you actually use,
   with no upfront costs.
### Why do we need it?

Organizations no longer need to purchase expensive hardware. Resources can be provisioned whenever required.

### Benefits

* On-Demand
* Scalable
* Pay-As-You-Go
* High Availability

### Example

Instead of purchasing a server for ₹1,00,000, you can rent an EC2 server and pay only for the hours used.

---

# What is an EC2 Instance?

An EC2 Instance is a virtual machine running inside AWS.

### Why do we need it?

Applications require a server to run. EC2 provides that server without requiring physical hardware.

### Example

```text
Ubuntu Server
Windows Server
Amazon Linux
Red Hat Linux
```

All of these can run as EC2 instances.

---

# EC2 High-Level Architecture

```text
Application
      |
Operating System
      |
EC2 Instance
      |
AWS Infrastructure
      |
Physical Hardware
```

### What is happening here?

AWS manages the physical servers, networking, and data centers.

You manage:

* Operating System
* Installed Software
* Applications

---

# Major Components of EC2

When launching an EC2 instance, you will commonly work with the following components.

---

## 1. AMI (Amazon Machine Image)

An AMI is a template used to create an EC2 instance.
* An AMI is an operating system image in AWS. AWS offers a
  selection of predefined operating systems for both Windows
  and Linux. You must choose an OS from AWS's provided list;
  external OS imports are not allowed.
### Why do we need it?

Instead of installing an operating system manually every time, AWS provides ready-made templates.

### Examples

```text
Ubuntu
Amazon Linux
Windows Server
Red Hat Linux
```

### Real Example

If you want a Linux server for your Spring Boot application, choose the Ubuntu AMI and AWS will create a server with Ubuntu already installed.

---

## 2. Instance Type
Here, you select the combination of CPU cores and RAM.
AWS offers optimized pairs to provide the best possible
performance. These combinations are referred to as instance
types.
Instance Type determines:

* CPU
* Memory (RAM)
* Network Performance

### Why do we need it?

Different applications require different resources.

### Example

| Instance Type | Usage                 |
| ------------- | --------------------- |
| t3.micro      | Learning & Small Apps |
| t3.small      | Development           |
| t3.medium     | Medium Applications   |
| t3.large      | Production Workloads  |

### Real Example

A simple Spring Boot application may run on a t3.micro instance, while a large e-commerce application may require larger instance types.

---

## 3. Storage (EBS)

EBS (Elastic Block Store) is storage attached to an EC2 instance.
EBS is a virtual hard disk that you attach to your instances.
You can choose the size and number of volumes you need.
EBS can store both the operating system and additional data,
such as media files and documents.
* Object Storage: Stores files like MP3s, MP4s, pictures, and
documents.
* Block Storage: Stores the operating system and databases.

### Why do we need it?

Every server needs storage for:

* Operating System
* Application Files
* Databases
* Logs

### Example

```text
EC2 Instance
      |
      +-- EBS Volume (30 GB)
```

### Real Example

When Ubuntu is installed on EC2, the operating system files are stored on EBS.

> Detailed discussion will be covered in ebs.md

---

## 4. Security Group

A Security Group acts as a virtual firewall.
Security groups manage the ports that allow traffic to and
from your instance. A port is like a door to your instance,
with a total range of 0 - 65535 available. Each port has
specific uses:
* RDP (3389): Used to access Windows servers.
*  SSH (22): Used to access Linux servers.
*  HTTP (80) and HTTPS (443): Used for web traffic.
* Other ports are available for specialized purposes, which can
be discussed in more advanced sessions.

### Why do we need it?

Without security controls, anyone on the internet could try to access your server.

### Common Ports

| Port | Purpose |
| ---- | ------- |
| 22   | SSH     |
| 80   | HTTP    |
| 443  | HTTPS   |
| 3389 | RDP     |

### Real Example

If users need to access your website, you must allow:

```text
80  -> HTTP
443 -> HTTPS
```

> Detailed discussion will be covered in security-groups.md

---

## 5. Key Pair

A Key Pair is used to securely connect to an EC2 instance.
A key pair acts as a security measure, similar to a password.
By default, you receive a .pem (Privacy-Enhanced Mail) key
file. To access a Windows instance, this .pem file must be
converted into a password, as Windows instances support
password-based access only.
### Why do we need it?

AWS uses cryptographic keys instead of simple passwords for better security.

### Example

```bash
ssh -i mykey.pem ubuntu@server-ip
```

### Real Example

The `.pem` file acts like a digital key that unlocks the server.

---

## 6. Tags

Tags are labels assigned to AWS resources.A tag is a meaningful name assigned to an EC2 instance for
identification purposes.

### Why do we need it?

Large organizations may have hundreds of servers. Tags help identify and organize resources.

### Example

```text
Name=SpringBootServer
Environment=Development
Project=Learning
```

### Real Example

When your AWS account contains 100 EC2 instances, tags help identify which server belongs to which application.

---

# EC2 Lifecycle

Every EC2 instance goes through different states.

```text
Create
   |
Pending
   |
Running
   |
Stopping
   |
Stopped
   |
Terminated
```

### Running

The server is active and accepting requests.

### Stopped

The server is powered off but can be started again.

### Terminated

The server is permanently deleted.

### Why do we need to understand this?

Different actions can only be performed in specific states.

---

# Stop vs Terminate

## Stop

### What happens?

* Instance is powered off
* Data remains
* Can be started later

### Example

You stop your development server at night to save costs.

---

## Terminate

### What happens?

* Instance is deleted
* Cannot be restarted
* Data may be lost

### Example

You terminate a temporary testing server after completing testing.

---

# Public IP vs Private IP

## Public IP

Used to access the server from the internet.

### Example

```text
52.x.x.x
```

---

## Private IP

Used for communication inside AWS networks.

### Example

```text
10.x.x.x
```

### Real Example

Users connect using the Public IP, while AWS services communicate using Private IPs.

---

# Common Use Cases

## Web Applications

Applications built using:

* Spring Boot
* Node.js
* Python
* .NET

---

## APIs

REST APIs and Microservices.

---

## Databases

Hosting:

* MySQL
* PostgreSQL
* MongoDB

---

## Development Environments

Used by developers for testing and learning.

---

## Docker Hosts

Running Docker containers and containerized applications.

---

# Typical Spring Boot Deployment

```text
User
   |
Internet
   |
EC2
   |
Java 17
   |
Spring Boot Application
```

### What is happening here?

The user sends a request through the internet. The EC2 server receives the request and forwards it to the Spring Boot application.

### Real Example

When a user opens:

https://mycompany.com/customers

the request eventually reaches a Spring Boot application running on an EC2 instance.

---

# Advanced Deployment

```text
User
   |
Load Balancer
   |
EC2
   |
Spring Boot
   |
RDS Database
```

### Why is this better?

* Better scalability
* Better reliability
* Easier maintenance

---

# Advantages of EC2

* Easy to launch
* Highly scalable
* Global availability
* Flexible configurations
* Cost effective
* Supports multiple operating systems

---

# Related AWS Services

| Service      | Purpose           |
| ------------ | ----------------- |
| EBS          | Storage           |
| S3           | Object Storage    |
| IAM          | Security          |
| VPC          | Networking        |
| RDS          | Managed Database  |
| ELB          | Load Balancer     |
| Auto Scaling | Automatic Scaling |
| CloudWatch   | Monitoring        |

These services are commonly used together with EC2 and will be covered separately.

---

# Interview Questions

## What is EC2?

EC2 (Elastic Compute Cloud) is an AWS service that provides virtual servers in the cloud.

---

## What is an EC2 Instance?

An EC2 Instance is a virtual machine running inside AWS.

---

## What are the major components required to launch an EC2 Instance?

* AMI
* Instance Type
* Storage (EBS)
* Security Group
* Key Pair
* Tags

---

## What is the difference between Stop and Terminate?

### Stop

* Can restart later
* Data remains

### Terminate

* Permanent deletion
* Cannot restart

---

# Summary

Amazon EC2 is the core compute service of AWS.

It allows users to create virtual servers on demand without managing physical hardware.

Before moving deeper into AWS, you should understand:

* EC2
* EBS
* Security Groups
* IAM
* VPC
* S3
* RDS

These services work together to build modern cloud applications.
