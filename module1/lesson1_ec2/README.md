**SEIR Foundations — Module 1, Lesson 1**

**Balerica Legacy Bank — EC2 Deployment Lab**

---

**1. Lab Overview**

**Purpose:** Learn how to deploy a banking application on Amazon EC2, connect through SSH, install the required software, and run a COBOL banking system with a Python FastAPI application.

**Learning Objectives:**

- Launch seven separate EC2 instances using the AWS Console.
- Complete Steps 0–4 of the Balerica Legacy Bank runbook on each instance.
- Connect to each server through Git Bash using SSH.
- Install Git and clone the SEIR Foundations repository.
- Install and run the COBOL banking application.
- Activate a Python virtual environment and start the FastAPI server.
- Understand COBOL return codes and fixed-width banking records.
- Document each deployment with screenshots and personal notes.
- Terminate unused EC2 instances after completing the exercises.

**Technologies Used:**

- Amazon Web Services (AWS)
- Amazon EC2
- Amazon Linux 2023
- Git and GitHub
- Git Bash and SSH
- GnuCOBOL
- Python
- FastAPI and Uvicorn
- Linux commands

**2. Deployment Configuration**

| Configuration | Value |
|---|---|
| AWS Region | us-east-1 |
| Operating System | Amazon Linux 2023 |
| Architecture | x86_64 |
| Instance Type | t3.micro |
| SSH Key Pair | seir-lab0-key |
| SSH Username | ec2-user |
| SSH Port | TCP 22 |
| Course Repository | BalericaAI/SEIR-Foundations |
| Banking Application | Balerica Legacy Bank |
| API Framework | FastAPI |
| Web Server | Uvicorn |
| COBOL Compiler | GnuCOBOL |

**EC2 Instance:** A virtual server running in AWS where I can install applications and execute Linux commands.

**SSH Authentication:** Allows me to connect securely to my EC2 instance from Git Bash on my Windows computer.

**COBOL:** A programming language commonly associated with older business and financial systems.

**FastAPI:** A Python framework used to build APIs that other applications can communicate with.

**3. Deployment Evidence**

Each run requires a brand-new EC2 instance. I have to complete Steps 0–4 manually, record the instance information, and take a screenshot showing the identity command and the Uvicorn startup message.

I completed the first three deployments on November 1, 2026. My plan is to complete another three on November 2 and the final deployment on November 3 before the assignment deadline.

This allows me to complete all seven runs across three separate days while following the maximum of three runs per day.

| Run | Date | Time zone | Instance ID | Boot time (UTC) | Public IPv4 DNS | Screenshot | Terminated? |
|---|---|---|---|---|---|---|---|
| 1 | 2026-11-01 | America/Toronto | i-0f3ab975037e7478b | 2026-11-02 02:13:34 | ec2-18-204-225-190.compute-1.amazonaws.com | [lab1_run1.jpg](screenshots/lab1_run1.jpg) | Yes |
| 2 | 2026-11-01 | America/Toronto | i-06ddeb2118ab43260 | 2026-11-02 03:04:04 | ec2-18-212-215-49.compute-1.amazonaws.com | [lab1_run2.jpg](screenshots/lab1_run2.jpg) | Yes |
| 3 | 2026-11-01 | America/Toronto | i-062c5efc28314067 | 2026-11-02 03:18:10 | ec2-54-160-239-62.compute-1.amazonaws.com | [lab1_run3.jpg](screenshots/lab1_run3.jpg) | Yes |
| 4 | Planned: 2026-11-02 | America/Toronto | Pending | Pending | Pending | Pending | Pending |
| 5 | Planned: 2026-11-02 | America/Toronto | Pending | Pending | Pending | Pending | Pending |
| 6 | Planned: 2026-11-02 | America/Toronto | Pending | Pending | Pending | Pending | Pending |
| 7 | Planned: 2026-11-03 | America/Toronto | Pending | Pending | Pending | Pending | Pending |

**Deployment 1**

**Instance ID:** `i-0f3ab975037e7478b`  
**Instance Type:** `t3.micro`  
**Public IPv4:** `18.204.225.190`  
**Boot Time (UTC):** `2026-11-02 02:13:34`

For my first deployment, I launched a new Amazon Linux 2023 EC2 instance and connected through Git Bash using SSH.

After connecting, I installed Git and cloned the SEIR Foundations repository. I then ran the Balerica Legacy Bank installer, which installed the required dependencies, compiled the COBOL programs, and created the bank's database.

