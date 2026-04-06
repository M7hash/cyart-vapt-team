# **Network Protocol Attacks Lab Report**

---

## **1. Lab Overview**

This lab focuses on performing **Man-in-the-Middle (MitM) attacks** and exploiting network protocols using industry-standard tools. The objective is to capture credentials, manipulate traffic, and analyze network packets for security weaknesses.

---

## **2. Tools Used**

* Responder
* Ettercap
* Wireshark

---

## **3. Objectives**

* Perform SMB relay attacks
* Capture NTLM authentication hashes
* Conduct ARP spoofing for MitM attacks
* Analyze intercepted traffic

---

## **4. Attack Simulation Log**

| Attack ID | Technique | Target IP     | Status  | Outcome   |
| --------- | --------- | ------------- | ------- | --------- |
| 015       | SMB Relay | 192.168.1.200 | Success | NTLM Hash |

---

## **5. Attack Details**

### **5.1 SMB Relay Attack **

* Configured Responder to listen for LLMNR/NBT-NS requests
* Victim machine attempted authentication over SMB
* Captured NTLM hash successfully
* Relay attack enabled unauthorized access simulation

---

### **5.2 Man-in-the-Middle Attack (Ettercap) **

Ettercap was used to perform ARP spoofing, positioning the attacker between the victim and gateway. Network traffic was intercepted and monitored in real time. Sensitive information such as credentials and session data could be captured, demonstrating the risks of unsecured networks and lack of proper encryption protocols.

---

### **5.3 Traffic Analysis (Wireshark)**

* Captured live packets during attack
* Filtered SMB, HTTP, and DNS traffic
* Identified authentication exchanges
* Observed NTLM challenge-response mechanism

---

## **6. Key Findings**

* NTLM authentication is vulnerable to relay attacks
* Lack of network segmentation increases risk
* Unencrypted traffic exposes sensitive data
* ARP spoofing remains highly effective in LAN environments

---

## **7. Checklist**

Capture NTLM hashes (Responder)
Spoof DNS (Ettercap)
Analyze traffic (Wireshark)

---

## **8. Conclusion**

The lab successfully demonstrated how attackers exploit network protocols using MitM techniques. Tools like Responder and Ettercap can intercept authentication and manipulate traffic, highlighting the importance of secure configurations, encryption, and network monitoring.

---

## **9. Recommendations**

* Disable LLMNR and NetBIOS
* Implement SMB signing
* Use network segmentation
* Deploy IDS/IPS systems
* Enforce strong authentication mechanisms

---
