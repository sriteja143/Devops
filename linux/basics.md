# Linux Commands Guide for Beginners

## Introduction

Linux is the most commonly used operating system for servers, cloud platforms, Docker containers, and Kubernetes environments.

As a Java/Spring Boot developer, understanding Linux commands is essential for:

* Deploying applications
* Monitoring logs
* Managing files
* Troubleshooting production issues
* Working with AWS EC2 instances

---

# 1. Basic Commands

## pwd

Displays the current working directory.

```bash
pwd
```

Output:

```bash
/home/ec2-user
```

---

## ls

Lists files and directories.

```bash
ls
```

Example:

```bash
application.jar
logs
config
```

### Useful Options

```bash
ls -a
```

Shows hidden files.

```bash
ls -la
```

Shows detailed file information.

---

## cd

Changes the current directory.

```bash
cd logs
```

Move to logs directory.

```bash
cd ..
```

Move one directory up.

---

# 2. Creating Files and Directories

## touch

Creates an empty file.

```bash
touch test.txt
```

Verify:

```bash
ls
```

Output:

```bash
test.txt
```

---

## mkdir

Creates a directory.

```bash
mkdir reports
```

Create nested directories:

```bash
mkdir -p parent/child/grandchild
```

---

## cat

Displays file contents.

```bash
cat test.txt
```

Create a file with content:

```bash
cat > notes.txt
```

Type:

```text
Hello Linux
```

Press:

```text
CTRL + D
```

Save and exit.

---

## nano

Simple text editor.

```bash
nano test.txt
```

Save:

```text
CTRL + O
```

Exit:

```text
CTRL + X
```

---

## vi / vim

Most widely used Linux editor.

```bash
vim application.properties
```

### Vim Basics

Enter edit mode:

```text
i
```

Save:

```text
ESC :w
```

Save and Exit:

```text
ESC :wq
```

Exit without saving:

```text
ESC :q!
```

---

# 3. File Management

## cp

Copy files.

```bash
cp file1.txt file2.txt
```

Copy directory:

```bash
cp -r sourceDir destinationDir
```

---

## mv

Move or rename files.

Rename:

```bash
mv old.txt new.txt
```

Move:

```bash
mv file.txt /tmp/
```

---

## rm

Delete a file.

```bash
rm file.txt
```

---

## rm -rf

Delete directory and contents.

```bash
rm -rf logs
```

⚠️ Warning: This permanently removes files.

---

## tree

Display directory structure.

```bash
tree
```

Example:

```text
.
├── logs
├── config
└── app.jar
```

---

# 4. Searching and Viewing Files

## grep

Search text inside files.

```bash
grep ERROR application.log
```

Output:

```text
ERROR Database connection failed
```

Ignore case:

```bash
grep -i error application.log
```

---

## less

View large files page by page.

```bash
less application.log
```

Exit:

```text
q
```

---

## head

View first 10 lines.

```bash
head application.log
```

View first 20 lines:

```bash
head -20 application.log
```

---

## tail

View last 10 lines.

```bash
tail application.log
```

View last 50 lines:

```bash
tail -50 application.log
```

Real-time log monitoring:

```bash
tail -f application.log
```

---

## sort

Sort file content.

```bash
sort names.txt
```

Numeric sort:

```bash
sort -n numbers.txt
```

---

# 5. System Information

## hostname

Display server name.

```bash
hostname
```

Example:

```text
ip-10-0-0-12
```

---

## ifconfig

Display network information.

```bash
ifconfig
```

Modern Linux:

```bash
ip addr
```

---

## df -h

Check disk usage.

```bash
df -h
```

Output:

```text
Filesystem Size Used Avail Use%
/dev/xvda1 20G 10G 10G 50%
```

---

## Memory Information

```bash
cat /proc/meminfo
```

Useful alternative:

```bash
free -m
```

---

## CPU Information

```bash
cat /proc/cpuinfo
```

Count CPUs:

```bash
nproc
```

---

## Operating System Version

```bash
cat /etc/os-release
```

Output:

