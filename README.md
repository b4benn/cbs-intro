# Cybersecurity Course Notes

Notes and progress tracking for the Google Cybersecurity 
Professional Certificate.

## Progress
- ✅ Course 1: Foundations of Cybersecurity
- 🔄 Course 2: Play It Safe (in progress)

## What I'm learning
- Security frameworks and controls
- Risk management
- Network security basics



## Portfolio Activity: Botium Toys Security Audit

Completed an internal IT security audit for a fictional company (Botium Toys) 
as part of the Google Cybersecurity Professional Certificate.

*What I did:*
- Reviewed the scope, goals, and risk assessment report
- Applied the NIST Cybersecurity Framework (CSF) to evaluate existing controls
- Completed a controls and compliance checklist covering:
- Administrative/Managerial controls (least privilege, password policies, 
    separation of duties, disaster recovery)
- Technical controls (firewall, IDS/IPS, encryption, backups, antivirus) 
 - Physical/Operational controls
- Identified gaps in encryption, access control, and backup/disaster recovery
- Provided recommendations to improve the company's security posture

*Key finding:* Risk score of 8/10 due to missing controls around data 
encryption, access management, and incident recovery.

📄 View completed checklist](Control and compliance 


# Google Cybersecurity Professional Certificate Portfolio
**Benjamin Nkansah Peprah** | Junior SOC Analyst (In Training)
📍 Kiel, Germany | GitHub: b4benn

## Progress
| Course | Title | Status |
|--------|-------|--------|
| 1 | Foundations of Cybersecurity | ✅ Complete |
| 2 | Play It Safe: Manage Security Risks | ✅ Complete |
| 3 | Connect and Protect: Networks and Network Security | 🔄 In Progress |
| 4-8 | Coming Soon | ⏳ Pending |

## Skills Gained So Far
- NIST Cybersecurity Framework (CSF)
- Security risk assessment
- Security audits and controls evaluation
- Incident response playbooks
- SIEM tool fundamentals
- Threat and vulnerability identification


----------------------------------//---/-----------


# Security Risk Assessment 

 Risk Assessment
**Framework Applied:** NIST Cybersecurity Framework (CSF)
**Prepared by:** Benjamin Nkansah Peprah
**Date:** June 2026

---

## Company Overview
**Company:** Botium Toys (Practice Scenario)
**Industry:** Retail / E-commerce
**Size:** Small business with growing online presence

---

## Asset Inventory
| Asset | Description |
|-------|-------------|
| On-premises equipment | Office computers, servers, network hardware |
| Employee devices | Laptops, mobile phones |
| Customer data | PII, payment card information |
| Internal systems | Accounting, HR, e-commerce database |
| Internet access | Business broadband connection |

---

## Threat Identification
| Threat | Likelihood | Notes |
|--------|-----------|-------|
| Phishing attacks | High | Employees lack security awareness training |
| Ransomware | Medium | No proper backup procedures in place |
| Unauthorized access | High | Weak password policies identified |
| Data breach | High | PII and payment data insufficiently protected |
| Insider threat | Low | Small team, limited access controls |

---

## NIST CSF Assessment

### 1. Identify
- No complete asset inventory exists
- Data classification policy is missing
- Risk management process is informal

### 2. Protect
- No encryption on customer payment data
- Password policy does not meet minimum standards
- No employee cybersecurity awareness training
- Least privilege access not enforced

### 3. Detect
- No SIEM tool currently in use
- No intrusion detection system (IDS) in place
- Security monitoring is reactive, not proactive

### 4. Respond
- No formal incident response plan exists
- No defined communication plan for breaches
- No designated incident response team

### 5. Recover
- No tested backup and recovery procedures
- No business continuity plan documented

---

## Risk Score
| Category | Score (1-10) | Priority |
|----------|-------------|---------|
| Access Controls | 8 | 🔴 High |
| Data Protection | 9 | 🔴 Critical |
| Incident Response | 7 | 🔴 High |
| Monitoring | 6 | 🟡 Medium |
| Recovery | 7 | 🔴 High |

---

## Recommendations
1. Implement least privilege access controls immediately
2. Encrypt all customer PII and payment data
3. Deploy a SIEM tool for real-time monitoring
4. Establish a formal incident response playbook
5. Conduct regular employee security awareness training
6. Create and test a backup and recovery plan




# Incident Response Playbook — Phishing Attack
**Prepared by:** Benjamin Nkansah Peprah
**Date:** June 2026
**Framework:** NIST SP 800-61

---

## Scenario
A Botium Toys employee receives and clicks a phishing email
containing a malicious link. Credentials may be compromised.

---

## Phase 1 — Preparation
- Ensure all staff have completed phishing awareness training
- Maintain an up-to-date contact list for incident response team
- Confirm SIEM alerts are active for suspicious login attempts
- Verify that email filtering tools are in place

---

## Phase 2 — Detection & Analysis
| Step | Action |
|------|--------|
| 1 | Employee reports suspicious email to IT/Security team |
| 2 | Analyst reviews email headers and embedded links |
| 3 | Check SIEM logs for any unusual login activity |
| 4 | Determine if credentials were entered on malicious site |
| 5 | Identify all affected accounts and systems |
| 6 | Assign severity level: Low / Medium / High / Critical |

---

## Phase 3 — Containment
**Short-term:**
- Immediately disable the affected user account
- Block the malicious URL at the firewall level
- Isolate affected device from the network

**Long-term:**
- Force password reset for all potentially affected accounts
- Enable multi-factor authentication (MFA) on all accounts
- Notify relevant stakeholders of the incident

---

## Phase 4 — Eradication
- Remove any malicious files or software from affected devices
- Scan all systems for indicators of compromise (IOCs)
- Patch any vulnerabilities exploited during the attack
- Confirm no persistence mechanisms remain on the network

---

## Phase 5 — Recovery
- Restore affected accounts with new secure credentials
- Monitor systems closely for 72 hours post-incident
- Confirm business operations are fully restored
- Document all actions taken during the incident

---

## Phase 6 — Post-Incident Review
| Question | Notes |
|----------|-------|
| How was the phishing email delivered? | |
| What controls failed or were missing? | |
| How long did detection take? | |
| What improvements are needed? | |

**Lessons learned report to be completed within 5 business days.**

---

## Severity Classification
| Level | Criteria |
|-------|---------|
| Low | Phishing email received, no link clicked |
| Medium | Link clicked, no credentials entered |
| High | Credentials entered, single account affected |
| Critical | Multiple accounts compromised, data exfiltrated |



# DNS/ICMP Traffic Analysis — Incident Investigation

**Type:** Network traffic analysis / incident report
**Tools used:** tcpdump (network protocol analyzer)
**Skills demonstrated:** packet log interpretation, DNS/UDP/ICMP protocol analysis, root cause identification, incident reporting

## Scenario

Multiple customers reported they were unable to access a client website (`yummyrecipesforme.com`), seeing a “destination port unreachable” error. As the analyst on call, I captured live traffic with tcpdump while reproducing the issue to identify which protocol and port were involved.

## Traffic Log Summary

```
13:24:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A? yummyrecipesforme.com. (24)
13:24:36.098564 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 udp port 53 unreachable, length 254

13:26:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A? yummyrecipesforme.com. (24)
13:27:15.934126 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 udp port 53 unreachable, length 320

13:28:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A? yummyrecipesforme.com. (24)
13:28:50.022967 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 udp port 53 unreachable, length 150
```

## Analysis

The client machine (`192.51.100.15`) sent UDP DNS queries to the DNS server (`203.0.113.2`), requesting an A record to resolve `yummyrecipesforme.com` to an IP address. Each of the three attempts was met with an ICMP error response: **“udp port 53 unreachable.”**

Port 53 is the standard port for DNS service. Because the DNS server is not responding on that port, the browser never receives an IP address to connect to — the failure happens at the **DNS resolution stage**, before any HTTPS connection to the actual web server is even attempted.

**Root cause (most likely):** the DNS server’s service on port 53 is down, misconfigured, or blocked by a firewall rule, preventing it from answering DNS queries.

## Incident Report

|                       |                                                                                                             |
|-----------------------|-------------------------------------------------------------------------------------------------------------|
|**Time occurred**      |First observed 13:24:32; recurred at 13:26:32 and 13:28:32                                                   |
|**How discovered**     |Customer reports of “destination port unreachable” errors accessing the site                                 |
|**Investigation steps**|Reproduced the error, then captured traffic with tcpdump during a retry                                      |
|**Key finding**        |Repeated UDP DNS queries to 203.0.113.2 answered with ICMP “port 53 unreachable”                             |
|**Suspected cause**    |DNS service down/misconfigured, or port 53 blocked by firewall on the DNS server                             |
|**Next steps**         |Verify DNS service status on 203.0.113.2, review firewall rules for port 53, confirm no recent config changes|

-----

*Part of my cybersecurity learning portfolio — Google Cybersecurity Professional Certificate, Course 2: Play It Safe.*



 



```

---