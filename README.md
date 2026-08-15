# 🛡️ Splunk Email Security & Threat Monitoring Lab

## 🎯 Project Objective
The goal of this lab is to monitor enterprise email gateway traffic and identify potential security threats, such as malicious attachments and phishing attempts, using Splunk SIEM. This project demonstrates hands-on experience in log analysis, threat hunting, and SOC dashboard creation.

## 🛠️ Tools & Technologies Used
* **SIEM:** Splunk Enterprise
* **OS:** Kali Linux 
* **Key Skills:** Log Analysis, Email Security, Threat Hunting, File Hash Tracking, SPL

## 📂 Project Workflow
1. **Data Ingestion:** Ingested custom email gateway logs (`email_logs`) into Splunk to analyze incoming mail traffic.
2. **Traffic Analysis:** Created visual dashboards to monitor the status of emails (Delivered, Dropped, Quarantined) and identified the most active email senders.
3. **Threat Hunting (SPL):** Investigated suspicious emails containing potentially malicious attachments (`.vbs`, `.exe`, `.docm`). 
4. **Incident Reporting:** Extracted critical fields including Sender, Recipient, Subject, Attachment Name, and File Hash to build a comprehensive incident report for the SOC team.

## 💻 Key SPL Queries Used

**1. Monitoring Email Gateway Traffic Status (Bar Chart):**
`source="*email_logs*" | stats count by Action`
*Purpose: To visualize the overall disposition of emails (e.g., how many were delivered vs. dropped).*

**2. Identifying Top Email Senders (Pie Chart):**
`source="*email_logs*" | stats count by Sender | sort - count`
*Purpose: To track which domains or addresses are sending the highest volume of emails, helping identify potential spam or phishing campaigns.*

**3. Malicious Attachment & File Hash Report (Incident Table):**
`source="*email_logs*" (Attachment_Name="*.docm" OR Attachment_Name="*.exe" OR Attachment_Name="*.vbs") | table _time, Sender, Recipient, Subject, Attachment_Name, File_Hash, Action`
*Purpose: To hunt for highly suspicious file extensions bypassing the gateway and extract their file hashes for further malware analysis.*

## 📸 Dashboard & Investigation Previews

### 1. Email Gateway Traffic & Top Senders

### 2. Malicious Attachment & File Hash Report

## 🚀 Conclusion
This hands-on project showcases the ability to actively monitor an email gateway, track malicious payloads, and build actionable reports in Splunk, simulating real-world Tier 1 SOC Analyst responsibilities.
