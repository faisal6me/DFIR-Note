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
1- **"${eval($_POST[potato])}};?>"**

2-One method of detection is to review web logs for suspicious GET requests. 
     exsample: ::1 — — [22/Aug/2018:12:42:00 -0400] “GET /dashboard/images/a.php?potato=ipconfig HTTP/1.1” 200 553 “-”       “Mozilla/5.0 (Windows NT 6.1; Trident/7.0; rv:11.0) like Gecko”

3-Process behaviour ! 
    exsample : a child of the web server process and run under the same user context as the server 
    Such as: w3wp.exe >>>cmd.exe or Powershell.exe or ipconfig
            httpd.exe >>> cmd.exe or whoami.exe or ifconfig
4- Run Yara Rules and Cheack All Public Servers Such As : DMZ server , Excagnge server , Fileshare server etc 

5- intrusion detection system/ intrusion prevention system logs,application logs, IIS/Apache logs, PCAP repositories, firewall logs, and reverse proxy logs.

**Incedent Response For Malware**


 
 
  

