# MISP-TI-Lab

![MISP Image](/screenshots/misp.png)


## Overview
**MISP-TI-Lab** is a simulated Security Operations Center (SOC) environment built around **MISP (Malware Information Sharing Platform)**. This lab allows security analysts to practice **threat intelligence collection, correlation, and sharing** by simulating real-world cyber threats such as ransomware campaigns. The lab demonstrates how organizations can track, analyze, and respond to cyber threats in a controlled environment.


## Objectives
- Deploy and configure a fully functional MISP instance.
- Simulate malware event targeting a client organization.
- Collect and organize Indicators of Compromise (IOCs) including file hashes, IPs, domains, URLs, and email addresses.
- Correlate events to detect campaigns and threat patterns.
- Apply tags, galaxy clusters, and contextual metadata for efficient threat analysis.
- Provide a realistic SOC training environment for analysts.

## Features
- User role management (Admin, Analyst, Read-only)
- Event creation and IOC management
- Object and attribute grouping for contextual analysis
- Event correlation and visualization


## Setup Instructions

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
