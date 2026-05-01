Concepts to know for ALL Security Engineers:

Computer Systems Concepts:

* OS Rings (Ring 0–3, kernel vs user space)
* Memory Management schemes
  + Paging
  + Segmentation
  + Memory Protection Units (MPU)
* Virtual Memory
  + Page tables
  + TLB (Translation Lookaside Buffer)
  + Swap space
* Process lifecycle (creation, scheduling, termination)
* Process scheduling algorithms (FIFO, Round Robin, CFS)
* Inter-Process Communication (IPC)
  + Pipes
  + Sockets
  + Shared Memory
  + Signals
  + Message Queues
* Threads vs Processes
* Concurrency and race conditions
* Stack and Heap memory layout
* Buffer overflows and memory corruption
* System calls and their role in security
* File system permissions and ACLs
* Privilege escalation vectors (SUID/SGID, DLL hijacking)
* Secure boot and firmware security (UEFI, TPM)
* Containers vs Virtual Machines (isolation model)
* Hypervisor types (Type 1 vs Type 2)

Computer Networks Concepts:

* Networking Hardware
  + Switches (L2 and L3)
  + Bridges
  + Routers
  + Hubs
  + Firewalls
  + Load Balancers
  + Network Taps and SPANs
* OSI Model (all 7 layers and their security implications)
* TCP/IP model
* IP Addressing
  + IPv4 vs IPv6
  + Subnetting and CIDR
  + Private vs public address space (RFC 1918)
  + NAT and PAT
* Core Protocols
  + TCP (three-way handshake, connection states, flags)
  + UDP
  + ICMP
  + ARP and ARP spoofing
  + DNS (resolution process, record types: A, AAAA, MX, CNAME, TXT, NS, PTR)
  + DHCP
  + HTTP/HTTPS
  + SMTP, IMAP, POP3
  + FTP vs SFTP vs FTPS
  + SSH
  + SNMP
  + NTP
* TLS/SSL
  + TLS handshake process
  + Certificate chain of trust
  + Certificate authorities (CAs) and PKI
  + Common TLS vulnerabilities (BEAST, POODLE, Heartbleed)
  + mTLS (mutual TLS)
* VPNs
  + IPsec (IKEv1/IKEv2, ESP, AH)
  + OpenVPN
  + WireGuard
  + Split tunneling
* Network segmentation (VLANs, DMZ, air-gapping)
* Software-Defined Networking (SDN)
* BGP and routing security (BGP hijacking)
* Wireless security
  + WPA2 vs WPA3
  + WEP weaknesses
  + Evil twin attacks
  + Deauthentication attacks

Security Fundamentals:

