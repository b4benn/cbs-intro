# Security Risk Assessment
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







