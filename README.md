Project 2 : SSH Brute Force Detection using Elastic SIEM
Project Overview

This project demonstrates the implementation of a real-world SOC use case by detecting SSH brute force attacks on a Linux system using Elastic SIEM. The project covers the complete incident lifecycle — from log ingestion and detection engineering to alert triage and closure.

Objective

To detect repeated failed SSH authentication attempts on a Linux host and generate actionable security alerts using Elastic SIEM, simulating a common brute force attack scenario handled by SOC analysts.

Tools & Technologies

Elastic Cloud (Elastic Security / SIEM)

Kibana

Elastic Agent

Ubuntu Linux

SSH

KQL (Kibana Query Language)

Architecture
Ubuntu Linux
   ↓
Elastic Agent
   ↓
Elastic SIEM (Kibana)
   ↓
Detection Rule
   ↓
Security Alert

Use Case Description

SSH brute force attacks involve repeated authentication attempts to gain unauthorized access to a Linux system. By monitoring system authentication logs (auth.log) and applying threshold-based detection logic, this project identifies such suspicious behavior and raises alerts for SOC investigation.

⚙️ Implementation Steps
1️⃣ SIEM Environment Setup

Deployed Elastic Cloud (Elastic for Security)

Accessed Kibana Security dashboard

2️⃣ Log Collection

Installed Elastic Agent on Ubuntu

Enabled System integration

Verified ingestion of Linux authentication logs (system.auth)

3️⃣ Attack Simulation

Simulated SSH brute force behavior by repeatedly attempting logins with invalid credentials:

ssh wronguser@localhost

4️⃣ Detection Rule Engineering

Rule Type: Threshold Rule

Index Pattern: logs-*

KQL Query:

event.dataset:system.auth AND process.name:sshd AND event.outcome:failure


Threshold: 5 events within 5 minutes

5️⃣ Rule Tuning & Troubleshooting

Initial alert did not trigger due to an excessively high threshold

Analyzed event volume and tuned threshold values

Successfully triggered alert after optimization

6️⃣ Alert Investigation & Closure

Validated SSH authentication failure events

Confirmed activity as test-generated

Closed alert as Benign / Test Activity

🚨 Detection Outcome

SSH brute force alert successfully generated

Alert validated and closed following SOC best practices

Demonstrated detection tuning and incident handling

👤 Author

Dharshan P
Aspiring SOC Analyst | Cybersecurity Enthusiast
📍 India
