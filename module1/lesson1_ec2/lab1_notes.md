\*\*SEIR Foundations — Module 1, Lesson 1\*\*



\*\*Balerica Legacy Bank — Personal Lab Notes\*\*



\---



\*\*1. Deployment Notes\*\*



\*\*Run 1 — November 1, 2026\*\*



\*\*Instance ID:\*\* `i-0f3ab975037e7478b`



For my first run, I launched a new Amazon Linux 2023 EC2 instance and connected through Git Bash using SSH. I installed Git, cloned the SEIR Foundations repository, and ran the Balerica Legacy Bank installer.



I tested Alice Johnson's account using the COBOL program, activated the Python virtual environment, and started the FastAPI application using Uvicorn.



During the exercises, I initially received return code 130 when checking the previous command. I repeated the account lookup and immediately ran `echo $?`, which returned 0.



I also learned that running the COBOL program from the wrong directory can cause a file error because it cannot locate its data files.



This was my first time installing a complete banking application on an EC2 instance instead of only connecting to a server.



\*\*Exact output from Run 1:\*\*



`INFO:     Started server process \[34185]`



I saved my screenshot as `lab1\_run1.jpg` and terminated the instance after completing the COBOL and Git exercises.



\*\*Run 2 — November 1, 2026\*\*



\*\*Instance ID:\*\* `i-06ddeb2118ab43260`



For my second run, I launched another EC2 instance and repeated the installation process manually.



I installed Git, cloned the course repository, and ran the Balerica Legacy Bank installer. All nine installation stages completed successfully.



I tested Alice Johnson's account again and confirmed that the COBOL program returned exit code 0.



I then activated the Python virtual environment, ran the required identity command, and started Uvicorn.



I didn't encounter any installation errors during this deployment. The process was more familiar because I had already completed it once, and I was becoming more comfortable with the order of the commands.



\*\*Exact output from Run 2:\*\*



`INFO:     Started server process \[33762]`



I saved the evidence as `lab1\_run2.jpg`.



\*\*Run 3 — November 1, 2026\*\*



\*\*Instance ID:\*\* `i-062c5efc28314067`



For my third run, I launched another brand-new EC2 instance and repeated the same installation steps.



By this point, I was becoming more familiar with using Git Bash, cloning the repository, and installing the banking application.



I activated the Python virtual environment, ran the required identity command, and started Uvicorn successfully.



I didn't encounter any new errors during this deployment. Repeating the same process helped me understand the deployment sequence and made me more comfortable working inside a Linux server.



\*\*Exact output from Run 3:\*\*



`INFO:     Started server process \[32598]`



I saved the screenshot as `lab1\_run3.jpg`, exited the SSH session, and terminated the instance afterward.



\*\*2. COBOL Practice\*\*



\*\*Instance Used:\*\* Run 1  

\*\*Instance ID:\*\* `i-0f3ab975037e7478b`



During my first deployment, I tested the four COBOL return codes required for the assignment.



\*\*Return Code 0 — Successful Account Lookup\*\*



\*\*Command:\*\*



```bash

./cobol/bin/account\_lookup 100001

echo $?

```



\*\*Output:\*\*



```text

ACCOUNT=100001

NAME=Alice Johnson

STATUS=ACTIVE

BALANCE=5000.00

CURRENCY=USD

0

```



I successfully retrieved Alice Johnson's account information. The return code was 0, which confirmed that the program completed successfully.



\*\*Return Code 4 — Account Not Found\*\*



\*\*Command:\*\*



```bash

./cobol/bin/account\_lookup 999999

echo $?

```



\*\*Output:\*\*



```text

ERROR=ACCOUNT NOT FOUND

ACCOUNT=999999

4

```



I tried to look up an account that didn't exist. The program returned code 4 rather than crashing.



\*\*Return Code 8 — Business Rejection\*\*



\*\*Command:\*\*



```bash

./cobol/bin/payment\_post TXN-JMK-0001 100001 0 USD INV-1001

echo $?

```



\*\*Output:\*\*



```text

TXN=TXN-JMK-0001

ACCOUNT=100001

AMOUNT=0.00

CURRENCY=USD

STATUS=REJECTED

REASON=AMOUNT MUST BE GREATER THAN ZERO

8

```



I attempted to process a zero-dollar payment using my initials in the transaction ID. The program rejected it because the amount was not greater than zero.



I learned that a banking system needs to enforce business rules and reject transactions that don't meet those requirements.



