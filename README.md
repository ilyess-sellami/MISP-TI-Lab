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

1. **Clone the Lab Environment**  

```bash
git https://github.com/ilyess-sellami/MISP-TI-Lab.git
cd MISP-TI-Lab
```

2. **Install Dependencies**

Ensure you have a Linux server (Ubuntu 20.04+) and run the provided install script:

```bash
chmod +x INSTALL.ubuntu2404.sh
sudo ./INSTALL.ubuntu2404.sh
```

![MISP Install](/screenshots/misp_install.png)

After the installation is completed, a default admin login is generated:

- Username: `admin@admin.test`
- Password: `<generated strong password>`

![MISP Default Credentials](/screenshots/misp_default_credentials.png)