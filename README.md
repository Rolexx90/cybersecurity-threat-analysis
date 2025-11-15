# Cybersecurity Threat Analysis & Network Packet Investigation

> **Network security analysis using Wireshark to identify and document real-world attack patterns**

[![Wireshark](https://img.shields.io/badge/Tool-Wireshark-1679A7?style=flat&logo=wireshark&logoColor=white)](https://www.wireshark.org/)
[![Network Analysis](https://img.shields.io/badge/Skill-Network%20Analysis-blue)](.)
[![Threat Detection](https://img.shields.io/badge/Skill-Threat%20Detection-red)](.)

---

## 📋 Project Overview

This project documents a comprehensive network security analysis conducted during my cybersecurity internship. Using Wireshark, I analyzed simulated network traffic to detect, document, and recommend mitigations for multiple attack patterns.

**Duration:** April - May 2025  
**Context:** Security assessment task at House of Couton Pvt. Ltd  
**Recognition:** Received highest supervisor feedback; report used as reference material

---

## 🎯 Key Achievements

- **Analyzed 500+ network packets** using advanced Wireshark filters
- **Detected 4 active attack patterns** in simulated traffic
- **Produced 15-page technical report** with methodology, findings, and recommendations
- **Documented mitigation controls** aligned with industry frameworks (OWASP, NIST)
- **Researched 5 critical attack vectors** with academic and industry sources

---

## 🔍 Attacks Identified & Analyzed

### 1. ARP Spoofing (Man-in-the-Middle Attack)
**Detection Method:** `arp` filter in Wireshark  
**Key Indicators:**
- Repeated ARP replies mapping multiple IPs to same MAC address
- MAC address `00:0d:b7:26:4a:74` claiming multiple IP addresses
- High frequency of ARP broadcasts indicating ARP table poisoning

**Impact:** Traffic redirected through attacker device for interception  
**Mitigation:** Dynamic ARP Inspection (DAI), static ARP entries for critical systems

---

### 2. SYN Flood (Denial of Service)
**Detection Method:** `tcp.flags.syn==1 && tcp.flags.ack==0` filter  
**Key Indicators:**
- 100+ SYN packets from source IP `10.1.17.215` (likely spoofed)
- No corresponding ACK responses (half-open connections)
- Primary targets: Port 443 (HTTPS) and Port 80 (HTTP)

**Impact:** Server resources exhausted via connection queue backlog  
**Mitigation:** SYN cookies, increased backlog queue, firewall DoS protection

---

### 3. UDP Flood with ICMP Backscatter
**Detection Method:** `icmp.type == 3 && icmp.code == 3` and UDP flow analysis  
**Key Indicators:**
- 20 UDP packets from `10.1.17.215` to `10.1.17.2`
- ICMP "Destination unreachable (Port unreachable)" responses
- One-way communication pattern (no replies from target)

**Impact:** Network reconnaissance and potential service disruption  
**Mitigation:** ICMP rate limiting, firewall filtering of malicious UDP, IDS signatures

---

### 4. HTTP-Based Command & Control (C2)
**Detection Method:** HTTP User-Agent analysis, `http.request.method == "HEAD"`  
**Key Indicators:**
- Microsoft BITS/7.8 User-Agent (commonly abused by malware)
- Obfuscated query strings in HEAD/GET requests
- Target: `msedge.b.tlu.dl.delivery.mp.microsoft.com`
- No browser activity (automated background service)

**Impact:** Covert payload delivery masquerading as legitimate traffic  
**Mitigation:** Monitor suspicious BITS traffic, filter via GPO if unused, detect repetitive HEAD/GET patterns

---

## 🛠️ Technical Skills Demonstrated

**Tools & Technologies:**
- Wireshark (packet capture and analysis)
- TCP/IP protocol analysis
- Network traffic filtering and correlation
- Payload inspection techniques

**Security Concepts:**
- Attack pattern recognition
- Indicators of Compromise (IoCs)
- Network protocol vulnerabilities
- Threat detection methodologies

**Professional Skills:**
- Technical documentation and reporting
- Security research (15+ academic/industry sources)
- Mitigation strategy development
- Communication of complex technical concepts

---

## 📊 Methodology

**Analysis Process:**
1. **Initial Scanning:** Reviewed overall traffic patterns and protocol distribution
2. **Filter Application:** Used targeted Wireshark filters to isolate anomalies
   - ARP: `arp`
   - SYN Flood: `tcp.flags.syn==1 && tcp.flags.ack==0`
   - UDP Flood: `icmp.type == 3 && icmp.code == 3`
   - C2 Traffic: `http.request && http.user_agent contains "BITS"`
3. **Behavioral Analysis:** Identified unusual host behaviors and repetitive patterns
4. **Payload Inspection:** Examined packet contents for malicious indicators
5. **Cross-Correlation:** Mapped timing and protocol usage to confirm attack hypotheses

---

## 📄 Report Contents

**Part A: Research Report**
- Man-in-the-Middle (MITM) Attacks
- Denial-of-Service (DoS) Attacks
- SQL Injection
- Zero-Day Exploits
- DNS Tunneling

**Part B: Practical Network Packet Analysis**
- Detailed methodology
- Attack detection and documentation (4 attacks)
- Packet-level analysis with Wireshark screenshots
- Mitigation recommendations
- Industry references (Verizon DBIR, OWASP, Cisco Talos, etc.)

---

## 🎓 Learning Outcomes

This project strengthened my understanding of:
- **Practical threat detection** in real-world network traffic
- **Wireshark proficiency** including advanced filtering and behavioral analysis
- **Attack methodologies** and their network-level indicators
- **Security documentation** best practices
- **Mitigation strategies** aligned with industry frameworks

---

## 🔗 Related Projects

- [ISO 27001 Incident Response Playbook](https://github.com/Rolexx90/cybersecurity-incident-playbooks) - Phishing attack response procedures

---

## 📚 References & Frameworks

- **OWASP Top 10** - Web application security risks
- **NIST Cybersecurity Framework** - Security best practices
- **Verizon DBIR 2023** - Data breach statistics and trends
- **Cisco Talos Intelligence** - Threat research
- Academic papers on MITM attacks, DoS defense, and DNS tunneling

*Full bibliography available in the report PDF*

---

## 👤 About

**Vishal Panda**  
Cybersecurity Student | VIT Bhopal University  
Expected Graduation: May 2026

**Connect with me:**
- 📧 Email: vishal99.business@gmail.com
- 💼 LinkedIn: [linkedin.com/in/VishalPanda](https://linkedin.com/in/vishalpanda09)
- 🌐 GitHub: [Rolexx90](https://github.com/Rolexx90)

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## ⭐ Acknowledgments

This analysis was completed as part of my cybersecurity internship at House of Couton Pvt. Ltd. Special thanks to my supervisor for guidance and feedback.

---

**🔒 Interested in cybersecurity? Feel free to explore the report and reach out with questions!**
```
