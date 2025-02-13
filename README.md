# 🔥 Ethical Hacking Project: RDP, Office Macro & File Upload Exploits

## 📌 Project Overview  
This project emphasizes three key areas in cybersecurity and penetration testing:
- **RDP Exploit on Fully Patched Windows 11**
- **Microsoft Office Macro Exploit**
- **File Upload Vulnerability Exploitation in DVWA**

The goal of this project is to analyze these vulnerabilities, understand their impact, and propose preventive measures to mitigate such risks.

# **🛠 Chapter 1: RDP Exploit on Fully Patched Windows 11**  
## 🔍 Introduction  
The **Remote Desktop Protocol (RDP)** allows users to remotely access Windows machines. Despite security patches, RDP is frequently targeted due to weak credentials and improper configurations. This project demonstrates **how an attacker can exploit RDP on a fully patched Windows 11 machine** through brute-force attacks.

## **⚠️ Problem Statement**  
Many Windows systems exposed to the internet have weak passwords or misconfigured security settings, making **brute-force attacks** viable. Even **fully patched Windows 11 machines** can be vulnerable to these attacks.

## **🎯 Objectives**
✔️ Identify open **RDP ports** using `nmap`  
✔️ Brute-force **Windows login credentials** using `Hydra`  
✔️ Gain **unauthorized RDP access** and demonstrate the risks  

## **📖 Literature Review**  
RDP remains a primary target for attackers due to **credential stuffing attacks**. Even with security updates, brute-force attempts on **TCP port 3389** continue to succeed on misconfigured systems.  

Research highlights the need for:  
✅ **Strong password policies**  
✅ **Multi-factor authentication (MFA)**  
✅ **Restricting RDP access to trusted IPs**  

**Source:** [Cloudflare - RDP Security Risks](https://www.cloudflare.com/learning/access-management/rdp-security-risks/)  

## **🛠 Exploitation Methodology**  
### **🔹 Step 1: Checking Windows Update Status**  
Before launching an attack, we ensure the target Windows 11 machine is fully patched.  

🔹 **Step 2: Scanning Open Ports with Nmap**
To check if RDP is open on the target, we use Nmap.

**Command Used:**
sudo nmap -p0-65535 192.168.133.131 | 
📌 Findings: Port 3389 (RDP) is open.

**🔹 Step 3: Creating User and Password Lists**
To perform brute-force, we create username and password lists.

**📌 Example Username List (userlist.txt):**
admin,
user,
administrator,
wasique

**📌 Example Password List (passlist.txt):**
123456,
password,
admin123

**🔹 Step 4: Brute-Forcing RDP Credentials with Hydra**
We use Hydra to attempt login with the generated username/password lists.

**Command Used:**
sudo hydra -L userlist.txt -P passlist.txt rdp://192.168.133.131 2>/dev/null | 
📌 Result: Valid credentials were found!

**🔹 Step 5: Connecting to Target with xfreerdp**
Once valid credentials are obtained, we use xfreerdp to connect.

**Command Used:**
sudo xfreerdp /u:Wasique /p:01798930353 /v:192.168.133.131 | 
📌 Result: Successfully connected to the target Windows 11 machine!

**📌 Results**
✔️ Successfully brute-forced RDP on a fully patched Windows 11 machine
✔️ Demonstrated weak password risks and the importance of security configurations

**📌 Attack Summary:**
The penetration testing process involved multiple stages, starting from reconnaissance to successful exploitation. Below is a step-by-step breakdown of how the attack unfolded:

**1️⃣ Reconnaissance and Port Scanning:**
Using Nmap, we conducted a full port scan on the target machine (192.168.133.131). The results revealed that port 3389 (RDP) was open, confirming that the system had Remote Desktop Protocol enabled and was potentially vulnerable.

**2️⃣ Credential Generation:**
To perform brute-force attacks, we created custom username and password lists based on common credentials. This included typical usernames like admin, user, and wasique, along with weak passwords like 123456, password, and admin123.

**3️⃣ Brute-Forcing Login Credentials:**
With Hydra, we launched a brute-force attack against the RDP login. The tool systematically tried different username-password combinations until it successfully discovered valid credentials for accessing the Windows 11 machine.

**4️⃣ Exploitation and Remote Access:**
After obtaining the valid credentials, we used xfreerdp to establish an RDP session with the target machine. This granted us full remote access to the system, demonstrating the severe risk posed by weak credentials.

**🎯 Final Outcome:**
✔️ Successfully bypassed authentication on a fully patched Windows 11 machine
✔️ Gained full remote desktop control over the target system
✔️ Highlighted the importance of strong passwords and RDP security hardening


**🔒 Mitigation Strategies:**
To secure RDP and prevent brute-force attacks, organizations should implement the following security measures:

🛡️ 1. Enforce Strong Password Policies
✔️ Use complex passwords (uppercase, lowercase, numbers, special characters).
✔️ Implement password expiration and rotation policies.

🛡️ 2. Enable Multi-Factor Authentication (MFA)
✔️ Require users to enter a second authentication factor (e.g., SMS, authenticator app).

🛡️ 3. Restrict RDP Access
✔️ Block RDP (port 3389) on the firewall unless necessary.
✔️ Allow only trusted IP addresses to access RDP.

🛡️ 4. Implement Account Lockouts
✔️ Lock accounts after 3-5 failed login attempts to prevent brute-force attacks.

🛡️ 5. Apply Security Updates
✔️ Keep Windows and security patches up to date to mitigate known vulnerabilities.

**🛠 Tools Used:**
Metasploit Framework,
Nmap,
Burp Suite,
Hydra,
Kali Linux



**📖 Next Steps**

Chapter 2: Microsoft Office Macro Exploit

Chapter 3: File Upload Vulnerability Exploit in DVWA

🔍 Read Full Project Report
