# MISP-TI-Lab

![MISP Image](/screenshots/misp.png)


## 🔎 Overview
**MISP-TI-Lab** is a practical simulation of a **Security Operations Center (SOC)** environment using **MISP (Malware Information Sharing Platform)**.  
In this lab, we set up MISP from scratch, configured access from a local machine, created a client organization, added users, and simulated a **real ransomware incident (Conti)** by importing actual Indicators of Compromise (IOCs).  

This environment provides a **hands-on introduction** to how SOC teams collect, analyze, correlate, and share threat intelligence in real-world scenarios.  


## 🎯 Objectives
- Install and configure a functional **MISP instance** on Ubuntu.  
- Configure `misp.local` access from **MacOS, Linux, and Windows** machines.  
- Change the **default admin credentials** and enforce password complexity.  
- Create a **client organization (Acme Finance Ltd)** with realistic details.  
- Add **SOC analyst users** to the client organization with proper roles.  
- Simulate a **Conti ransomware incident** by creating an event and adding attributes (file hashes, IP, malicious executable).  
- **Publish events** so they are searchable, correlated, and shareable.  


## 🛠 Features
- **Multi-organization support** (Admin + Client organizations).  
- **Role-based access control** (Admin, Analyst, Read-only).  
- **Event creation workflow** with attributes, attachments, and tags.  
- **IOC management** (file hashes, IP addresses, domains, files).  
- **Event publishing and correlation** for realistic SOC training.  
- **Hands-on practice** with a real-world malware case (Conti ransomware).  

## 📦 Setup Instructions

### 1. Clone the Lab Environment  

```bash
git https://github.com/ilyess-sellami/MISP-TI-Lab.git
cd MISP-TI-Lab
```

### 2. Install Dependencies

Ensure you have a **Linux server (Ubuntu 20.04+)** and run the provided install script:

```bash
chmod +x INSTALL.ubuntu2404.sh
sudo ./INSTALL.ubuntu2404.sh
```

![MISP Install](/screenshots/misp_install.png)

After the installation is completed, a default admin login is generated:

- Username: `admin@admin.test`
- Password: `<generated strong password>`

![MISP Default Credentials](/screenshots/misp_default_credentials.png)


### 3. Configure `misp.local` on Your PC

Before accessing MISP from your local machine, you need to map the `misp.local` domain to your Ubuntu server’s IP address because MISP references this domain by default.

**MacOS / Linux**

1. Open a terminal.

2. Edit your hosts file with a text editor using `sudo`:
```bash
sudo nano /etc/hosts
```

3. Add a new line with your server IP and `misp.local`:
```bash
<your-ubuntu-server-ip> misp.local
```

4. Save the file and exit (`Ctrl+O`, `Enter`, `Ctrl+X` in nano).

5. Test by running:
```bash
ping misp.local
```

You should see responses from your server IP.

**Windows**

1. Open `Notepad` **as Administrator**.

2. Open the hosts file located at:
```bash
C:\Windows\System32\drivers\etc\hosts
```

3. Add a new line with your server IP and misp.local:
```bash
<your-ubuntu-server-ip> misp.local
```

4. Save the file.

5. Test by opening Command Prompt and running:
```bash
ping misp.local
```

You should see responses from your server IP.

### 4. Access MISP and Change Default Password

Once `misp.local` is correctly mapped to your Ubuntu server IP, you can access MISP from your local machine.

1. Open your web browser.

2. Navigate to:
```bash
https://misp.local
```

3. Log in using the default admin credentials provided after installation:
- **Username:** `admin@admin.test`
- **Password:** `<generated strong password>`

![MISP Login](/screenshots/misp_login_page.png)

4. MISP will immediately prompt you to **change the default password** for security reasons.

![MISP Change Password](/screenshots/misp_change_password.png)

5. Enter a **strong new password** that meets MISP’s complexity requirements:
- At least 12 characters
- Mix of uppercase, lowercase, numbers, and special characters

6. Save the new password. You are now ready to start using MISP securely.


### 5. Add Client Organization

To simulate a realistic SOC scenario, add a client organization that your events will target.

1. Log in as an **admin** in MISP.

2. Go to the top menu:
**`Administration` → `Organisations` → `Add Organisation`**

3. Fill in the details for the organization:

