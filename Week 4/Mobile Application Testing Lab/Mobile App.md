# Mobile Application Testing 
## 1. Lab Overview

This lab focuses on identifying vulnerabilities in Android applications using static and dynamic analysis techniques. Tools such as MobSF, Frida, and Drozer were used to analyze APK files, exploit weaknesses, and document findings.

## 2. Tools Used
MobSF (Mobile Security Framework)

Frida

Drozer
## 3. Static Analysis Findings

Objective: Analyze APK for insecure storage vulnerabilities using MobSF.

Description:
MobSF analysis revealed that sensitive data is stored insecurely within the application. The app uses unencrypted storage mechanisms, exposing user data to potential attackers.

Impact:
Attackers can access confidential data such as credentials, tokens, or personal information.

Recommendation:
Use secure storage mechanisms such as Android Keystore and encrypt sensitive data before storage.

## 4. Dynamic Testing (Frida)

Objective: Hook application functions and bypass authentication.

Summary 
Frida was used to dynamically hook authentication functions within the application. By intercepting function calls, authentication checks were bypassed, allowing unauthorized access. This demonstrated weak runtime protections and lack of integrity checks. Proper validation and anti-hooking mechanisms should be implemented to prevent such attacks.

## 5. IPC Testing (Drozer)

Objective: Test Inter-Process Communication vulnerabilities.

Findings:

Exported components were identified.
Some services were accessible without proper permissions.
Potential for privilege escalation via IPC misuse.

Recommendation:
Restrict component exposure and enforce proper permission checks.

## 6. Checklist

Run MobSF for static analysis
Hook functions with Frida
Test IPC vulnerabilities using Drozer

## 7. Conclusion

The mobile application exhibited multiple security weaknesses, including insecure data storage and weak runtime protections. Proper secure coding practices, encryption, and runtime defenses must be implemented to enhance the overall security posture of the application.
