# -Multi-Honeypot-Platform
Enhanced cybersecurity posture by deploying the T-Pot multi-honeypot platform on Azure Cloud, configuring virtual machines and networks to simulate attack surfaces, and monitoring malicious activity to analyze threats and improve incident detection capabilities.

Using T-pot to create a virtualized honeypot on Azure

Technologies used:
- Microsoft Azure
- Telekom Security's Tpot honeypot

In short, a honeypot is a mechanism used to detect, deceive, or gather information about unauthorized access attempts or malicious activities on computer networks or systems. 
The purpose of a honeypot is to divert and distract attackers from the actual target systems, allowing security professionals to observe and analyze their techniques, motivations, and objectives. By closely monitoring the activities within the honeypot, security professionals can gain insights into the attackers' methods, tools, and vulnerabilities they exploit.

Given my interest in cybersecurity, I was naturally curious about how attackers in the real world might attack a system in the wild and decided to find out first hand. I used Azure so spin up a VM for safety (no "real"/ procuction system would be put at risk) and Telekom Security's Tpot honeypot to act as an irresistible  target (https://github.com/telekom-security/tpotce). 

 ## 🛠️ Implementation Steps

### 1. Installing PuTTY for SSH Access
![PuTTY Installation](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/4d9c36f8c7f09a63b0e34f9dcb7314e166b20290/Images/1.png)
PuTTY is a free and open-source SSH client used to access the T-Pot honeypot server remotely. It helps establish a secure terminal connection between the local machine and the Azure-hosted VM.

### 2. Microsoft Azure Homepage
![Azure Homepage](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/4d9c36f8c7f09a63b0e34f9dcb7314e166b20290/Images/2.png)
This is the Azure portal homepage, where resources such as virtual machines, networks, and storage can be created and managed. It serves as the foundation for deploying and running the T-Pot honeypot environment.

### 3. Azure Dashboard with Created Resources
![Azure Dashboard](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/4d9c36f8c7f09a63b0e34f9dcb7314e166b20290/Images/3.png)
The Azure dashboard displays the deployed resources for this project, including the virtual machine for T-Pot, a Log Analytics workspace, and a resource group for better organization and monitoring.

### 4. Creating a Virtual Machine in Azure
![Create VM](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/4d9c36f8c7f09a63b0e34f9dcb7314e166b20290/Images/4.png)
This screenshot shows the process of setting up a virtual machine in Azure. It includes selecting the subscription, resource group, and configuration options necessary to host the T-Pot honeypot platform.

### 5. Selecting Ubuntu Image for VM
![Ubuntu Image Selection](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/6ba5b5fa9eada639dfce855008f3860e0f9ae734/Images/5.png)  
During the VM setup, the image **Ubuntu Server 24.04 LTS - x64 Gen2** was selected. This OS provides a secure and updated environment ideal for deploying security tools like T-Pot.

### 6. Azure Deployment in Progress
![Deployment In Progress](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/6ba5b5fa9eada639dfce855008f3860e0f9ae734/Images/6.png)  
After initiating the virtual machine creation, Azure shows the status as "Deployment in progress" under the resource group `RG-Honeypot`. This ensures all configuration steps are being processed.

### 7. Deployment Completed Successfully
![Deployment Complete](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/6ba5b5fa9eada639dfce855008f3860e0f9ae734/Images/7.png)  
The Azure portal confirms that the VM deployment is complete. This status indicates that the virtual machine is now ready for further configuration and SSH access.

### 8. VM Overview with Public IP
![VM Overview](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/6ba5b5fa9eada639dfce855008f3860e0f9ae734/Images/8.png)  
The virtual machine is now running and accessible. The assigned public IP address `20.93.68.74` allows remote SSH connections, which is critical for installing and managing T-Pot honeypot services.

### 9. Network Security Group Overview
![Network Security Group](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/b344025fb1e3138f547801a799e41f407cd2948a/Images/9.png)
This shows the main Network Security Group (NSG) configuration for the HoneyPot virtual machine. The NSG named "HoneyPot-nsg" is attached to network interface "honeypot215_z1" and provides essential network traffic control. It impacts 0 subnets and 1 network interface, offering granular security management for the honeypot system.

### 10. Port Rule Management Interface
![Port Rule Management](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/b344025fb1e3138f547801a799e41f407cd2948a/Images/10.png)
The NSG configuration interface allows creation and management of both inbound and outbound port rules. This interface provides options to configure source and destination IP ranges, protocol specifications (TCP, UDP, Any), port ranges, and action settings (Allow/Deny) for comprehensive network security control.

