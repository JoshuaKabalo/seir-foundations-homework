\# Module 1 — Lesson 2: Slack Alerting and System Monitoring



\*\*SEIR Foundations | AWS EC2 • Python • Linux • Slack\*\*



\## Project Overview



This lab focuses on building and testing a basic monitoring and alerting workflow using Python scripts running on an AWS EC2 instance.



The objective was to understand how infrastructure monitoring works, how alerts are classified by severity, and how engineers can use Slack notifications to respond to operational issues.



I completed seven homework exercises and three additional experiments using the Balerica Bank training environment.



The exercises covered system information, disk utilization, CPU load, severity filtering, simulated incidents, and automated monitoring reports.



> \*\*Lab environment:\*\* This project uses a simulated banking application for educational purposes. The incident scenarios and alerts do not represent actual production banking failures.



\## Technologies Used



| Technology | Purpose |

|---|---|

| AWS EC2 | Hosted the Linux lab environment |

| Amazon Linux 2023 | Operating system for the EC2 instance |

| Python | Executed monitoring and alerting scripts |

| Slack Webhooks | Delivered monitoring notifications |

| Linux CLI | Ran scripts and inspected system information |

| Environment variables | Controlled alert severity and notification behavior |

| Git and GitHub | Version control and technical documentation |



\## Monitoring and Alerting Workflow



The lab used the following workflow:



```text

AWS EC2 Instance

&#x20;      |

&#x20;      v

Python Monitoring Scripts

&#x20;      |

&#x20;      v

System Metrics / Simulated Events

&#x20;      |

&#x20;      v

Severity Classification

&#x20;      |

&#x20;      v

Alert Configuration Checks

&#x20;      |

&#x20;      v

Slack Webhook

&#x20;      |

&#x20;      v

\#balerica-alerts

```



Each Python script collected a system measurement or generated a simulated event, selected an appropriate severity level, and attempted to send an alert through the configured Slack webhook.



Alert delivery depended on the configured minimum severity and whether Slack alerts were enabled.



\## Homework Exercises



\### Homework 1 — Personalized Slack Alert



\*\*Objective:\*\* Send a personalized INFO notification from the EC2 instance to Slack.



\*\*Result:\*\* Successfully delivered a personalized alert to the Slack channel.



\*\*Key takeaway:\*\* Verified that the Python script, environment configuration, and Slack webhook could communicate successfully.



\*\*Evidence:\*\*



!\[Initial Slack alerts](screenshots/slack-alerts-part1.png)



\### Homework 2 — Severity Tour



\*\*Objective:\*\* Test the four supported alert severity levels.



| Severity | Result |

|---|---|

| INFO | Delivered |

| WARNING | Delivered |

| ERROR | Delivered |

| CRITICAL | Delivered |



With `SLACK\_ALERT\_SEVERITY=INFO`, all four alerts met the minimum threshold and were delivered.



\*\*Key takeaway:\*\* Severity thresholds control which notifications are sent to the monitoring channel.



\*\*Evidence:\*\*



!\[Severity alerts part 1](screenshots/slack-alerts-part1.png)



!\[Severity alerts part 2](screenshots/slack-alerts-part2.png)



\### Homework 3 — Server Time



\*\*Objective:\*\* Compare the EC2 instance's UTC time with the local time zone.



\*\*Observed results:\*\*



| Time zone | Timestamp |

|---|---|

| UTC | November 12, 2026 — 01:00:47 |

| EST (UTC−5) | November 11, 2026 — 20:00:47 |

| Difference | 5 hours |



\*\*Key takeaway:\*\* UTC provides a consistent reference for log analysis, troubleshooting, and incident coordination across time zones.



\*\*Evidence:\*\*



!\[Server time and system monitoring alerts](screenshots/hw3-hw5-slack-alerts.png)



\### Homework 4 — Disk Watch



\*\*Objective:\*\* Measure root filesystem utilization and classify disk usage by severity.



\*\*Observed results:\*\*



| Measurement | Value |

|---|---|

| Disk usage | 25.3% |

| WARNING threshold | 75% |

| ERROR threshold | 90% |

| Selected severity | INFO |



The disk usage was below the WARNING threshold, so the script correctly classified the measurement as INFO.



\*\*Key takeaway:\*\* Monitoring thresholds should distinguish healthy conditions from problems that require intervention.



\*\*Evidence:\*\*



!\[Disk monitoring alert](screenshots/hw3-hw5-slack-alerts.png)



\### Homework 5 — CPU Load Check



\*\*Objective:\*\* Measure system load and determine whether the server was under significant resource pressure.



\*\*Observed results:\*\*



| Measurement | Value |

|---|---|

| 1-minute load | 0.00 |

| 5-minute load | 0.00 |

| 15-minute load | 0.00 |

| Logical CPUs | 2 |

| Selected severity | INFO |



The system reported minimal load during the test.



Potential causes of increased load in the training application include high transaction volume, resource-intensive processes, inefficient scripts, and blocked disk operations.



\*\*Key takeaway:\*\* Load averages help identify system pressure, but should be interpreted together with CPU and I/O metrics.



\*\*Evidence:\*\*



!\[CPU load alert](screenshots/hw3-hw5-slack-alerts.png)



\### Homework 6 — Incident Drill



\*\*Objective:\*\* Generate simulated banking incidents and determine their operational urgency.



I ran the drill three times.



| Run | Incident ID | Severity | Simulated event |

|---|---|---|---|

| 1 | DRILL-2441 | INFO | Nightly ledger backup completed successfully |

