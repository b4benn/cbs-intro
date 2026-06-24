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