I tested the COBOL program by looking up Alice Johnson's account. The program successfully returned her account information and balance.

After that, I activated the Python virtual environment and started the FastAPI application using Uvicorn.

The terminal displayed `Application startup complete`, confirming that the banking application had started successfully.

I captured the required screenshot showing my instance ID, boot time, and application startup message. I also completed the COBOL practice and Git cloning exercises using the same instance.

Once I finished collecting my evidence, I exited the server and terminated the EC2 instance.

**Deployment 2**

**Instance ID:** `i-06ddeb2118ab43260`  
**Instance Type:** `t3.micro`  
**Public IPv4:** `18.212.215.49`  
**Boot Time (UTC):** `2026-11-02 03:04:04`

For my second deployment, I launched another Amazon Linux 2023 EC2 instance and connected through Git Bash using SSH.

I installed Git again and cloned the SEIR Foundations repository onto the new instance. After that, I ran the Balerica Legacy Bank installer and confirmed that all nine installation stages completed successfully.

I tested Alice Johnson's account using the COBOL lookup program. The account information appeared correctly, and `echo $?` returned 0.

I then activated the Python virtual environment and ran the required identity command before starting Uvicorn.

The application started successfully, and the terminal displayed `Application startup complete`.

**Uvicorn Process ID:** `33762`

I saved the required screenshot as `lab1_run2.jpg`.

During this deployment, I was more familiar with the steps because I had already completed the first run. I didn't need to repeat the additional COBOL screenshots and Git cloning assignment, so I focused on completing Steps 0–4 correctly.

**Termination Status:** Awaiting confirmation.

**Deployment 3**

**Instance ID:** `i-062c5efc28314067`  
**Instance Type:** `t3.micro`  
**Public IPv4:** `54.160.239.62`  
**Boot Time (UTC):** `2026-11-02 03:18:10`

For my third deployment, I launched another brand-new EC2 instance and repeated the same installation process manually.

I connected through SSH, installed Git, cloned the course repository, and ran the Balerica Legacy Bank installer.

I then prepared the banking application and activated the Python virtual environment.

Before starting Uvicorn, I ran the required command to display my username, Toronto date and time, instance ID, and boot time.

The application started successfully and displayed `Application startup complete`.

**Uvicorn Process ID:** `32598`

I captured the screenshot and saved it as `lab1_run3.jpg`.

By the third deployment, I was more comfortable with the commands and the order of the steps. Repeating the process helped me become more familiar with installing the application and starting the server.

After saving my screenshot, I exited the SSH session and terminated the instance.

**Deployments 4–7**

I plan to complete Runs 4, 5, and 6 on November 2, 2026, and Run 7 on November 3, 2026, before the deadline.

Each deployment will use a separate EC2 instance. I will document the actual results and any issues I encounter.

**4. Application and System Verification**

During my first three deployments, I successfully installed and started the banking application.

| Check | Observed Result |
|---|---|
| Linux Username | ec2-user |
| Git Installation | Successful on Runs 1–3 |
| Course Repository Clone | Successful on Runs 1–3 |
| COBOL Installation | Successful on Runs 1–3 |
| Bank Accounts Exported | 3 per installation |
| Alice's Account Lookup | Successful on Runs 1–2 |
| Alice's Balance | $5,000.00 USD |
| Python Virtual Environment | Activated on Runs 1–3 |
| Run 1 Uvicorn Process ID | 34185 |
| Run 2 Uvicorn Process ID | 33762 |
| Run 3 Uvicorn Process ID | 32598 |
| FastAPI Startup | Successful on Runs 1–3 |

**COBOL Account Lookup:** I used the COBOL program to retrieve account information from the bank's ledger.

**Python Virtual Environment:** I activated the environment so the application could use its installed Python packages.

**Uvicorn:** I started the FastAPI server on port 8000 and confirmed that the application completed startup on all three instances.

**5. COBOL Practice Evidence**

During Deployment 1, I tested the four COBOL return codes required for the assignment.

| Return Code | Result | Screenshot |
|---|---|---|
| 0 | Successful account lookup | [cobol_rc0.jpg](screenshots/cobol_rc0.jpg) |
| 4 | Account not found | [cobol_rc4.jpg](screenshots/cobol_rc4.jpg) |
| 8 | Payment rejected because the amount was zero | [cobol_rc8.jpg](screenshots/cobol_rc8.jpg) |
| 12 | File error caused by running the program from the wrong directory | [cobol_rc12.jpg](screenshots/cobol_rc12.jpg) |

