# Azure Honeypot & SIEM Lab

## Objective
In this solo project, I deployed a Windows 10 honeypot in Azure to monitor and analyze unauthorized RDP login attempts. My goal was to capture attack activity, enrich the data with geographic context, and visualize patterns of malicious behavior using Microsoft Sentinel. This project gave me hands-on experience with cloud security, SIEM operations, and threat detection.

---

## What I Did

**Azure VM Deployment and Configuration**  
I created a Windows 10 virtual machine in Azure and configured its Network Security Group to allow all inbound traffic. I also disabled the Windows Firewall on the VM to make it an open honeypot for testing attack activity.

---

**Capturing Attack Activity**  
I simulated attack activity by attempting multiple failed logins with a test username. These attempts were recorded in the Windows Security logs.  

**Screenshot 1:**  
![Event Viewer Logs](VM.PNG)

---

**Inspecting Access Control Rules**  
I reviewed the inbound and outbound rules applied to the VM via Network Security Groups to confirm which traffic was allowed.

**Screenshot 2:**  
![Access Control Lists]([Access control lists.PNG](https://github.com/ZOrroryan/Azure-Honeypot-SIEM-Lab/commit/8e52d81f663a8c50b8b25e45112d735f4039ab86#diff-e27572e9922ea62d2085e10592d26a325935766e00bdf4295ffb32b75023690f))

---

**Querying Logs in Sentinel**  
Once logs were centralized in the Log Analytics Workspace via Microsoft Sentinel, I ran KQL queries to analyze failed login attempts.  

**Example Query 1:**  
```kql
SecurityEvent
| where EventID == '4625'