```text
NAME="Amazon Linux"
VERSION="2023"
```

---

# 6. Package Management

## Install Package

```bash
sudo yum install git
```

Install Apache:

```bash
sudo yum install httpd
```

---

## Update Packages

```bash
sudo yum update
```

---

## Remove Package

```bash
sudo yum remove httpd
```

---

## List Installed Packages

```bash
yum list installed
```

---

# 7. Service Management

Start service:

```bash
sudo service httpd start
```

Stop service:

```bash
sudo service httpd stop
```

Restart service:

```bash
sudo service httpd restart
```

Check status:

```bash
sudo service httpd status
```

Modern Linux:

```bash
systemctl start httpd
systemctl stop httpd
systemctl restart httpd
systemctl status httpd
```

---

# 8. User Utilities

## whoami

Shows current user.

```bash
whoami
```

Output:

```text
ec2-user
```

---

## sudo

Run commands with administrator privileges.

```bash
sudo yum install git
```

---

## which

Locate executable path.

```bash
which java
```

Output:

```text
/usr/bin/java
```

---

## find

Find files.

Find all log files:

```bash
find . -name "*.log"
```

Find directories:

```bash
find . -type d
```

Find files:

```bash
find . -type f
```

---

## wget

Download files from internet.

```bash
wget https://example.com/file.zip
```

---

# 9. File Permissions

Linux permissions:

```text
r = Read
w = Write
x = Execute
```

Example:

```text
-rwxr-xr-x
```

---

## chmod

Change permissions.

```bash
chmod 755 script.sh
```

Explanation:

```text
Owner  : rwx
Group  : r-x
Others : r-x
```

Make executable:

```bash
chmod +x script.sh
```

---

## chown

Change owner.

```bash
sudo chown ec2-user file.txt
```

---

## chgrp

Change group.

```bash
sudo chgrp developers file.txt
```

---

# 10. Archiving and Compression

## tar

Create archive.

```bash
tar -cvf logs.tar logs/
```

Extract archive:

```bash
tar -xvf logs.tar
```

---

## gzip

Compress file.

```bash
gzip logs.tar
```

Result:

```text
logs.tar.gz
```

---

## gunzip

Uncompress file.

```bash
gunzip logs.tar.gz
```

---

# 11. User and Group Management

## gpasswd

Add user to group.

```bash
sudo gpasswd -a teja developers
```

Remove user:

```bash
sudo gpasswd -d teja developers
```

---

# 12. Links

## Soft Link

Like a shortcut.

```bash
ln -s original.txt shortcut.txt
```

---

## Hard Link

Creates another reference to same file.

```bash
ln original.txt backup.txt
```

---

# 13. SSH Configuration

Edit SSH settings.

```bash
sudo vi /etc/ssh/sshd_config
```

Reload configuration:

```bash
sudo service sshd reload
```

---

# 14. Linux Commands Used Daily by Java Developers

## Log Analysis

```bash
tail -f application.log
grep ERROR application.log
grep Exception application.log
```

---

## Disk Usage

```bash
df -h
```

---

## Search Files

```bash
find . -name "*.log"
```

---

## Check Running Application

```bash
ps -ef | grep java
```

---

## Check Port Usage

```bash
netstat -tulpn
```

or

```bash
ss -tulpn
```

---

## Kill Process

```bash
kill -9 PID
```

Example:

```bash
kill -9 12345
```

---

# Quick Reference Cheat Sheet

```bash
pwd
ls -la
cd
touch
mkdir
cat
vim
cp
mv
rm
grep
find
head
tail -f
df -h
free -m
whoami
sudo
chmod
chown
tar
gzip
gunzip
wget
```

## Conclusion

For Java/Spring Boot developers, the most important Linux commands are:

```bash
tail -f application.log
grep ERROR application.log
find . -name "*.log"
df -h
free -m
ps -ef | grep java
chmod +x script.sh
sudo
```

Mastering these commands will help you troubleshoot production issues, manage servers, and work efficiently in cloud environments such as AWS EC2, Docker, and Kubernetes.
