**SEIR Foundations — Module 1, Lab 0**

**Your First EC2 Deployment**

---

**1. Lab Overview**

**Purpose:** Learn how to launch, access, monitor, and terminate an Amazon EC2 instance using a reusable launch template.

**Learning Objectives:**

- Launch three separate Amazon EC2 instances.
- Connect to each instance using SSH.
- Understand basic Linux system metrics.
- Document deployment evidence in GitHub.
- Terminate unused instances while preserving the launch template.

**Technologies Used:**

- Amazon Web Services (AWS)
- Amazon EC2
- Amazon Linux 2023
- EC2 Launch Templates
- Bash User Data
- SSH and Git Bash
- Git and GitHub

**2. Deployment Configuration**

| Configuration | Value |
|---|---|
| AWS Region | us-east-1 |
| Operating System | Amazon Linux 2023 |
| Architecture | x86_64 |
| Instance Type | t3.micro |
| Launch Template | seir-lab0-ec2-template |
| SSH Key Pair | seir-lab0-key |
| SSH Username | ec2-user |
| SSH Port | TCP 22 |
| Security Group | seir-lab0-sg |
| User Data | Instructor-provided SEIR dashboard script |

**Launch Template:** A reusable configuration that defines how an EC2 instance should be launched.

**SSH Authentication:** Public-key authentication allows secure access to the server from my local Windows computer.

**Security Group:** A virtual firewall controlling access to my EC2 instance. The intended SSH configuration restricts port 22 to my authorized public IP address.

**3. Deployment Evidence**

| Deployment | Public IPv4 Address | Connection Method | Screenshot | Terminated? |
|---|---|---|---|---|
| 1 | 54.147.27.218 | Git Bash SSH | [deployment-1.png](screenshots/deployment-1.png) | Yes |
| 2 | 54.91.95.226 | Git Bash SSH | [deployment-2.png](screenshots/deployment-2.png) | Yes |
| 3 | Pending | Pending | Pending | Pending |

**Deployment 1**

**Instance ID:** `i-09a9bf781a4927959`  
**Instance Type:** `t3.micro`  
**Availability Zone:** `us-east-1b`

I launched an Amazon Linux 2023 EC2 instance using my saved launch template. I connected through Git Bash using SSH and successfully accessed the SEIR Foundations dashboard.

The dashboard appeared automatically after login. I captured the required screenshot, uploaded it to GitHub, and terminated the instance.

**Deployment 2**

**Instance ID:** `i-0f64e2f7e5f4b452a`  
**Instance Type:** `t3.micro`  
**Availability Zone:** `us-east-1b`  
**Public IPv4:** `54.91.95.226`

For my second deployment, I reused the same launch template from the first deployment instead of creating another one. I launched a new EC2 instance and used Git Bash to connect through SSH.

I initially entered the public DNS address without the SSH command, which gave me a command not found error. After correcting the command, I connected successfully and the SEIR dashboard appeared automatically.

The dashboard showed 2 vCPUs, around 0% CPU usage, 175 Mi