# SEIR Foundations — Module 1, Lesson 2
## Slack Alerting — Homework Notes and Experiment Results

### Overview

For this assignment, I worked with the Balerica AI Slack notification agent running on an AWS EC2 instance. The objective was to understand how Python scripts can monitor system conditions, classify events by severity, and send notifications to Slack.

I completed seven homework scripts covering alert delivery, severity filtering, server time, disk usage, CPU load, simulated banking incidents, and a combined monitoring report.

After running the scripts, I completed three additional experiments to test how configuration changes affect alert delivery and monitoring behavior.

---

### Homework 2 — Severity Tour

**My Prediction and Reasoning**

I predicted that all four alerts would be delivered to Slack because my `.env` configuration had `SLACK_ALERT_SEVERITY=INFO`.

INFO is the lowest severity level, so WARNING, ERROR, and CRITICAL also meet the minimum threshold.

The Python script uses a `for` loop to go through the severity list and call `send_alert()` separately for each level.

I had also successfully tested the connection between my EC2 instance and Slack beforehand, so I expected all four alerts to reach the channel.

**Actual Result**

All four alerts — INFO, WARNING, ERROR, and CRITICAL — were successfully delivered to `#balerica-alerts`, confirming my prediction.

**What I Learned**

Severity thresholds determine which notifications are allowed through. Setting a lower threshold increases visibility, while setting a higher threshold helps reduce unnecessary alerts.

---

### Homework 3 — Server Time

**Question:** How many hours apart are server time and your wall clock?

**My Answer**

The time difference between my server time and my wall clock was five hours.

My EC2 script reports time in Coordinated Universal Time (UTC), while my local time zone was Eastern Standard Time (EST), which is UTC−5.

When I ran the script, the server reported November 12, 2026, at 01:00:47 UTC. At the same moment, my local clock showed November 11, 2026, at 8:00:47 PM EST.

**What I Learned**

UTC provides a consistent time reference for servers and applications operating across different regions. This is useful when analyzing logs, troubleshooting incidents, and coordinating engineering teams in different time zones.

---

### Homework 4 — Disk Watch

**Question:** Why is a quiet INFO alert good design rather than a failure?

**My Answer**

There are three main reasons:

1. **Normal conditions shouldn't trigger urgent responses.** Healthy disk usage doesn't require an engineer to intervene.

2. **Alert fatigue is a real operational problem.** Too many routine notifications can make important alerts easier to miss.

3. **Severity filtering reduces noise.** In production, teams may filter INFO notifications while preserving WARNING, ERROR, and CRITICAL alerts.

**Actual Result**

My EC2 instance reported 25.3% disk usage, and the monitoring script correctly selected INFO severity because the usage was below the 75% WARNING threshold.

The terminal confirmed that the message was delivered.

**What I Learned**

Monitoring should help engineers identify conditions that require attention without overwhelming them with notifications about normal system activity.

---

### Homework 5 — CPU Load Check

**Question:** What would make the CPU load average spike on the Balerica bank?

**My Answer**

The load average on the Balerica bank could spike for several reasons.

For example, if the bank suddenly receives a large number of transactions, the server might struggle to process all the API requests at once.

Resource-intensive COBOL programs could also increase demand on the CPUs. An inefficient Python script or an infinite loop could consume significant processing resources.

Heavy disk activity could also increase the system load average because processes may have to wait for disk operations to finish.

**Actual Result**

My EC2 instance reported the following load averages:

| Measurement | Value |
|---|---|
| 1-minute load | 0.00 |
| 5-minute load | 0.00 |
| 15-minute load | 0.00 |
| Logical CPUs | 2 |
| Selected severity | INFO |

The script correctly classified the load as INFO because the five-minute load average was below the number of available logical CPUs.

**What I Learned**

System load averages help engineers understand how much work a Linux server is handling. High load can indicate CPU contention or processes waiting on certain I/O operations, so it should be investigated alongside other system metrics.

---

### Homework 6 — Incident Drill

**Question:** Which fake incident deserves to wake a human at 3 AM, and why?

**My Answer**

I believe the CRITICAL incident where the Balerica bank's ledger file becomes unreachable deserves to wake an engineer at 3 AM.

My reasoning is that the ledger is important for the bank's operations because it contains account information needed by the banking application.

