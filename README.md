# SOC Home Lab – Attack Detection using Splunk & Sysmon

---

## 📌 Project Overview

This project demonstrates the design and implementation of a Security Operations Center (SOC) Home Lab to simulate and detect cyber attacks in a controlled environment.

The lab replicates a real-world SOC workflow by integrating log collection, attack simulation, detection, and analysis using industry-standard tools.

---

## 🎯 Objective

- Build a functional SOC environment for monitoring endpoint activity  
- Simulate real-world cyber attacks (brute force, PowerShell execution)  
- Detect malicious behavior using Splunk queries (SPL)  
- Analyze logs and generate actionable security insights  

---

## 🏗️ Architecture

```
Kali Linux (Attacker)
        ↓
Windows Machine (Victim + Sysmon)
        ↓
Splunk Universal Forwarder
        ↓
Splunk Enterprise (SIEM)
```

---

## 🛠️ Tools & Technologies

- Splunk Enterprise – SIEM platform  
- Splunk Universal Forwarder – Log collection  
- Sysmon – Endpoint monitoring  
- Windows 10/11 – Target system  
- Kali Linux – Attacker machine  
- Hydra – Brute force attack tool  

---

## ⚔️ Attack Scenarios

### 🔹 Brute Force Attack (Login)

- Generated multiple failed login attempts  
- Detected using EventCode 4625  
- Identified targeted accounts  

---

### 🔹 PowerShell Activity Detection

- Executed PowerShell commands  
- Logged via Sysmon EventCode 1  
- Detected suspicious command-line activity  

---

## 🔍 Detection Queries

### Brute Force Detection

```spl
index=wineventlog EventCode=4625
| where NOT like(Account_Name,"%$")
| stats count by Account_Name, host
| where count > 5
```

---

### PowerShell Detection

```spl
index=sysmon EventCode=1
| where like(CommandLine,"%powershell%")
```

---

## 📊 Key Findings

- Multiple failed login attempts detected  
- Administrator account targeted  
- PowerShell activity successfully logged  
- Attack patterns visible in logs  

---

## 🛡️ Mitigation

- Enable account lockout  
- Restrict RDP access  
- Monitor PowerShell usage  
- Enable centralized logging  

---

## 📸 Screenshots

(To be added)

---

## 📄 Conclusion

This project demonstrates hands-on experience in SOC operations including log analysis, attack simulation, and detection using real-world tools.