| 2 | DRILL-6702 | CRITICAL | Ledger file unreachable |

| 3 | DRILL-6928 | CRITICAL | Ledger file unreachable |



All three alerts were delivered according to the terminal output.



The CRITICAL ledger incidents would require immediate investigation in a real production environment because losing access to essential ledger information could disrupt banking services.



\*\*Key takeaway:\*\* Incident response should prioritize customer impact, service availability, and operational urgency rather than treating every notification equally.



\*\*Evidence:\*\*



!\[Simulated incident drill](screenshots/hw6-incident-drill-slack-alerts.png)



\### Homework 7 — Morning Monitoring Report



\*\*Objective:\*\* Generate a consolidated server-health report and deliver it to Slack.



The report included:



\- UTC timestamp

\- EC2 hostname

\- Python version

\- Root disk utilization

\- One-minute system load



\*\*Observed results:\*\*



| Measurement | Value |

|---|---|

| Python version | 3.9.25 |

| Disk usage | 25.3% |

| 1-minute load | 0.00 |

| Slack delivery | Successful |



\*\*Key takeaway:\*\* Combining multiple system measurements into a single report can make infrastructure monitoring more efficient and provide a useful operational overview.



\*\*Evidence:\*\*



!\[Morning monitoring report in terminal](screenshots/hw7-morning-report-terminal.png)



!\[Morning monitoring report delivered to Slack](screenshots/hw7-morning-report-slack-alert.png)



\---



\## Configuration Experiments



After completing the homework, I performed three additional experiments to understand how changes in monitoring configuration affect alert behavior.



\### Experiment 1 — Severity Filtering



I changed the minimum alert threshold to:



```dotenv

SLACK\_ALERT\_SEVERITY=CRITICAL

```



\*\*Results:\*\*



| Severity | Result |

|---|---|

| INFO | Skipped |

| WARNING | Skipped |

| ERROR | Skipped |

| CRITICAL | Delivered |



Only the CRITICAL alert was delivered.



\*\*Lesson learned:\*\* Increasing the minimum severity reduces notification volume and helps teams focus on high-priority events.



\### Experiment 2 — Alert Kill Switch



I temporarily disabled Slack notifications:



```dotenv

SLACK\_ALERTS\_ENABLED=false

```



When I reran the personalized alert script, the terminal reported that the alert was skipped.



\*\*Lesson learned:\*\* Configuration-based controls can temporarily suppress notifications during maintenance without modifying application logic.



In a production environment, disabling alerts would require appropriate safeguards to avoid missing critical incidents.



\### Experiment 3 — Disk Threshold Adjustment



I reduced the WARNING threshold from 75% to 20%.



\*\*Results:\*\*



| Measurement | Before | After |

|---|---|---|

| Disk usage | 25.3% | 25.3% |

| WARNING threshold | 75% | 20% |

| Alert severity | INFO | WARNING |



The actual disk usage did not change. However, the alert severity increased because the threshold was lowered.



\*\*Lesson learned:\*\* Alert classifications depend on monitoring rules as well as system conditions. Poorly chosen thresholds can produce unnecessary notifications.



\*\*Evidence:\*\*



!\[Disk threshold experiment](screenshots/experiment3-disk-warning-slack-alert.png)



After testing, I restored the original disk-monitoring thresholds.



\---



\## Final Configuration



The lab was returned to its intended monitoring configuration:



```dotenv

SLACK\_ALERT\_SEVERITY=INFO

SLACK\_ALERTS\_ENABLED=true

```



The disk thresholds were restored to:



\- WARNING: 75% utilization

\- ERROR: 90% utilization



Only non-sensitive configuration values are documented here. Webhook credentials and environment secrets are excluded from the repository.



\## Security Considerations



This lab reinforced several practices relevant to cloud operations and security engineering:



\- \*\*Secret management:\*\* Keep Slack webhook URLs and other credentials out of public source control.

\- \*\*Least privilege:\*\* Restrict AWS instance access to authorized users and trusted networks.

\- \*\*Monitoring integrity:\*\* Avoid disabling critical alerts without appropriate operational controls.

\- \*\*Incident prioritization:\*\* Use severity and potential service impact to guide response.

\- \*\*Auditability:\*\* Document configuration changes, observed behavior, and testing evidence.

\- \*\*Cost management:\*\* Terminate unnecessary EC2 instances and manage retained AMIs and EBS snapshots.



These are important considerations when expanding a basic monitoring exercise into a more secure and reliable cloud environment.



\## Lessons Learned



Completing this assignment helped me understand that effective monitoring involves more than sending messages to Slack.



I learned how Python scripts can collect system information, evaluate metrics, classify alerts, and control delivery based on configuration settings.



One of the most important concepts was \*\*alert fatigue\*\*. A monitoring system should provide useful information while reducing unnecessary noise so engineers can recognize urgent incidents.



I also gained practical experience interpreting Linux system metrics, working with UTC timestamps, simulating incidents, and verifying system behavior after configuration changes.



These exercises provide a foundation for further work in cloud engineering, infrastructure automation, incident response, and cloud security.



\## Additional Documentation



For detailed homework answers, technical observations, and experiment explanations, see:



\[Homework Notes and Experiment Results](homework\_notes.md)



\## Lab Status



\*\*Completed:\*\* Seven homework exercises and three configuration experiments.



\*\*Evidence:\*\* Seven screenshots documenting terminal output, Slack alerts, simulated incidents, and configuration testing.

