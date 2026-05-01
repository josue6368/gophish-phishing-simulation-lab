# gophish-phishing-simulation-lab
Built a phishing simulation lab using GoPhish, Kali Linux, Mailpit, and a Windows 11 test endpoint. Created a simulated email campaign, landing page, and user group to track email opens, link clicks, and fake credential submissions in a controlled lab environment.

### Disclaimer
<ins>
This phishing simulation was conducted entirely within a private virtual lab environment. A local SMTP testing inbox was used to deliver emails, and only fake test credentials were submitted. No real users, external email accounts, or production systems were targeted.
</ins>

# GoPhish Phishing Simulation Lab
## Overview

This project demonstrates a phishing simulation conducted in a controlled virtual lab environment using GoPhish. The goal of this lab was to simulate a realistic phishing campaign, track user interaction, and analyze how phishing awareness and email security testing can be performed safely.

A simulated Microsoft 365 password expiration email was created and delivered to a test user through a local SMTP inbox. The campaign tracked email delivery, email opens, link clicks, and fake credential submissions.

## Lab Architecture
* Phishing Platform: GoPhish
* SMTP Testing Inbox: Mailpit
* Attacker/Operator Machine: Kali Linux VM
* Test Endpoint: Windows 11 VM
* Platform: VMware
* Network: Private NAT lab environment

## Tools and Technologies
* GoPhish
* Mailpit
* Kali Linux
* Windows 11
* VMware
* HTML email and landing page templates

## Lab Setup Summary
* Installed and launched GoPhish on Kali Linux
* Configured Mailpit as a local SMTP testing inbox
* Created a phishing email template
* Created a simulated login landing page
* Created a test user group
* Configured a local sending profile
* Launched a controlled phishing simulation campaign
* Opened the simulated email from a Windows 11 test endpoint
* Submitted fake credentials to validate campaign tracking

## Service Validation

GoPhish was launched on Kali Linux and accessed through the administrative web portal to manage templates, landing pages, user groups, and campaigns.

```
sudo ./gophish
```
The platform was successfully initialized and used throughout the phishing simulation workflow.

<br>
<img width="2194" height="1609" alt="Screenshot 2026-04-30 215316" src="https://github.com/user-attachments/assets/67e977c8-f0d4-47d6-be27-ff461aadbc31" />
<br />


## Mailpit Installation and Validation

Mailpit was installed on the Kali Linux system to provide a safe local SMTP testing inbox for the phishing simulation.

The installation was performed using the following command:
```
sudo sh < <(curl -sL https://raw.githubusercontent.com/axllent/mailpit/develop/install.sh)
```
After installation, Mailpit was started and confirmed to be listening on the expected SMTP and HTTP ports.
This allowed GoPhish to send simulation emails through a local SMTP service and provided a web inbox for safely viewing campaign emails from the Windows test system.
<br>
<img width="979" height="271" alt="Screenshot 2026-05-01 075819" src="https://github.com/user-attachments/assets/b51a4303-2084-4854-9e59-d83ef6411b0b" />
<br />

## Connectivity Validation

Before launching the phishing campaign, connectivity between the Windows 11 test endpoint and the Kali Linux system was validated to confirm access to the Mailpit web interface.

Connectivity testing included:
```
ping 192.168.88.128
```
and:
```
Test-NetConnection <KALI-IP> -Port 8025
```
The successful ping response and positive TCP connection test confirmed that the Windows VM could access Mailpit over the lab network.

This validation step helped confirm that campaign emails could be viewed from the Windows test endpoint through the Mailpit inbox.
<br>
<img width="1212" height="964" alt="Screenshot 2026-05-01 081217" src="https://github.com/user-attachments/assets/0e8323fe-8b6c-43b8-a5f1-d3a93da3bb62" />
<br />

## Email Template

A simulated Disney+ password expiration email was created to represent a common phishing lure based on urgency and account access.

Template Theme
* Password expiration warning
* Streaming/Account service interruption
* Account verification link
* Disney+ Team-themed sender
<br>
<img width="1515" height="1226" alt="Screenshot 2026-05-01 074057" src="https://github.com/user-attachments/assets/332d4a5b-8b2f-4a3b-b29d-3a5f5c8427e0" />

<br />

## Landing Page