### 11. Security Rules Configuration
![Security Rules Table](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/b344025fb1e3138f547801a799e41f407cd2948a/Images/11.png)
This displays the current inbound port rules configuration with 5 active rules. Key rules include SSH access on port 22 (priority 300) and a wide port range rule (1-65535) for traffic analysis (priority 310). These rules are strategically designed to attract and monitor malicious traffic while maintaining controlled administrative access to the honeypot system.

### 12. PuTTY SSH Configuration
![PuTTY Configuration](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/b344025fb1e3138f547801a799e41f407cd2948a/Images/12.png)

PuTTY configuration window showing the SSH connection setup for remote access to the honeypot system. The configuration includes host IP address (20.93.68.74), port 22, and SSH connection type. The interface displays various configuration categories including session management, terminal settings, and connection parameters for secure remote administration and monitoring capabilities.

### 13. SSH Connection to HoneyPot System
![SSH Login](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/21e4508bea8712c19d20cf2cd0c96bb9cf9d630c/Images/13.png)
This shows the successful SSH connection to the HoneyPot virtual machine running Ubuntu 24.04.1 LTS. The terminal displays the login as user "CyberCheck" to IP address 20.93.68.74. System information includes current load (0.01), memory usage (2%), processes (148), and network configuration. The system shows 0 security updates available and provides links to Ubuntu documentation and support resources.

### 14. T-Pot Installation Process
![T-Pot Setup](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/21e4508bea8712c19d20cf2cd0c96bb9cf9d630c/Images/14.png)
The terminal shows the T-Pot honeypot platform installation process. After installing Git, the system clones the T-Pot repository from GitHub (telekom-security/tpotce.git). The installation progress displays object enumeration, counting, compression, and resolution phases. The T-Pot ASCII art logo is visible, indicating the honeypot framework is being set up for threat detection and analysis.

### 15. T-Pot System Updates and Configuration
![T-Pot Updates](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/21e4508bea8712c19d20cf2cd0c96bb9cf9d630c/Images/15.png)
This displays the T-Pot system performing package updates and dependency resolution. The terminal shows the system reading package lists, building dependency trees, and updating system components. The T-Pot "Update IP" and "Clean up" ASCII banners are visible, indicating the honeypot is configuring network settings and cleaning up installation files. The system reports 0 packages to upgrade, confirming a clean installation state.

### 16. T-Pot Web Dashboard Interface
![T-Pot Dashboard](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/21e4508bea8712c19d20cf2cd0c96bb9cf9d630c/Images/16.png)
The T-Pot web interface dashboard accessible at https://20.51.253.206:64297 showing the main control panel at 11:29 with a "Good morning" greeting. The dashboard provides access to various security tools including Attack Map, Cockpit, Cyberchef, Elasticvue, Kibana, Spiderfoot, SecurityMeter, T-Pot GitHub repository, and T-Pot ReadMe. The hexagonal design with the T-POG logo represents the comprehensive honeypot platform for cyberthreat monitoring and analysis.

### 17. T-Pot Honeypot Global Attack Map
![T-Pot Global Attack Map](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/21e4508bea8712c19d20cf2cd0c96bb9cf9d630c/Images/17.png)
Interactive world map displaying real-time honeypot attack statistics with geographical visualization. Shows attack origins with connection lines and provides detailed statistics including last minute (91), last hour (2463), and last 24 hours (98331) attacks. Features service breakdown by protocol (FTP, SSH, TELNET, EMAIL, SQL, DNS, HTTP) with attack source countries and IP addresses for comprehensive threat intelligence.

### 18. T-Pot Honeypot Analytics Dashboard
![T-Pot Analytics Dashboard](https://github.com/rakshitbhari/-Multi-Honeypot-Platform/blob/21e4508bea8712c19d20cf2cd0c96bb9cf9d630c/Images/18.png)
Comprehensive Elastic/Kibana dashboard showing detailed honeypot attack analytics over the last 24 hours. Features multiple visualization panels including top 10 honeypot attacks summary (Dionaea: 41,944, HoneyTrap: 15,829, etc.), attack frequency histograms, time-series charts, geographic attack distribution with dynamic world map, destination port analysis, country-wise attack statistics, and attacker IP reputation data with OS distribution metrics.

---


