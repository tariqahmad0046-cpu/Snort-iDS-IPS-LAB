# Snort-iDS-IPS-LAB

# 🔐 Enterprise Network Intrusion Detection & Prevention Lab using Snort

---

## 👨‍💻 Author

**Tariq Ahmad**
Cybersecurity Enthusiast | SOC Aspirant | Network Security Learner

---

## 📌 Project Overview

This project demonstrates the deployment and configuration of **Snort** as both:

* Intrusion Detection System (IDS)
* Intrusion Prevention System (IPS)

The lab simulates a real-world enterprise security monitoring environment using virtual machines.

The project includes:

* Detection of ICMP (Ping) attacks
* Detection of TCP SYN port scans
* Inline blocking of malicious traffic
* Log analysis
* Custom rule creation

---

## 🎯 Project Objectives

* Deploy Snort in IDS (Passive) mode
* Configure Snort in IPS (Inline) mode
* Detect ICMP reconnaissance attempts
* Detect TCP SYN (Nmap) scans
* Block malicious traffic in real-time
* Analyze Snort alert logs
* Simulate real-world SOC monitoring environment

---

## 🛠 Tools & Technologies Used

* Snort
* Kali Linux (Attacker Machine)
* Ubuntu (IDS/IPS Sensor)
* VirtualBox (Virtualization Platform)
* Nmap (Port Scanning Tool)

---

## 🌐 Lab Architecture

### 🔹 IDS Mode (Passive Monitoring)

```
+------------------+
|  Kali Linux      |
|  (Attacker)      |
+--------+---------+
         |
         |  Internal Network
         |
+--------v---------+
|  Ubuntu Server   |
|  Snort (IDS)     |
+------------------+
```

✔ Monitors traffic
✔ Generates alerts
❌ Does NOT block traffic

---

### 🔹 IPS Mode (Inline Blocking)

```
+------------------+
|  Kali Linux      |
|  (Attacker)      |
+--------+---------+
         |
         |
+--------v---------+
|  Ubuntu Server   |
|  Snort (IPS)     |
|  Inline Mode     |
+--------+---------+
         |
         |
+--------v---------+
|  Target Network  |
+------------------+
```

✔ Detects attacks
✔ Blocks malicious packets
✔ Prevents unauthorized access

---

## ⚙️ Installation & Setup

### Step 1: Update System

```bash
sudo apt update
```

### Step 2: Install Snort

```bash
sudo apt install snort -y
```

### Step 3: Verify Installation

```bash
snort -V
```

---

## 📂 Configuration Files

Main configuration file:

```
/etc/snort/snort.conf
```

Custom rule file:

```
/etc/snort/rules/local.rules
```

Ensure the following line exists in snort.conf:

```
include $RULE_PATH/local.rules
```

---

## 🧠 Custom Rules Created

### 🔹 ICMP Detection Rule

```bash
alert icmp any any -> any any (msg:"ICMP Ping Detected"; sid:1000001; rev:1;)
```

Purpose:
Detects ping-based reconnaissance attempts.

---

### 🔹 TCP SYN Scan Detection Rule

```bash
alert tcp any any -> any any (flags:S; msg:"Possible SYN Scan Detected"; sid:1000002; rev:1;)
```

Purpose:
Detects potential Nmap SYN scan activity.

---

### 🔹 IPS Blocking Rule (ICMP)

```bash
drop icmp any any -> any any (msg:"ICMP Blocked"; sid:1000003; rev:1;)
```

Purpose:
Blocks ICMP traffic in IPS inline mode.

---

## 🚨 Running Snort

### IDS Mode (Detection Only)

```bash
sudo snort -A console -c /etc/snort/snort.conf -i eth0
```

Result:
Snort monitors traffic and generates alerts.

---

### IPS Mode (Inline Blocking)

```bash
sudo snort -Q --daq afpacket -c /etc/snort/snort.conf -i eth0
```

Result:
Malicious traffic is automatically dropped.

---

## 🔍 Attack Simulation

### ICMP Ping Test

Executed from Kali Linux:

```bash
ping <target-ip>
```

Result:

* Detected in IDS mode
* Blocked in IPS mode

---

### Nmap SYN Scan Test

Executed from Kali Linux:

```bash
nmap -sS <target-ip>
```

Result:
Detected as potential reconnaissance activity.

---

## 📊 Log Analysis

Snort Alert Log Location:

```
/var/log/snort/alert
```

View logs:

```bash
cat /var/log/snort/alert
```

Sample Output:

```
[**] [1:1000001:1] ICMP Ping Detected [**]
```

This demonstrates real-time detection and logging capability.

---

## 🔐 Security Improvements Implemented

* Custom rule creation
* Inline traffic blocking
* Attack simulation testing
* Log verification and monitoring

---

## 📈 Skills Demonstrated

* Network Security Monitoring
* IDS/IPS Deployment
* Linux System Administration
* Snort Rule Writing
* Attack Simulation
* Log Analysis
* Cybersecurity Lab Environment Setup

---

## 🏁 Project Outcome

This project successfully demonstrates practical implementation of an enterprise-level intrusion detection and prevention system using Snort in a virtualized lab environment.

The system was capable of:

✔ Detecting reconnaissance attempts
✔ Blocking malicious ICMP traffic
✔ Logging suspicious network activity
✔ Simulating real-world SOC operations

---

## 📌 Future Improvements

* Integration with SIEM solution
* ELK Stack log visualization
* Email alert notifications
* Detection of brute-force attacks
* Web attack detection rules

---

## 📚 References

* Official Snort Documentation
* Network Security Best Practices

---

# 🔥 Final Notes

This project reflects hands-on experience in defensive cybersecurity and demonstrates readiness for entry-level SOC Analyst roles.

Tell me what’s next, Tariq 👨‍💻🔥
