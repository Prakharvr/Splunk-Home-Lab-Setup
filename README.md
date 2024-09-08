# Splunk Home Lab Setup

![Splunk](https://i.pinimg.com/564x/5e/20/4b/5e204b9ede454a0e12a40c1cbe4c28ef.jpg)


## Overview
This guide will walk you through the process of setting up a Splunk Home Lab environment for practicing incident investigations, particularly focusing on brute force attack detection and analyzing logs from various services like DNS, FTP, HTTP, SSH, and more. The lab will include setting up Splunk, configuring log sources, and performing an investigation.

![Splunk Setup](https://private-user-images.githubusercontent.com/40385860/303673214-2a1f4e02-3ae9-4d47-8e09-9370548035ed.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MjU3NzcyNzYsIm5iZiI6MTcyNTc3Njk3NiwicGF0aCI6Ii80MDM4NTg2MC8zMDM2NzMyMTQtMmExZjRlMDItM2FlOS00ZDQ3LThlMDktOTM3MDU0ODAzNWVkLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNDA5MDglMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjQwOTA4VDA2MjkzNlomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWU5NWExMzYwYTE4YmFkMTIyMzg1YWE1N2M3NWRlZmE5MWY3ZDA1ZjJkNjgyZGFkNGEwZjE2OWQzYWUyOGM2MTUmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.2ueghhrXHN2rWc-7wx6QSfhDwMthQBYOK1mKECO9rtI)


---

## Prerequisites

Before you begin, ensure you have the following:

- A machine with at least **8 GB of RAM** and **20 GB of disk space**.
- An operating system like **Windows**, **Linux**, or **macOS**.
- **Splunk Free or Enterprise Trial** installer.
- Virtual machines (optional) to simulate network services (e.g., DNS, FTP, HTTP, SSH).

---

## Step 1: Download and Install Splunk

1. Visit the [Splunk Downloads page](https://www.splunk.com/en_us/download/splunk-enterprise.html).
2. Choose the appropriate installer for your operating system.
3. Follow the installation steps provided by Splunk.
   - For **Linux**, extract the tar file and run the `splunk` binary.
   - For **Windows**, follow the installation wizard.
   - For **macOS**, download and install the `.dmg` file.
4. Start Splunk using the following commands:

   - **Linux/macOS**:
     ```bash
     ./splunk start
     ```
   - **Windows**: Launch the Splunk app from the Start Menu.

5. Open a browser and navigate to `http://localhost:8000` to access Splunk.

---

## Step 2: Configure Data Inputs

To investigate various types of logs (DNS, FTP, HTTP, SSH), you will need to configure data inputs.

1. **Add data inputs:**
   - Go to **Settings > Add Data**.
   - Select **Monitor**, and choose the file or directory containing logs, or configure inputs for network-based logs.
   
2. **Enable or import logs** for DNS, FTP, HTTP, and SSH:
   - You can set up your local network services to generate these logs or use pre-existing log files.
   
3. **Simulate services** using virtual machines or Docker containers:
   - DNS, FTP, HTTP, and SSH services can be set up on VMs or Docker containers to generate traffic for investigation.
   - Use tools like **dnsmasq**, **vsftpd**, **Apache**, and **OpenSSH** for service simulation.

---

## Step 3: Investigating Brute Force Attacks

In this section, we will investigate a brute force attack. The logs we'll focus on include DNS, FTP, HTTP, and SSH logs.

### SSH Brute Force Attack

1. **SSH Logs** can reveal multiple failed login attempts in a short period, which may indicate brute force attempts.
2. Check the **/var/log/auth.log** (Linux) or **Event Viewer** (Windows) for excessive login attempts.
   
### FTP Brute Force Attack

1. **FTP Logs** will show repeated login attempts from the same IP address.
2. Review logs for `vsftpd` or other FTP services to identify brute force patterns.

### HTTP Brute Force Attack

1. HTTP brute force attacks often target login pages.
2. Check the **access logs** of your web server (e.g., Apache or Nginx) for multiple failed login attempts.

### DNS Logs

1. DNS logs can reveal abnormal query patterns, indicating possible DNS tunneling or brute force attempts to resolve domains.
2. Look at logs from **dnsmasq** or another DNS server for unusual query behavior.

---

## Step 4: Analyzing Logs in Splunk

Once the logs are ingested, you can begin analyzing them:

1. **Search Interface**: Use the search bar to look for patterns such as failed login attempts, abnormal query behavior, or unusual traffic patterns.
2. **Dashboards**: Create custom dashboards to visualize brute force attempts and other incidents.
3. **Alerts**: Set up alerts for suspicious behavior, such as excessive failed login attempts.

---

## Step 5: Report and Document Findings

After your investigation, summarize the findings in a report. Include:

- The source and nature of the attack (e.g., SSH brute force).
- IP addresses involved.
- Log evidence (without sharing filters here).
- Suggested mitigations (e.g., blocking IPs, enhancing authentication methods).

---

## Conclusion

This Splunk Home Lab setup will help you practice incident investigations, especially brute force attacks across services like DNS, FTP, HTTP, and SSH. You can continuously add more data sources and adjust configurations to simulate different attack scenarios. Happy investigating!