If the system cannot access the ledger, it could prevent customers from checking their accounts or processing transactions.

This is a serious issue because it could disrupt banking services and potentially affect customers financially.

Unlike an INFO alert about a successful backup, this problem requires immediate investigation rather than waiting until the morning.

**Actual Result**

I ran the incident drill three times:

| Run | Incident ID | Severity | Simulated event |
|---|---|---|---|
| 1 | DRILL-2441 | INFO | Nightly ledger backup completed successfully |
| 2 | DRILL-6702 | CRITICAL | Ledger file unreachable |
| 3 | DRILL-6928 | CRITICAL | Ledger file unreachable |

All three alerts were successfully delivered according to the terminal output.

**What I Learned**

Not all incidents require the same response. Engineers need to consider severity, customer impact, service availability, and urgency when deciding whether immediate intervention is necessary.

All incidents in this exercise were synthetic and did not represent actual banking failures.

---

## Configuration Experiments

### Experiment 1 — Severity Filtering

**Prediction and Reasoning**

My initial prediction was two alerts. After reviewing the severity ordering, I corrected my expectation to one CRITICAL alert.

Since `SLACK_ALERT_SEVERITY=CRITICAL` sets the highest severity as the minimum threshold, INFO, WARNING, and ERROR should be filtered out.

**Actual Result**

The script produced the following results:

| Severity | Result |
|---|---|
| INFO | Skipped |
| WARNING | Skipped |
| ERROR | Skipped |
| CRITICAL | Delivered |

Only one CRITICAL alert was delivered to Slack.

**What I Learned**

The configured severity threshold acts as the minimum level required for alert delivery.

When the threshold is CRITICAL, all lower-severity notifications are suppressed, allowing engineers to focus on the highest-priority events.

---

### Experiment 2 — Slack Alert Kill Switch

**Question:** What happened when alerts were disabled, and why is a kill switch useful during maintenance?

**My Answer**

When I set `SLACK_ALERTS_ENABLED=false` and ran Homework 1 again, the terminal displayed "Skipped" instead of delivering an alert.

This happened because the Slack notification agent checks whether alerts are enabled before attempting to send a message.

A kill switch is useful during scheduled maintenance because engineers can temporarily suppress unnecessary notifications while performing planned work.

This helps reduce alert fatigue without changing the Python scripts.

**Actual Result**

The terminal confirmed that the alert was skipped.

**What I Learned**

Configuration settings can control application behavior without requiring changes to the application code. In production, disabling alerts should be managed carefully so critical incidents are not missed.

---

### Experiment 3 — Disk Monitoring Threshold

**My Observation**

I changed the WARNING threshold in `hw4_disk_watch.py` from 75% to 20%.

When I reran the script, my EC2 instance reported 25.3% disk usage, but the alert severity changed from INFO to WARNING.

| Measurement | Original configuration | Modified configuration |
|---|---|---|
| Disk usage | 25.3% | 25.3% |
| WARNING threshold | 75% | 20% |
| Selected severity | INFO | WARNING |

**What I Learned**

Monitoring thresholds determine how a system classifies its measurements.

Even though my disk usage stayed the same, changing the threshold caused the monitoring agent to generate a higher-severity alert.

This showed me that monitoring behavior depends not only on the system's actual condition but also on the rules defined by the engineer.

After completing the experiment, I restored the WARNING threshold to 75%.

---

## Final Configuration Verification

After completing the experiments, I restored the alert configuration:

```dotenv
SLACK_ALERT_SEVERITY=INFO
SLACK_ALERTS_ENABLED=true
```

I also restored the original disk-monitoring thresholds:

- WARNING: Disk usage of 75% or higher
- ERROR: Disk usage of 90% or higher

This ensured that the environment was returned to its intended homework configuration.

---

## Final Reflection

This assignment helped me better understand how monitoring and alerting work in a cloud environment.

Instead of only sending messages to Slack, I learned how Python scripts can collect system information, evaluate conditions, assign severity levels, and decide whether a notification should be delivered.

The most important lesson for me was understanding that **a monitoring system should provide useful information without creating unnecessary noise**.

I also learned how configuration changes can affect system behavior, why UTC timestamps matter, and how engineers prioritize incidents based on their potential impact.

These exercises gave me practical experience with concepts I can build on as I continue learning cloud engineering, automation, and security operations.