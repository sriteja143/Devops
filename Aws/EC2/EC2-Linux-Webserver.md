# Linux Web Server Lab

## Objective

Learn how to configure an Amazon Linux EC2 instance as a web server using Apache HTTP Server (HTTPD).

---

# What is a Web Server?

A web server is a server that hosts and serves web content such as HTML pages, images, CSS, and JavaScript files to users over the internet using the HTTP protocol.

A web server can run on:

* Linux
* Windows

To convert a normal server into a web server, three main steps are required:

1. Install a web server package (HTTPD/Apache)
2. Create web content (HTML files)
3. Start the web server service

---

# Prerequisites

Before starting this lab, ensure:

* An Amazon Linux EC2 instance is running
* SSH access is enabled (Port 22)
* HTTP access is enabled (Port 80)
* You can connect to the instance using PuTTY or SSH

---

# Architecture

```text
User Browser
      |
      | HTTP (Port 80)
      |
      v
Amazon Linux EC2
      |
      +--> Apache HTTPD
      |
      +--> /var/www/html/index.html
```

---

# Important Security Group Configuration

To access the website from a browser, open the following ports:

| Type | Protocol | Port |
| ---- | -------- | ---- |
| SSH  | TCP      | 22   |
| HTTP | TCP      | 80   |

> If Port 80 is not open, users will not be able to access the website.

---

# Step 1: Connect to Linux Server

Connect to your EC2 instance using SSH or PuTTY.

---

# Step 2: Switch to Root User

```bash
sudo su -
```

Verify:

```bash
whoami
```

Expected Output:

```text
root
```

---

# Step 3: Update the Server

Update all installed packages:

```bash
yum update -y
```

Purpose:

* Installs latest security patches
* Updates existing packages
* Improves system stability

---

# Step 4: Install Apache HTTP Server

Install the HTTPD package:

```bash
yum install httpd -y
```

Verify installation:

```bash
rpm -qa | grep httpd
```

Expected Output:

```text
httpd
httpd-tools
```

---

# Step 5: Navigate to Web Root Directory

Move to the Apache web content directory:

```bash
cd /var/www/html
```

Verify current location:

```bash
pwd
```

Expected Output:

```text
/var/www/html
```

---

# Step 6: Create a Web Page

Create a simple HTML page:

```bash
echo "MyGoogle" > index.html
```

Verify:

```bash
cat index.html
```

Expected Output:

```text
MyGoogle
```

---

# Step 7: Verify File Creation

List files:

```bash
ls
```

Expected Output:

```text
index.html
```

---

# Step 8: Start Apache Service

Start the web server:

```bash
service httpd start
```

Alternative command:

```bash
systemctl start httpd
```

Check service status:

```bash
systemctl status httpd
```

Expected Output:

```text
active (running)
```

---

# Step 9: Enable HTTPD on Server Restart

To automatically start Apache after reboot:

```bash
systemctl enable httpd
```

Verify:

```bash
systemctl is-enabled httpd
```

Expected Output:

```text
enabled
```

---

# Step 10: Access the Website

Copy the EC2 Public IP Address.

Example:

```text
54.xx.xx.xx
```

Open a browser and navigate to:

```text
http://<Public-IP>
```

Example:

```text
http://54.xx.xx.xx
```

Expected Output:

```text
MyGoogle
```

---

# Complete Command List

```bash
sudo su -

yum update -y

yum install httpd -y

cd /var/www/html

echo "MyGoogle" > index.html

ls

service httpd start
```

---

# Useful Apache Commands

## Start Service

```bash
systemctl start httpd
```

## Stop Service

```bash
systemctl stop httpd
```

## Restart Service

```bash
systemctl restart httpd
```

## Check Status

```bash
systemctl status httpd
```

## Enable Auto Start

```bash
systemctl enable httpd
```

# Key Takeaways

* HTTPD (Apache) is one of the most widely used web servers.
* Web content is typically stored in `/var/www/html`.
* Port 80 must be open for HTTP traffic.
* The `index.html` file is the default page served by Apache.
* Apache services can be managed using `systemctl`.
* Linux web servers are commonly used for websites, APIs, enterprise applications, and DevOps environments.