\*\*Return Code 12 — Environment Failure\*\*



\*\*Command:\*\*



```bash

cd \~

/opt/balerica-bank/cobol/bin/account\_lookup 100001

echo $?

```



\*\*Output:\*\*



```text

ERROR=CANNOT OPEN data/accounts.dat

FILE-STATUS=35

12

```



I ran the COBOL program from my home directory instead of `/opt/balerica-bank`.



The program couldn't find the ledger file and returned code 12. This helped me understand why the current working directory matters when a program uses relative file paths.



\*\*3. Fixed-Width Ledger Decoding\*\*



\*\*Instance Used:\*\* Run 1  

\*\*Instance ID:\*\* `i-0f3ab975037e7478b`



I used the Linux `cut -c` command to decode the account information stored in `data/accounts.dat`.



\*\*Original ledger record:\*\*



```text

100001Alice Johnson                 ACTIVE  000000500000USD

```



\*\*Commands and Results:\*\*



| Command | Result |

|---|---|

| `cut -c 1-6 data/accounts.dat \\| head -n 1` | `100001` |

| `cut -c 7-36 data/accounts.dat \\| head -n 1` | `Alice Johnson` |

| `cut -c 37-44 data/accounts.dat \\| head -n 1` | `ACTIVE` |

| `cut -c 45-56 data/accounts.dat \\| head -n 1` | `000000500000` |

| `cut -c 57-59 data/accounts.dat \\| head -n 1` | `USD` |



\*\*Alice's decoded balance:\*\* $5,000.00 USD.



I learned that fixed-width records store information using specific character positions instead of separators such as commas.



The balance doesn't contain a visible decimal point. The last two digits represent cents.



\*\*4. Transaction Journal Verification\*\*



\*\*Transaction ID:\*\* `TXN-JMK-0001`



After attempting the zero-dollar payment, I checked the payment journal.



\*\*Command:\*\*



```bash

cat data/payments.dat

```



\*\*Output:\*\*



```text

TXN-JMK-0001        100001000000000000USDREJECTEDINV-1001

```



The journal recorded my transaction as rejected.



I then ran another account lookup:



```bash

./cobol/bin/account\_lookup 100001

```



\*\*Output:\*\*



```text

ACCOUNT=100001

NAME=Alice Johnson

STATUS=ACTIVE

BALANCE=5000.00

CURRENCY=USD

```



Alice's balance remained $5,000.00 after the rejected transaction.



This showed me that the system records rejected payment attempts without changing the account balance.



\*\*5. GitHub Cloning Practice\*\*



\*\*Instance Used:\*\* Run 1  

\*\*Instance ID:\*\* `i-0f3ab975037e7478b`



I cloned my personal homework repository onto the EC2 instance.



\*\*Command:\*\*



```bash

git clone https://github.com/JoshuaKabalo/seir-foundations-homework.git

```



After cloning, I ran:



```bash

ls seir-foundations-homework/module1

```



\*\*Output:\*\*



```text

lab0.5\_basics\_contd  lab0\_basics  lesson1\_ec2

```



This confirmed that my homework repository was successfully downloaded onto the Linux server.



I learned that I can use Git to access project files from a remote server without having to manually transfer them from my computer.



\*\*6. Mistakes I Made\*\*



\- I initially received exit code 130 when checking the previous command and needed to repeat the COBOL lookup to verify its actual return code.

\- I learned that running a COBOL executable from the wrong directory can prevent it from finding its data files.

\- During the first run, I needed more guidance to understand the order of the installation steps.



\*\*7. Commands I Now Know by Heart\*\*



\- `whoami` — Check my current Linux username.

\- `pwd` — Check my current directory.

\- `cd` — Navigate between directories.

\- `ls` — List files and folders.

\- `sudo dnf install -y git` — Install Git.

\- `git clone` — Download a repository.

\- `echo $?` — Check the previous command's exit status.

\- `cat` — Display file contents.

\- `cut -c` — Extract characters from fixed-width records.

\- `source venv/bin/activate` — Activate a Python virtual environment.

\- `uvicorn app.main:app --host 0.0.0.0 --port 8000` — Start the banking API.



\*\*8. Future Learning Notes\*\*



I still want to understand how the FastAPI application communicates with the COBOL programs and how the database stores transactions.



I also want to become more comfortable completing the installation steps without needing to look at the runbook as often.



The remaining four deployments will give me more practice with these commands. I will continue updating these notes after each run.