* Confidentiality, Integrity, Availability (CIA Triad)
* Defense in Depth
* Principle of Least Privilege
* Separation of Duties
* Fail-safe defaults
* Open design (Kerckhoffs's principle)
* Authorization
  + Role-Based Access Control (RBAC)
  + Attribute-Based Access Control (ABAC)
  + Mandatory Access Control (MAC)
  + Discretionary Access Control (DAC)
* Authentication
  + Password-based authentication and storage (salting, bcrypt, Argon2)
  + Multi-Factor Authentication (MFA) types: TOTP, FIDO2, hardware tokens
  + Biometric authentication
  + Certificate-based authentication
* SSO (Single Sign-On)
  + SAML 2.0
  + OAuth 2.0
  + OpenID Connect (OIDC)
  + LDAP and Active Directory integration
* Identity Federation
* Session management (tokens, cookies, session fixation)
* Cryptography fundamentals
  + Symmetric encryption (AES-128, AES-256, block vs stream ciphers)
  + Asymmetric encryption (RSA, ECC, Diffie-Hellman key exchange)
  + Hashing (SHA-256, SHA-3, MD5 weaknesses)
  + Digital signatures
  + HMAC
  + Key management and key derivation functions (KDF)
  + Random number generation (CSPRNG)
  + Post-quantum cryptography basics
* Risk Management
  + Risk = Likelihood × Impact
  + Risk acceptance, mitigation, transfer, avoidance
  + Qualitative vs quantitative risk assessment
* Security Controls
  + Preventive, Detective, Corrective, Compensating
  + Technical, Administrative, Physical
* Vulnerability lifecycle (discovery, disclosure, patching)
* CVE, CWE, and CVSS scoring
* Patch management
* Security Policies and Standards (AUP, password policies, data classification)

Common Attacks and Their Defenses:

* Smurf Attack
* DoS (Denial of Service)
* DDoS (Distributed Denial of Service)
  + Volumetric attacks
  + Protocol attacks
  + Application layer (L7) attacks
  + Defenses: rate limiting, scrubbing centers, anycast routing
* Slowloris
* Kaminsky Attack (DNS cache poisoning)
* Man-in-the-Middle (MitM)
  + ARP poisoning
  + SSL stripping
  + BGP hijacking
* Replay Attacks
* Pass-the-Hash
* Pass-the-Ticket (Kerberos)
* Golden Ticket and Silver Ticket attacks
* Credential stuffing
* Brute force and password spraying
* Rainbow table attacks and defense (salting)
* SQL Injection
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Phishing, spear phishing, and vishing
* Social engineering
* Supply chain attacks
* Ransomware
* Rootkits and bootkits
* Fileless malware
* Insider threat

Frameworks:

* NIST Cybersecurity Framework (CSF) — Identify, Protect, Detect, Respond, Recover
* NIST SP 800-53 (Security and Privacy Controls)
* NIST SP 800-171 (CUI protection)
* MITRE ATT&CK Framework (Tactics, Techniques, Procedures)
* MITRE D3FEND
* CIS Controls (v8)
* ISO/IEC 27001 and 27002
* SOC 2 (Trust Service Criteria)
* PCI DSS
* HIPAA Security Rule
* GDPR (data protection principles)
* OWASP (Top 10, ASVS, Testing Guide)
* Cyber Kill Chain (Lockheed Martin)
* Diamond Model of Intrusion Analysis

Network Security:

* Kerberos (AS-REQ, TGT, TGS, service tickets)
* RADIUS and TACACS+
* 802.1X (port-based NAC)
* Network Access Control (NAC)
* Firewall types (stateless, stateful, NGFW, WAF)
* Intrusion Detection Systems (IDS) vs Intrusion Prevention Systems (IPS)
* Proxy servers (forward proxy, reverse proxy, transparent proxy)
* Network segmentation and micro-segmentation
* Zero Trust Network Access (ZTNA)
* DNS security (DNSSEC, DNS over HTTPS, DNS over TLS, Sinkholing)
* Email security (SPF, DKIM, DMARC)
* Network monitoring and packet analysis (Wireshark, tcpdump)
* NetFlow and traffic analysis
* Honeypots and honeynets

Scripting and Automation:

* Python basics for security automation
  + File and log parsing
  + API interaction (requests library)
  + Regular expressions
  + Building simple scanners and parsers
* Bash scripting for security tasks
* PowerShell for Windows security tasks
* Git and version control basics
* REST API concepts and security
* JSON and data parsing

Security Engineering Practices:

* Security requirements gathering
* Secure design principles
* Security code review basics
* Threat modeling (understanding the concepts applicable to all domains)
* Vulnerability scanning (Nessus, OpenVAS)
* Asset inventory and management
* Change management and its security implications
* Incident detection concepts
* Log management and correlation basics
* Security metrics and KPIs
* Communication skills: writing security findings for technical and non-technical audiences
* Staying current: reading CVE advisories, security blogs, threat intel feeds

Relevant Books:

* [The Infosec Handbook: An Introduction to Information Security](https://www.amazon.com/InfoSec-Handbook-Introduction-Information-Security/dp/1430263822)
* [Security Engineering by Ross Anderson](https://www.amazon.com/Security-Engineering-Building-Dependable-Distributed/dp/1119642787)
* [The Web Application Hacker's Handbook](https://www.amazon.com/Web-Application-Hackers-Handbook-Exploiting/dp/1118026470)
* [CompTIA Security+ Study Guide](https://www.amazon.com/CompTIA-Security-Study-Guide-SY0-701/dp/1394211449)
* [Cybersecurity and Cyberwar: What Everyone Needs to Know](https://www.amazon.com/Cybersecurity-Cyberwar-Everyone-Needs-Know/dp/019933606X)

Relevant Certifications (by level):

* Entry: CompTIA Security+, CompTIA Network+
* Intermediate: CompTIA CySA+, GIAC GSEC, CEH
* Advanced: CISSP, CISM, GIAC GCIA, OSCP