A simulated Disney+ login page was created in GoPhish to capture user interaction during the phishing test.

The landing page was configured to capture submitted data using fake lab credentials only.

### Fake Test Credentials Used

```
testuser@lab.local
FakePassword123!
```
<br>
<img width="1255" height="1222" alt="Screenshot 2026-05-01 074905" src="https://github.com/user-attachments/assets/90324fea-591f-4c47-9288-521ac6df7b8a" />
<br />
<br>
<img width="1308" height="774" alt="Screenshot 2026-05-01 085857" src="https://github.com/user-attachments/assets/34c57af3-adf9-4116-8bb0-c2e3591e0d58" />
<br />

## Sending Profile

A local SMTP sending profile was configured in GoPhish using Mailpit.

### Sending Profile Details

```
From: disneyplus@mail.disneyplus.com
SMTP Host: 127.0.0.1:1025
```
Mailpit provided a safe local inbox for testing email delivery without sending messages to real external accounts.

<br>
<img width="1319" height="590" alt="Screenshot 2026-05-01 083644" src="https://github.com/user-attachments/assets/23c179a9-fd48-44ff-a984-6102deaa23ce" />
<br/>



## User Group

A test user group was created to represent a simulated campaign recipient.

### Test User
```
Name: Test User
Email: testuser@lab.local
Position: Lab User
```
<br>
<img width="1593" height="1005" alt="Screenshot 2026-05-01 180101" src="https://github.com/user-attachments/assets/b9203b08-52c8-41f3-b3a2-ee0ece5995b7" />
<br />

## Campaign Execution

A phishing campaign was launched using the configured email template, landing page, sending profile, and test user group.

The simulated email was opened from the Windows 11 test endpoint using the Mailpit inbox. The verification link was clicked, and fake credentials were submitted to validate tracking functionality.

<br>
<img width="1588" height="874" alt="Screenshot 2026-05-01 180422" src="https://github.com/user-attachments/assets/97763f5a-2941-4a27-a8c4-75c5175668be" />

<br>
<img width="1322" height="853" alt="Screenshot 2026-05-01 083701" src="https://github.com/user-attachments/assets/afa4220a-a701-4681-8057-7fe7b42df824" />
<br />

<img width="1593" height="985" alt="Screenshot 2026-05-01 180553" src="https://github.com/user-attachments/assets/3e2e7ec9-389d-4ce7-967d-0641ae5a6703" />

## Campaign Results

GoPhish successfully tracked the following campaign events:

* Email sent
* Email opened
* Link clicked
* Submitted data

These results demonstrate how phishing simulation platforms can measure user interaction and support security awareness training.

<br>
<img width="1569" height="1385" alt="Screenshot 2026-05-01 180820" src="https://github.com/user-attachments/assets/c55db339-1427-4391-88ac-841d16c70c57" />
<br />

<img width="1295" height="1193" alt="Screenshot 2026-05-01 180906" src="https://github.com/user-attachments/assets/b0408777-4d63-4f33-8be9-5e407a825026" />
<br />

## Security Analysis

The simulated campaign demonstrated common phishing characteristics, including:

* Urgency-based messaging
* Account access pressure
* Credential harvesting attempt
* Use of a familiar streaming service theme

These indicators are commonly seen in real-world phishing attempts and highlight the importance of user awareness, email security controls, and incident response processes.

## Defensive Recommendations for a Business Environment

Based on this simulation, recommended defenses include:

* Conduct recurring phishing awareness training
* Teach users to inspect sender addresses and URLs
* Implement multi-factor authentication
* Use email security gateways and filtering controls
* Monitor for suspicious login attempts after credential submission
* Establish clear reporting procedures for suspected phishing emails

## Skills Demonstrated
* Phishing campaign simulation
* Social engineering awareness
* Email security testing
* GoPhish configuration
* SMTP lab setup using Mailpit
* Landing page and email template creation
* Campaign tracking and results analysis
* Security awareness recommendations

## Key Takeaways

This project reinforced how phishing simulations can be used to safely evaluate user behavior, identify awareness gaps, and improve organizational security training.

By conducting the simulation in a controlled lab environment, this project demonstrated the full phishing campaign lifecycle without targeting real users or external systems.

### Author
josue6368  
Cybersecurity Analyst | IT Professional

