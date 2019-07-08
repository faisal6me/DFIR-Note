# DFIR-Note
This Is just My Personal Note For Fast-IR


What are the Most Tragted Servers By the Adversy and Why :

1-SCCM is a platform that allows for an enterprise to package and deploy operating systems, software, and software updates.If you can gain access to SCCM, it makes for a great attack platform. It heavily integrates Windows PowerShell, has excellent network visibility, and has a number of SCCM clients as SYSTEM just waiting to execute your code as SYSTEM.



2-DC : Domin Controller 
Domain controllers contain the data that determines and validates access to your network, including any group policies and all computer names. Everything an attacker could possibly need to cause massive damage to your data and network is on the DC, which makes a DC a primary target during a cyberattack.

3-AD :ACTIVE DIRECTORY : DOMAIN CONTROLLER :: car : engine
Active Directory is a type of domain, and a domain controller is an important server on that domain. Kind of like how there are many types of cars, and every car needs an engine to operate. Every domain has a domain controller, but not every domain is Active Directory.

4-EX1: Microsoft Exchange Server is a mail server and calendaring server developed by Microsoft. It runs exclusively on Windows Server operating , allows hackers to gain full control over all mail traffic, including the ability to intercept, redirect, or modify the content of inbound and outbound messages. 

5- DMZ= In computer security, a DMZ or demilitarized zone is a physical or logical subnetwork that contains and exposes an organization's external-facing services to an untrusted network,

6-Fileshare server : becouse it face public network 

