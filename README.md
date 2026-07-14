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

