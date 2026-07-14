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




# Cybersecurity Incident Report

## Section 1: Identify the type of attack that may have caused this network interruption

**One potential explanation for the website's connection timeout error message is:**

- **The logs show that:**
    - A single source IP address, `203.0.113.0`, is sending a continuous and overwhelming number of TCP `[SYN]` requests to the web server (port 443) at `192.0.2.1`.
    - The log entries show repeated SYN packets from `203.0.113.0` to the server without completing the three-way handshake, as indicated by the lack of subsequent ACK packets from that source to finalize the connections.
    - This pattern is visible across multiple log entries (e.g., lines 52, 57, 59, 61, 66, 68, 70, 72, 74, 76, 78, 80, 81, 82).

- **This event could be:**
    - A **SYN Flood attack**, which is a specific type of **Denial of Service (DoS)** attack.
    - The attacker sends a high volume of `[SYN]` packets, often with spoofed IP addresses, to overwhelm the server's ability to process legitimate connection requests.
    - While the logs show a single source IP, the attacker could be using this IP as a spoofed address or launching a DoS attack from a single compromised machine.

---

## Section 2: Explain how the attack is causing the website to malfunction

**When website visitors try to establish a connection with the web server, a three-way handshake occurs using the TCP protocol. Explain the three steps of the handshake:**

1.  **SYN:** The client sends a `[SYN]` packet to the server to initiate a connection request.
2.  **SYN-ACK:** The server responds with a `[SYN, ACK]` packet to acknowledge the request and synchronize its own sequence number.
3.  **ACK:** The client sends a final `[ACK]` packet to acknowledge the server's response, establishing a full connection.

**Explain what happens when a malicious actor sends a large number of SYN packets all at once:**

- The attacker's SYN packets cause the web server to allocate resources (memory and processing power) for each half-open connection.
- The server sends a `[SYN, ACK]` reply and then waits for the final `[ACK]` to complete the handshake.
- Since the attacker never sends the final ACK, these connections remain in a half-open state, consuming all available server resources.
- This overwhelms the server, making it unable to respond to legitimate SYN requests, resulting in connection timeouts.

**Explain what the logs indicate and how that affects the server:**

- The logs show a flood of `[SYN]` packets from `203.0.113.0`.
- The server attempts to respond to each with a `[SYN, ACK]` but many of these requests are not completed.
- This is evident in the log where legitimate client requests (e.g., from `198.51.100.23` or `198.51.100.14`) take a long time to be processed.
- The server becomes so overwhelmed that it eventually cannot handle legitimate traffic, leading to **HTTP 504 Gateway Timeout** errors (as seen at line 77) for legitimate visitors attempting to access `sales.html`.
- The attack is successfully denying service to legitimate employees and customers.

---

## Section 3: Evidence from Wireshark Log
```markdown
# Cybersecurity Incident Report

## Section 1: Identify the type of attack that may have caused this network interruption

**One potential explanation for the website's connection timeout error message is:**

- **The logs show that:**
    - A single source IP address, `203.0.113.0`, is sending a continuous and overwhelming number of TCP `[SYN]` requests to the web server (port 443) at `192.0.2.1`.
    - The log entries show repeated SYN packets from `203.0.113.0` to the server without completing the three-way handshake, as indicated by the lack of subsequent ACK packets from that source to finalize the connections.
    - This pattern is visible across multiple log entries (e.g., lines 52, 57, 59, 61, 66, 68, 70, 72, 74, 76, 78, 80, 81, 82).

- **This event could be:**
    - A **SYN Flood attack**, which is a specific type of **Denial of Service (DoS)** attack.
    - The attacker sends a high volume of `[SYN]` packets, often with spoofed IP addresses, to overwhelm the server's ability to process legitimate connection requests.
    - While the logs show a single source IP, the attacker could be using this IP as a spoofed address or launching a DoS attack from a single compromised machine.

---

## Section 2: Explain how the attack is causing the website to malfunction

**When website visitors try to establish a connection with the web server, a three-way handshake occurs using the TCP protocol. Explain the three steps of the handshake:**

1.  **SYN:** The client sends a `[SYN]` packet to the server to initiate a connection request.
2.  **SYN-ACK:** The server responds with a `[SYN, ACK]` packet to acknowledge the request and synchronize its own sequence number.
3.  **ACK:** The client sends a final `[ACK]` packet to acknowledge the server's response, establishing a full connection.

**Explain what happens when a malicious actor sends a large number of SYN packets all at once:**

- The attacker's SYN packets cause the web server to allocate resources (memory and processing power) for each half-open connection.
- The server sends a `[SYN, ACK]` reply and then waits for the final `[ACK]` to complete the handshake.
- Since the attacker never sends the final ACK, these connections remain in a half-open state, consuming all available server resources.
- This overwhelms the server, making it unable to respond to legitimate SYN requests, resulting in connection timeouts.

**Explain what the logs indicate and how that affects the server:**

- The logs show a flood of `[SYN]` packets from `203.0.113.0`.
- The server attempts to respond to each with a `[SYN, ACK]` but many of these requests are not completed.
- This is evident in the log where legitimate client requests (e.g., from `198.51.100.23` or `198.51.100.14`) take a long time to be processed.
- The server becomes so overwhelmed that it eventually cannot handle legitimate traffic, leading to **HTTP 504 Gateway Timeout** errors (as seen at line 77) for legitimate visitors attempting to access `sales.html`.
- The attack is successfully denying service to legitimate employees and customers.

---

## Section 3: Evidence from Wireshark Log

```