- **Name:** `Acme Finance Ltd`  
- **Description:** `A leading financial services company. This organization is used in the SOC lab to simulate real-world attacks targeting financial institutions.` 
- **UUID:** Leave blank (automatically generated)  
- **Authkey:** Optional, used for syncing with other MISP instances  
- **Type / Sector:** `Finance / Banking`

![MISP Add Org](/screenshots/misp_add_org.png)

4. Save the organization.

![MISP Success Add Org](/screenshots/misp_success_add_org.png)

### 6. Add User to Client Organization

After creating the client organization, you need to add SOC users and assign them to the organization.

1. Log in as **admin** in MISP.

2. Navigate to:  
**`Administration` → `Users` → `Add User`**

3. Fill in the user details:

- **Email / Username:** `analyst@acmefinance.test` 
- **Name:** `John Doe (SOC Analyst)` 
- **Role:** `Analyst` (can view, add, and manage events for their organization)  
- **Organization:** `Acme Finance Ltd`
- **Password:** Use a strong password meeting MISP’s complexity requirements  
- **Authkey:** Optional, for API access  

4. Save the user.

### 7. Add Malware Event for Client Organization

To simulate a realistic attack, we will create an event representing a **Conti ransomware incident** targeting the client organization **Acme Finance Ltd**.

[VirusTotal link](https://www.virustotal.com/gui/file/53b1c1b2f41a7fc300e97d036e57539453ff82001dd3f6abf07f4896b1f9ca22)  

![VirusTotal Conti Ransomware](/screenshots/virustotal_conti_ransomware.png)

1. Log in as a user assigned to **Acme Finance Ltd** (e.g., SOC Analyst).
2. Navigate to:  
**`Event Actions` → `Add Event`**

3. Fill in the event details:

- **Date:** `2025-09-13`
- **Distribution:** `Your organization only`
- **Threat Level:** `High` 
- **Analysis:** `Initial` 
- **Event Info:** `Conti ransomware detected on Acme Finance Ltd. Sample analyzed via VirusTotal`

![MISP Add Event](/screenshots/misp_add_event.png)

4. Add **Attributes / Indicators of Compromise (IOCs)** with Setting up the **Category:** `Payload Delivery`:

- **MD5:** `290c7dfb01e50cea9e19da81a781af2c`
- **SHA-256:** `53b1c1b2f41a7fc300e97d036e57539453ff82001dd3f6abf07f4896b1f9ca22`
- **IP Address**: `131.107.255.255`


![MISP ADD ATTRIBUTES](/screenshots/misp_event_add_attribute.png)

![MISP Attributes List](/screenshots/misp_event_attributes_list.png)

5. Add the malware **File Attachment**: 
- `53b1c1b2f41a7fc300e97d036e57539453ff82001dd3f6abf07f4896b1f9ca22.exe`

![MISP Add File Attachement](/screenshots/misp_event_add_attachement.png)

6. Optionally, add **tags or galaxy clusters** such as `Ransomware`, `Conti` 

7. Click **Submit** to create and publish the event


### 8. Final Step: Publish the Event

After creating the event and adding all attributes, you need to **publish it** so that it becomes visible and usable by other analysts in your organization.

1. Navigate to:  **`Event Actions` → `List Events`**

![MISP Events List](/screenshots/misp_events_list.png)

2. Locate the event you just created (e.g., **Conti ransomware detected in Acme Finance Ltd**).  

3. Open the event and click the **Publish Event** button at the top-right.  

![MISP Publish Event](/screenshots/misp_publish_event.png)

Once published:  
- The event and its attributes are now **available for searching, correlation, and sharing**.  
- Other users in your organization (or communities, depending on distribution settings) can **use the indicators to detect and respond to similar threats**.  


## ✅ Conclusion

This lab demonstrates how to set up and use MISP (Malware Information Sharing Platform) as a SOC tool for managing and sharing threat intelligence.  
By walking through the process of installing MISP, creating an organization and users, and simulating a real-world ransomware attack event, we saw how MISP helps:  

- **Centralize threat intelligence** with structured events and attributes.  
- **Enable correlation** between imported threat feeds and internal events.  
- **Improve collaboration** between SOC teams and organizations by sharing indicators of compromise.  
- **Support incident response** with actionable data such as hashes, IPs, domains, and malicious files.  

With this setup, security teams can quickly detect, analyze, and respond to threats, while also contributing to a global community of defenders.  


