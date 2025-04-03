# Splunk-Demonstration
# Splunk Security Monitoring and Log Analysis

## Introduction
Splunk is a powerful platform for searching, monitoring, and analyzing machine-generated data. It is widely used in cybersecurity for real-time event detection, threat intelligence, and log management. This assessment demonstrates key functionalities of Splunk for security monitoring by tracking login attempts, monitoring file access, analyzing log files, and identifying vulnerabilities.

---

## Functionalities Demonstrated

### 1. Login Attempt Tracking
**Objective:** Monitor successful and failed login attempts to detect unauthorized access.

**Steps:**
1. Search for Windows Security Logs related to login events using Splunk.
2. Use the following query to retrieve login attempts:
   ```spl
   index=* sourcetype="WinEventLog:Security" (EventCode=4624 OR EventCode=4625)
   | eval Status=if(EventCode=4624, "Successful Login", "Failed Login")
   | table _time, Account_Name, src_ip, Status
   ```
3. Create a visualization using a timechart to observe trends in login activity.

![image](https://github.com/user-attachments/assets/9a3f66d1-2b60-4a60-8234-031887fadc3f)

---

### 2. Read/Write File Access Monitoring
**Objective:** Track file access attempts, including read and write operations.

**Steps:**
1. Enable file auditing in Windows Security settings for specific directories.
2. Use Splunk to search for file access events (EventCode 4663):
   ```spl
   index=* sourcetype="WinEventLog:Security" EventCode=4663
   | table _time, Account_Name, Object_Name, Access_Mask
   ```
3. Analyze which files are accessed and by whom.

![image](https://github.com/user-attachments/assets/4f48ee48-8de6-43ee-970a-852654ca45cd)

---

### 3. Uploading and Analyzing Log Files
**Objective:** Manually upload log files to Splunk for analysis.

**Steps:**
1. Navigate to **Settings > Add Data > Upload File** in Splunk.
2. Select a sample log file and configure the sourcetype.
3. Use Splunk queries to extract and analyze the log data.
   ```spl
   index=* sourcetype="custom_logs"
   | table _time, message, severity
   ```
4. Generate reports or dashboards for visualization.

![image](https://github.com/user-attachments/assets/61e85b13-1108-4a8e-9f4e-d871632bdd1b)



## Conclusion
This assessment demonstrated how Splunk can be used for effective security monitoring. By tracking login attempts, monitoring file access, analyzing log files, and identifying vulnerabilities, organizations can strengthen their cybersecurity posture.

Splunk's powerful search capabilities, real-time alerts, and visualizations make it a valuable tool for security professionals. Further enhancements can include setting automated alerts, integrating SIEM solutions, and performing advanced analytics.


## Contributors
- Kartik Ambupe
- Suhrud Korgaokar
- Atharv Bhosale 
