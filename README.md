Task 4 Report – Exploitation & System Security
Internship

Cyber Security Internship – Task 4

Objective

The objective of this task was to understand the penetration testing workflow by exploiting vulnerabilities in a controlled lab environment using Metasploit Framework, performing post-exploitation activities, and demonstrating password auditing using John the Ripper.

Lab Environment

Attacker Machine

Operating System: Kali Linux
IP Address: 192.168.0.102

Target Machine

Operating System: Metasploitable2
IP Address: 192.168.0.101

Tools Used

Metasploit Framework
Nmap
John the Ripper
Meterpreter
Linux Terminal
Penetration Testing Methodology

The following methodology was followed:

Target Verification
Vulnerability Identification
Exploitation
Post-Exploitation
Password Auditing
Documentation
Exploitation Using Metasploit
Target Verification

Connectivity between Kali Linux and Metasploitable2 was verified.

The vulnerable FTP service running on the target was identified.

Service:

vsFTPd 2.3.4
Vulnerability Verification

The Metasploit module:

exploit/unix/ftp/vsftpd_234_backdoor

was selected.

The built-in check functionality confirmed that the target appeared vulnerable.

Exploitation

The following parameters were configured:

RHOSTS = 192.168.0.101
LHOST = 192.168.0.102

The exploit was executed successfully.

A Meterpreter session was established with the target system.

Post-Exploitation

After successful exploitation, Meterpreter was used to enumerate the compromised system.

Commands executed included:

sysinfo
getuid
pwd
shell
whoami
hostname
id
uname -a
ifconfig

The session confirmed successful access to the target system and allowed collection of basic host information.

Password Auditing using John the Ripper

Password hashes were obtained from the target Linux machine using:

/etc/passwd
/etc/shadow

The files were merged using:

unshadow passwd.txt shadow.txt > hashes.txt

John the Ripper was then executed:

john hashes.txt

Several weak passwords were successfully recovered, demonstrating the risks associated with poor password practices.

Examples included:

user → user
postgres → postgres
msfadmin → msfadmin
service → service
klog → 123456789
sys → batman
Hydra Observation

An attempt was made to perform SSH password auditing using Hydra.

The connection could not be established because the legacy OpenSSH server on Metasploitable2 supports cryptographic algorithms that are disabled by default in modern Kali Linux distributions.

Manual SSH authentication using compatibility options confirmed that the target credentials were valid, indicating the issue was due to client-server cryptographic compatibility rather than incorrect configuration.

Learning Outcomes

During this task I learned:

Metasploit Framework workflow
Vulnerability verification using Metasploit
Exploiting intentionally vulnerable systems
Meterpreter session handling
Linux post-exploitation techniques
Password hash extraction on Linux
Password auditing using John the Ripper
The impact of weak passwords
The importance of maintaining updated cryptographic standards
Conclusion

This task demonstrated the complete exploitation lifecycle in a controlled penetration testing environment. Successful exploitation of the target machine, post-exploitation enumeration, and password auditing highlighted the importance of vulnerability management, secure configurations, and strong password policies in defending modern systems.
