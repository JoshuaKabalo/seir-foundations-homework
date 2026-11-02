\# SEIR Foundations — Module 1, Lab 0

\## Your First EC2 Deployment



\### 1. Lab Overview



\*\*Purpose:\*\* Learn how to launch, access, monitor, and terminate an Amazon EC2 instance using a reusable launch template.



\*\*Learning Objectives:\*\*

\- Launch three separate Amazon EC2 instances.

\- Connect to each instance using SSH.

\- Understand basic Linux system metrics.

\- Document deployment evidence in GitHub.

\- Terminate unused instances while preserving the launch template.



\*\*Technologies Used:\*\*

\- Amazon Web Services (AWS)

\- Amazon EC2

\- Amazon Linux 2023

\- EC2 Launch Templates

\- Bash User Data

\- SSH and Git Bash

\- Git and GitHub



\### 2. Deployment Configuration



| Configuration | Value |

|---|---|

| AWS Region | us-east-1 |

| Operating System | Amazon Linux 2023 |

| Architecture | x86\_64 |

| Instance Type | t3.micro |

| Launch Template | seir-lab0-ec2-template |

| SSH Key Pair | seir-lab0-key |

| SSH Username | ec2-user |

| SSH Port | TCP 22 |

| Security Group | seir-lab0-sg |

| User Data | Instructor-provided SEIR dashboard script |



\*\*Launch Template:\*\* A reusable configuration that defines how an EC2 instance should be launched.



\*\*SSH Authentication:\*\* Public-key authentication allows secure access to the server from my local Windows computer.



\*\*Security Group:\*\* A virtual firewall controlling access to my EC2 instance. The intended SSH configuration restricts port 22 to my authorized public IP address.



\### 3. Deployment Evidence



| Deployment | Public IPv4 Address | Connection Method | Screenshot | Terminated? |

|---|---|---|---|---|

| 1 | 54.147.27.218 | Git Bash SSH | \[deployment-1.png](screenshots/deployment-1.png) | Yes |

| 2 | Pending | Pending | Pending | Pending |

| 3 | Pending | Pending | Pending | Pending |



\#### Deployment 1



\*\*Instance ID:\*\* `i-09a9bf781a4927959`  

\*\*Instance Type:\*\* `t3.micro`  

\*\*Availability Zone:\*\* `us-east-1b`



I launched an Amazon Linux 2023 EC2 instance using my saved launch template. I connected through Git Bash using SSH and successfully accessed the SEIR Foundations dashboard.



The dashboard appeared automatically after login. I captured the required screenshot, uploaded it to GitHub, and terminated the instance.



\#### Deployment 2



\*To be completed after the second deployment.\*



\#### Deployment 3



\*To be completed after the third deployment.\*



\### 4. System Metrics



The following metrics were recorded during Deployment 1.



| Metric | Observed Value |

|---|---|

| CPU | Approximately 0% busy |

| vCPUs | 2 |

| Memory | 179 MiB used / 913 MiB total |

| Root Disk | 1.7 GiB used / 8.0 GiB total |

| Disk Usage | 21% |

| Uptime | Approximately 12 minutes |

| Load Average | 0.03, 0.03, 0.03 |



\*\*CPU and vCPUs:\*\* CPU utilization indicates how busy the processor is. vCPUs represent the virtual processing resources allocated to the instance.



\*\*Memory:\*\* RAM used by the operating system and running processes.



\*\*Disk Usage:\*\* Storage space consumed on the instance's filesystem.



\*\*Uptime:\*\* How long the operating system has been running.



\*\*Load Average:\*\* The average system workload over 1, 5, and 15 minutes.



\### 5. Troubleshooting



\#### Problem 1 — SSH Key File Location



I initially had difficulty locating my downloaded SSH private key because I was using an incorrect file path.



\*\*Diagnosis:\*\* Git Bash returned a file-not-found error.



\*\*Resolution:\*\* I located the key in `/c/downloads` and ran:



```bash

ls -l seir-lab0-key.pem

chmod 400 seir-lab0-key.pem

```



\*\*Lesson:\*\* Confirm the current directory and file location before executing commands.



\#### Problem 2 — First SSH Connection



During my first connection, SSH asked whether I trusted the server's host key.



After entering the full response `yes`, the host key was saved locally and the connection succeeded.



\*\*Lesson:\*\* SSH uses host keys to help verify server identity. Host fingerprints should be checked against a trusted source before acceptance.



\#### Problem 3 — Screenshot Organization



I initially had difficulty finding the correct folder for my screenshot.



\*\*Resolution:\*\* I saved the image as `deployment-1.png` inside `module1/lab0\_basics/screenshots/` and verified it using `ls`.



\*\*Lesson:\*\* Proper filenames and folder organization are important for reproducible documentation and assignment evidence.



\### 6. Lessons Learned



\*\*What I understood:\*\*

\- The difference between an EC2 instance and a launch template.

\- How to access a remote Linux server using SSH.

\- How public IPv4 addresses identify internet-reachable endpoints.

\- How User Data configures a server during startup.

\- How to interpret basic system metrics.

\- How to save, commit, and push deployment evidence to GitHub.



\*\*What became easier through repetition:\*\*



\*To be completed after Deployments 2 and 3.\*



\*\*What I would do differently:\*\*



I would organize and verify my SSH key location before attempting to connect, and prepare my screenshot directory before launching an instance.



\*Additional reflections will be added after the remaining deployments.\*



\### 7. Security and Cost Management



\*\*SSH Key Handling:\*\* Private SSH keys should remain on my local computer and never be committed to GitHub. I used `chmod 400` to restrict access to my key file.



\*\*Security Groups:\*\* SSH access should be limited to trusted IP addresses rather than unnecessarily allowing the entire internet.



\*\*EC2 Termination:\*\* Deployment 1 was terminated after its evidence was collected.



\*\*Resource Cleanup:\*\* I retained the launch template for reuse. EBS volume and Elastic IP cleanup verification remains to be documented.



\*\*AWS Costs:\*\* A launch template does not incur EC2 compute charges simply by existing. Running instances, storage, and public IPv4 usage may incur charges depending on account benefits and usage.



\### 8. Future Learning Notes



This section will be expanded throughout SEIR Foundations.



\#### Linux Commands to Practice



\- `pwd` — Display the current directory

\- `ls` — List files and folders

\- `cd` — Change directories

\- `mkdir` — Create directories

\- `chmod` — Modify file permissions

\- `cat` — Display file contents

\- `ssh` — Connect to a remote system

\- `find` — Locate files and directories



\#### EC2 Concepts to Revisit



\- AMIs and instance types

\- Launch templates and versioning

\- Security groups and VPC networking

\- Public versus private IP addresses

\- EC2 instance lifecycle

\- User Data and cloud-init



\#### Questions for Future Lessons



\- How does SSH authentication work internally?

\- How does AWS assign public and private IP addresses?

\- What happens when an EC2 instance fails a status check?

\- How can I troubleshoot a failed User Data script?

\- How does AWS calculate EC2 charges?



\#### Ideas for Future Automation



\- Provision EC2 infrastructure using Terraform.

\- Automate configuration using Bash scripts.

\- Implement automated infrastructure testing.

\- Monitor EC2 resources using Amazon CloudWatch.

\- Use CI/CD pipelines to deploy infrastructure changes.



\---



\*\*Lab Status:\*\* In Progress — Deployment 1 of 3 completed.