I also decoded Alice Johnson's fixed-width banking record using the Linux `cut -c` command.

The stored balance was `000000500000`, which represents $5,000.00 USD.

**Ledger Screenshot:** [cobol_ledger_decode.jpg](screenshots/cobol_ledger_decode.jpg)

I tested a zero-dollar transaction using the transaction ID `TXN-JMK-0001`. The bank rejected the transaction because the amount needed to be greater than zero.

I checked the payment journal and confirmed that the rejected transaction was recorded. After checking Alice's account again, her balance remained $5,000.00.

**6. GitHub Cloning Evidence**

During Run 1, I cloned my own homework repository onto the EC2 instance using Git.

I then listed the `module1` folder and confirmed that my Lab 0, Lab 0.5, and Lesson 1 folders were present.

This helped me understand that Git can be used to download repositories directly onto a remote Linux server, not just my Windows computer.

**Screenshot:** [git_clone.jpg](screenshots/git_clone.jpg)

**7. Troubleshooting and Lessons Learned**

**Problem 1 — Understanding Linux Return Codes**

During the first COBOL account lookup, I initially received return code 130 when checking the previous command.

I ran the account lookup again and immediately used `echo $?`. This time, the result was 0.

**Lesson:** I learned that `echo $?` displays the exit status of the most recently executed command, and that I need to check it immediately after running a program.

**Problem 2 — Running COBOL from the Wrong Directory**

I ran the COBOL account lookup from my home directory using its full path.

The program couldn't open `data/accounts.dat` and returned code 12.

**Lesson:** I learned that some programs depend on the current working directory to locate their files.

**What I learned:**

- How to install Git on an EC2 instance.
- How to clone a GitHub repository onto a remote server.
- How to install and execute a COBOL banking application.
- How COBOL programs communicate success and errors through return codes.
- How fixed-width records store banking information.
- How Python and FastAPI can provide a modern interface for an older banking system.
- How to activate a Python virtual environment.
- How to start an application using Uvicorn.

**What became easier:**

Since I had already completed Lab 0, connecting to my EC2 instance through SSH was more familiar.

I was also more comfortable navigating Linux directories and following the installation instructions.

The main difference this time was that I was installing and running a banking application instead of only accessing the EC2 dashboard.

During the second and third deployments, I was more familiar with the installation process. I was able to repeat the same commands on new instances and confirm that the application started successfully each time.

I also became more comfortable checking the terminal output before moving to the next step.

**What I would do differently:**

I would check each command's output before moving to the next step and make sure I understand which directory I'm working in.

Additional lessons will be documented after the remaining deployments.

**8. Security and Cost Management**

**SSH Key Handling:** I kept my private SSH key on my Windows computer and did not upload it to GitHub.

**Security Groups:** SSH access should be restricted to trusted IP addresses.

**EC2 Termination:** I terminated the first and third EC2 instances after completing the deployments and collecting my evidence. Termination of the second instance still needs to be confirmed.

**Resource Cleanup:** EBS volume and Elastic IP cleanup verification is still pending.

**AWS Costs:** Running EC2 instances, EBS storage, and public IPv4 addresses may incur charges. I will terminate each instance after finishing its required work.

**9. Future Learning Notes**

This section will be updated as I complete the remaining deployments.

**Linux Commands to Practice**

- `whoami` — Display the current user
- `pwd` — Display the current directory
- `cd` — Change directories
- `ls` — List files and folders
- `git clone` — Download a Git repository
- `sudo dnf install` — Install software packages
- `echo $?` — Display the previous command's exit code
- `cut -c` — Extract specific character positions
- `cat` — Display file contents
- `source venv/bin/activate` — Activate a Python virtual environment
- `uvicorn` — Start the FastAPI application

**Topics to Revisit**

- COBOL and legacy banking systems
- Fixed-width files and financial records
- API development with FastAPI
- Python virtual environments
- Linux return codes
- Git and remote repositories
- EC2 deployment automation
- AWS infrastructure security

**Questions for Future Labs**

- How does FastAPI communicate with the COBOL banking program?
- Why do financial institutions still use COBOL?
- What happens if the COBOL program fails while the API is running?
- How are banking transactions stored and audited?
- How would this application be deployed in a production cloud environment?

**Ideas for Future Automation**

- Automate EC2 provisioning using Terraform.
- Automate application installation using scripts.
- Monitor application performance using CloudWatch.
- Build CI/CD pipelines for application deployment.
- Explore how AI can interact with legacy banking systems through APIs.