Log Analysis Summary:

Line Source Destination Info Analysis
47 198.51.100.23 192.0.2.1 TCP SYN to port 443 Legitimate SYN request from employee
48 192.0.2.1 198.51.100.23 TCP SYN-ACK Server responds to legitimate request
49 198.51.100.23 192.0.2.1 TCP ACK Handshake completes for legitimate user
52 203.0.113.0 192.0.2.1 TCP SYN to port 443 Malicious SYN from attacker
53 192.0.2.1 203.0.113.0 TCP SYN-ACK Server responds (wasting resources)
57 203.0.113.0 192.0.2.1 TCP SYN Attacker sends another SYN (no ACK sent back)
59 203.0.113.0 192.0.2.1 TCP SYN Continued SYN flood
61 203.0.113.0 192.0.2.1 TCP SYN SYN flood continues
66 203.0.113.0 192.0.2.1 TCP SYN Server resources being depleted
68 203.0.113.0 192.0.2.1 TCP SYN Attack intensifies
70 203.0.113.0 192.0.2.1 TCP SYN Half-open connections accumulate
72 203.0.113.0 192.0.2.1 TCP SYN Server approaching capacity
74 203.0.113.0 192.0.2.1 TCP SYN Attack continues unabated
76 203.0.113.0 192.0.2.1 TCP SYN Server resources exhausted
77 192.0.2.1 198.51.100.5 HTTP 504 Gateway Timeout Legitimate user receives timeout error
78 203.0.113.0 192.0.2.1 TCP SYN Attacker persists despite server issues
80-82 203.0.113.0 192.0.2.1 TCP SYN (multiple) Simultaneous SYN packets sent

```

---

## Section 4: Impact and Recommendations

**Impact on Organization:**
- Employees cannot access the sales webpage to search for vacation packages for customers
- Customers cannot access the company website to view sales and promotions
- Revenue loss due to inability to process new bookings
- Damage to company reputation and customer trust
- Potential loss of business to competitors
- IT resources diverted to incident response and recovery

**Recommended Mitigation Strategies:**
1. **SYN Cookies:** Enable SYN cookies on the web server to handle half-open connections more efficiently
2. **Rate Limiting:** Implement rate limiting on the firewall to restrict the number of SYN packets from a single IP
3. **Intrusion Prevention System (IPS):** Deploy IPS rules to detect and block SYN flood patterns
4. **Load Balancer:** Use a load balancer to distribute traffic across multiple servers
5. **DDoS Protection Service:** Consider cloud-based DDoS protection services (e.g., Cloudflare, AWS Shield)
6. **Firewall Rules:** Already implemented (blocked `203.0.113.0`), but need more dynamic blocking capabilities
7. **Network Monitoring:** Enhanced monitoring to detect unusual traffic patterns early
8. **Incident Response Plan:** Develop and test incident response procedures for DDoS attacks

---

**Report Completed By:** Security Analyst
**Date:** 2026-07-14
**Incident Status:** Under Investigation - Server Offline for Recovery
```