![](https://www.vmray.com/analyses/rtf-doc-cve-exploit-analysis/report/process_graph.svg)

**The 6 steps Of IR**

1. Preparation
This phase will be the work horse of your incident response planning, and in the end, the most crucial phase to protect your business. Part of this phase includes:

Develop incident response drill scenarios and regularly conduct mock data breaches to evaluate your incident response plan.
Ensure that all aspects of your incident response plan (training, execution, hardware and software resources, etc.) are 

Does the Incident Response Team know their roles and the required notifications to make?



2. Identification
This is the process where you determine whether you’ve been breached. A breach, or incident, could originate from many different areas.

 Questions to address 
When did the event happen?
How was it discovered?
Who discovered it?
Have any other areas been impacted?
What is the scope of the compromise?
Does it affect operations?
Has the source (point of entry) of the event been discovered?



3. Containment
When a breach is first discovered, your initial instinct may be to securely delete everything so you can just get rid of it. However, that will likely hurt you in the long run since you’ll be destroying valuable evidence that you need to determine where the breach started and devise a plan to prevent it from happening again.

Instead, contain the breach so it doesn’t spread and cause further damage to your business. If you can, disconnect affected devices from the Internet. Have short-term and long-term containment strategies ready. It’s also good to have a redundant system back-up to help restore business operations. That way, any compromised data isn’t lost forever.

This is also a good time to update and patch your systems, review your remote access protocols (requiring mandatory multi-factor authentication), change all user and administrative access credentials and harden all passwords.

WATCH: Forensics Lessons Learned Webinar

 Questions to address 
What’s been done to contain the breach short term?
What’s been done to contain the breach long term?
Has any discovered malware been quarantined from the rest of the environment?
What sort of backups are in place?
Does your remote access require true multi-factor authentication?
Have all access credentials been reviewed for legitimacy, hardened and changed?
Have you applied all recent security patches and updates?



4. Eradication
Once you’ve contained the issue, you need to find and eliminate the root cause of the breach. This means all malware should be securely removed, systems should again be hardened and patched, and updates should be applied.

Whether you do this yourself, or hire a third party to do it, you need to be thorough. If any trace of malware or security issues remain in your systems, you may still be losing valuable data, and your liability could increase.

 Questions to address 
Have artifacts/malware from the attacker been securely removed?
Has the system be hardened, patched, and updates applied?
Can the system be re-imaged?


5. Recovery
This is the process of restoring and returning affected systems and devices back into your business environment. During this time, it’s important to get your systems and business operations up and running again without the fear of another breach.


**Incedent Response For Webshell**

1. **"${eval($_POST[potato])}};?>"**

2. One method of detection is to review web logs for suspicious GET requests. 
     exsample: ::1 — — [22/Aug/2018:12:42:00 -0400] “GET /dashboard/images/a.php?potato=ipconfig HTTP/1.1” 200 553 “-”       “Mozilla/5.0 (Windows NT 6.1; Trident/7.0; rv:11.0) like Gecko”

3. Process behaviour ! 
    exsample : a child of the web server process and run under the same user context as the server 
    Such as: w3wp.exe >>>cmd.exe or Powershell.exe or ipconfig
            httpd.exe >>> cmd.exe or whoami.exe or ifconfig
4. Run Yara Rules and Cheack All Public Servers Such As : DMZ server , Excagnge server , Fileshare server etc 

5. intrusion detection system/ intrusion prevention system logs,application logs, IIS/Apache logs, PCAP repositories, firewall logs, and reverse proxy logs.

**More Deep Analysis:! **
```
-Detect persistence in VDI environments by searching file shares containing user profiles for all .lnk files.
-Detect evasion techniques by the threat actors by identifying deleted logs. This can be done by reviewing last-seen entries and by searching for event 104 on Windows system logs.
-Detect persistence by reviewing all administrator accounts on systems to identify unauthorized accounts, especially those created recently.
-Detect the malicious use of legitimate credentials by reviewing the access times of remotely accessible systems for all users. Any unusual login times should be reviewed by the account owners.
-Detect the malicious use of legitimate credentials by validating all remote desktop and VPN sessions of any user’s credentials suspected to be compromised.
-Detect spear-phishing by searching OWA logs for all IP addresses listed in the IOC packages.
-Detect spear-phishing through a network by validating all new email accounts created on mail servers, especially those with external user access.
-Detect persistence on servers by searching system logs for all filenames listed in the IOC packages.
-Detect lateral movement and privilege escalation by searching PowerShell logs for all filenames ending in “.ps1” contained in the IOC packages. (Note: requires PowerShell version 5, and PowerShell logging must be enabled prior to the activity.)
-Detect persistence by reviewing all installed applications on critical systems for unauthorized applications, specifically note FortiClient VPN and Python 2.7.
-Detect persistence by searching for the value of “REG_DWORD 100” at registry location “HKLM\SOFTWARE\Policies\Microsoft\Windows NT\Terminal”. Services\MaxInstanceCount” and the value of “REG_DWORD 1” at location “HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\system\dontdisplaylastusername”.
-Detect installation by searching all proxy logs for downloads from URIs without domain names.
```
**Incedent Response For Malware**
> Note: There are Two types of Malware File Malware and Fileless Malware.>

• What to look for:

o Programs executing from temporary or cache folders
o Programs executing from user profiles (AppData, Roaming, Local, etc)
o Programs executing from C:\ProgramData or All Users profile
o Programs executing from C:\RECYLER
o Programs stored as Alternate Data Streams (i.e. C:\Windows\System32:svchost.exe)
o Programs with random and unusual file names
o Windows programs located in wrong folders (i.e. C:\Windows\svchost.exe)
o Other activity on the system around suspicious files

 
 
 **General Best Practices Applicable To CA or IR:**
 
 ```
-Prevent external communication of all versions of SMB and related protocols at the network boundary by blocking TCP ports 139 and 445 with related UDP port 137. See the NCCIC/US-CERT publication on SMB Security Best Practices for more information.
-Block the Web-based Distributed Authoring and Versioning (WebDAV) protocol on border gateway devices on the network.
-Monitor VPN logs for abnormal activity (e.g., off-hour logins, unauthorized IP address logins, and multiple concurrent logins).
-Deploy web and email filters on the network. Configure these devices to scan for known bad domain names, sources, and addresses; block these before receiving and downloading messages. This action will help to reduce the attack surface at the network’s first level of defense. Scan all emails, attachments, and downloads (both on the host and at the mail gateway) with a reputable anti-virus solution that includes cloud reputation services.
-Segment any critical networks or control systems from business systems and networks according to industry best practices.
-Ensure adequate logging and visibility on ingress and egress points.
-Ensure the use of PowerShell version 5, with enhanced logging enabled. Older versions of PowerShell do not provide adequate -logging of the PowerShell commands an attacker may have executed. Enable PowerShell module logging, script block logging, and transcription. Send the associated logs to a centralized log repository for monitoring and analysis. See the FireEye blog post Greater Visibility through PowerShell Logging for more information.
-Implement the prevention, detection, and mitigation strategies outlined in the NCCIC/US-CERT Alert TA15-314A – Compromised Web Servers and Web Shells – Threat Awareness and Guidance.
-Establish a training mechanism to inform end users on proper email and web usage, highlighting current information and analysis, and including common indicators of phishing. End users should have clear instructions on how to report unusual or suspicious emails.
-Implement application directory whitelisting. System administrators may implement application or application directory whitelisting through Microsoft Software Restriction Policy, AppLocker, or similar software. Safe defaults allow applications to run from PROGRAMFILES, PROGRAMFILES(X86), SYSTEM32, and any ICS software folders. All other locations should be disallowed unless an exception is granted.
-Block RDP connections originating from untrusted external addresses unless an exception exists; routinely review exceptions on a regular basis for validity.
-Store system logs of mission critical systems for at least one year within a security information event management tool.
-Ensure applications are configured to log the proper level of detail for an incident response investigation.
-Consider implementing HIPS or other controls to prevent unauthorized code execution.
-Establish least-privilege controls.
-Reduce the number of Active Directory domain and enterprise administrator accounts.
-Based on the suspected level of compromise, reset all user, administrator, and service account credentials across all local and domain systems.
-Establish a password policy to require complex passwords for all users.
-Ensure that accounts for network administration do not have external connectivity.
-Ensure that network administrators use non-privileged accounts for email and Internet access.
-Use two-factor authentication for all authentication, with special emphasis on any external-facing interfaces and high-risk environments (e.g., remote access, privileged access, and access to sensitive data).
-Implement a process for logging and auditing activities conducted by privileged accounts.
-Enable logging and alerting on privilege escalations and role changes.
-Periodically conduct searches of publically available information to ensure no sensitive information has been disclosed. ---Review photographs and documents for sensitive data that may have inadvertently been included.
-Assign sufficient personnel to review logs, including records of alerts.
-Complete independent security (as opposed to compliance) risk review.
-Create and participate in information sharing programs.
-Create and maintain network and system documentation to aid in timely incident response. Documentation should include network diagrams, asset owners, type of asset, and an incident response plan.
 ```


- [x] Finish my changes
- [ ] Push my commits to GitHub
- [ ] Ready to Engage 
