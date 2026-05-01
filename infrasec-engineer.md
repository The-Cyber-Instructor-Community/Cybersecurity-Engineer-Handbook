Here is the list of concepts you need to learn to become an awesome Infrastructure security engineer.

Basics:

* Defense in Depth
  + Layered security controls (perimeter → network → host → application → data)
  + No single point of failure in security design
* Principle of Least Privilege
  + User access rights
  + Service account permissions
  + Just-in-time (JIT) access provisioning
* Endpoint Security Policies
  + Antivirus and anti-malware (signature vs behavioral)
  + Endpoint Detection and Response (EDR)
  + Application allowlisting and blocklisting
  + Host-based firewall configuration
  + USB and peripheral device control
  + Full disk encryption (BitLocker, FileVault, LUKS)
  + Patch management enforcement
* Network Security Policies (Corporate and Production)
  + Network segmentation strategy (flat network risks)
  + VLAN design and inter-VLAN routing controls
  + DMZ design (dual-firewall vs single-firewall)
  + East-west vs north-south traffic controls
  + Micro-segmentation
  + Firewall rule management and lifecycle (rule review, rule cleanup)
  + Network access control (NAC) enforcement
* Vulnerability Management and Patching
  + Vulnerability scanning cadence (internal and external)
  + Patch prioritization using CVSS and threat intelligence
  + Patch testing before production deployment
  + Compensating controls for unpatchable systems
  + Vulnerability tracking and SLA management
  + Attack surface reduction
* Data Security
  + Data classification (Public, Internal, Confidential, Restricted)
  + Data at rest encryption
  + Data in transit encryption (TLS everywhere)
  + Data Loss Prevention (DLP) tools and policies
  + Database security (encryption, access control, query logging)
  + Backup security (encrypted backups, offsite storage, backup integrity testing)
  + Data retention and secure deletion (NIST 800-88 media sanitization)
* Multi-Factor Authentication (MFA)
  + MFA types: TOTP (authenticator apps), FIDO2/WebAuthn (hardware keys), SMS (weak)
  + Phishing-resistant MFA (FIDO2, passkeys)
  + MFA enforcement for privileged accounts and remote access
  + MFA bypass techniques and mitigations (SIM swapping, MFA fatigue attacks)

Identity and Access Management (IAM):

* Identity lifecycle (provisioning, role changes, deprovisioning)
* User account types
  + Standard users
  + Privileged/admin accounts
  + Service accounts
  + Break-glass/emergency accounts
* Privileged Access Management (PAM)
  + Privileged Account and Session Management (PASM)
  + Just-in-time (JIT) privilege elevation
  + PAM tools: CyberArk, BeyondTrust, HashiCorp Boundary
  + Privileged access workstations (PAWs)
* Directory Services
  + Active Directory (AD) architecture (domains, forests, trusts, OUs, GPOs)
  + AD security hardening (disabling LLMNR/NBT-NS, SMB signing, LDAP signing)
  + Tiered administration model (Tier 0/1/2)
  + AD attack paths: Kerberoasting, AS-REP Roasting, DCSync, Pass-the-Hash, NTLM relay
  + BloodHound for AD attack path analysis and remediation
  + Group Policy Object (GPO) security configuration
  + Protected Users security group
  + LAPS (Local Administrator Password Solution)
  + Azure AD / Entra ID basics
* Single Sign-On (SSO) and Federation
  + SAML 2.0
  + OAuth 2.0 and OIDC
  + Active Directory Federation Services (ADFS)
  + Okta, Azure AD, Google Workspace as IdP

Network Security:

* Firewall types and configuration
  + Stateless packet filters
  + Stateful inspection firewalls
  + Next-Generation Firewalls (NGFW) (application-aware, IPS, SSL inspection)
  + Web Application Firewalls (WAF)
  + Firewall rule best practices (allowlist by default, deny all inbound, log drops)
  + Firewall high availability (active-passive, active-active)
* Network Segmentation
  + VLAN design and security
  + Subnetting for security isolation
  + Screened subnet (DMZ) architecture
  + Microsegmentation with SDN or host-based firewalls
* Intrusion Detection and Prevention Systems (IDS/IPS)
  + Placement (network tap vs inline)
  + Signature vs anomaly-based detection
  + Tuning to reduce false positives
* Network Access Control (NAC)
  + 802.1X port-based authentication
  + Pre-admission vs post-admission NAC
  + Device health checks (posture assessment)
  + Guest network isolation
* VPN and Remote Access Security
  + IPsec VPN (site-to-site and client-to-site)
  + SSL/TLS VPN
  + Always-on VPN
  + Zero Trust Network Access (ZTNA) as VPN replacement
  + Split tunneling risks
* DNS Security
  + DNSSEC
  + DNS over HTTPS (DoH) and DNS over TLS (DoT) for clients
  + DNS filtering (Cisco Umbrella, Pi-hole, Cloudflare Gateway)
  + DNS sinkholing for malware C2 blocking
  + Internal DNS architecture (split-horizon DNS)
* Email Security
  + SPF (Sender Policy Framework)
  + DKIM (DomainKeys Identified Mail)
  + DMARC (Domain-based Message Authentication, Reporting and Conformance)
  + Email gateway filtering (anti-spam, anti-phishing, anti-malware)
  + Email encryption (S/MIME, PGP)
  + BIMI (Brand Indicators for Message Identification)
* Network Monitoring
  + NetFlow/IPFIX collection and analysis
  + Network Performance Monitoring (NPM)
  + Network Detection and Response (NDR) tools
  + Packet capture infrastructure (TAPs, SPAN ports)
* Wireless Network Security
  + WPA2-Enterprise (802.1X + RADIUS)
  + WPA3 improvements
  + Rogue AP detection
  + Guest network isolation
  + Wireless intrusion detection (WIDS)
* DDoS Protection
  + On-premise mitigation (rate limiting, blackhole routing)
  + Cloud-based scrubbing (Cloudflare, Akamai, AWS Shield)
  + Anycast routing for DDoS resilience

Endpoint Hardening:

* Operating System Hardening
  + CIS Benchmarks (Windows, Linux, macOS, cloud)
  + DISA STIGs (for government/defense)
  + Disabling unnecessary services and ports
  + Removing unnecessary software
  + Enforcing strong authentication (no null/blank passwords, disable guest accounts)
* Windows Hardening
  + Group Policy hardening (AppLocker, Windows Defender settings, PowerShell logging)
  + Windows Defender Credential Guard
  + Windows Defender Application Guard
  + Secure baseline images
  + LAPS for local admin password management
  + Windows Firewall configuration
  + Disabling legacy protocols (NTLM v1, SMBv1, WEP, SSL/TLS 1.0/1.1)
  + UAC (User Account Control) configuration
  + Attack Surface Reduction (ASR) rules
* Linux Hardening
  + AppArmor and SELinux (Mandatory Access Control)
  + Disabling root SSH login (PermitRootLogin no)
  + SSH hardening (key-only authentication, disabling weak ciphers, AllowUsers)
  + File permissions and SUID/SGID auditing
  + auditd configuration
  + Kernel hardening (sysctl parameters: kernel.randomize_va_space, etc.)
  + Rootkit detection (chkrootkit, rkhunter)
  + CIS Benchmark for Linux
* Configuration Management and Hardening Automation
  + Ansible for security configuration enforcement
  + Chef InSpec and CIS Compliance scanning
  + Puppet for baseline enforcement
  + Terraform for IaC security

Cloud Security:

* Cloud fundamentals
  + IaaS vs PaaS vs SaaS — security responsibility differences
  + Shared Responsibility Model (per provider: AWS, Azure, GCP)
* Cloud IAM
  + Types of identities
    - Human users (console, CLI)
    - Service accounts / managed identities / instance profiles
    - Federated identities (SSO from on-prem to cloud)
  + Types of policies
    - IAM Allow policies
    - IAM Deny policies (SCPs in AWS Organizations)
    - Permission boundaries
    - Resource-based policies
    - Condition keys (IP-based, MFA required, time-based)
  + Service accounts and workload identity
    - AWS IAM roles and instance profiles
    - GCP service accounts and Workload Identity Federation
    - Azure Managed Identities
  + Common IAM misconfigurations
    - Overly permissive wildcard policies
    - Unused access keys and stale credentials
    - Public S3 buckets / GCS buckets / Azure Blob containers
    - IAM privilege escalation paths
  + AWS IAM privilege escalation techniques (iam:AttachUserPolicy, iam:PassRole, etc.)
  + IAM Access Analyzer (AWS) and equivalent tools
  + Principle of least privilege in cloud IAM (access reviews, permission audits)
* Zero Trust in Cloud
  + Identity as the new perimeter
  + BeyondCorp model (Google's Zero Trust)
  + Continuous verification and context-aware access
  + Micro-segmentation in cloud VPCs
* Cloud Storage Security
  + S3 bucket policies, ACLs, Block Public Access
  + Encryption at rest (SSE-S3, SSE-KMS, SSE-C in AWS)
  + Signed URLs and presigned requests
  + Lifecycle policies and versioning for data integrity
* Cloud Network Security
  + VPC design (public/private subnets, NAT gateways, internet gateways)
  + Security Groups and NACLs (AWS)
  + Private endpoints and VPC service endpoints
  + AWS PrivateLink, GCP Private Service Connect
  + Cloud WAF (AWS WAF, Cloudflare, Azure Front Door WAF)
  + VPC Flow Logs for network forensics
* Cloud Workload Security
  + Compute hardening (no public IPs, SSM Session Manager instead of SSH)
  + Container security (image scanning, runtime protection, least privilege pods)
  + Kubernetes security (RBAC, PodSecurity, network policies, secrets management)
  + Serverless security (Lambda function permissions, code vulnerability scanning)
  + AMI and machine image hardening pipelines
* Cloud Security Posture Management (CSPM)
  + Continuous misconfiguration detection
  + Tools: AWS Config, Azure Policy, GCP Security Command Center, Prisma Cloud, Wiz
* Cloud Detection and Response
  + AWS: CloudTrail + GuardDuty + Security Hub + Macie
  + Azure: Microsoft Defender for Cloud + Sentinel
  + GCP: Security Command Center + Cloud Audit Logs
* Infrastructure as Code (IaC) Security
  + Terraform security (tfsec, Checkov, KICS)
  + CloudFormation Guard
  + Detecting misconfigurations before deployment
  + Secrets in IaC (never hardcode — use Vault or cloud secrets managers)
* Secrets Management
  + HashiCorp Vault
  + AWS Secrets Manager and Parameter Store
  + Azure Key Vault
  + GCP Secret Manager
  + Secret rotation automation
* Cloud Compliance
  + Shared Responsibility and compliance mapping
  + AWS Well-Architected Framework (Security Pillar)
  + CIS AWS Foundations Benchmark
  + SOC 2, PCI DSS, HIPAA, GDPR in cloud context

PKI and Certificate Management:

* Public Key Infrastructure (PKI) components
  + Certificate Authorities (Root CA, Intermediate CA)
  + Certificate Revocation (CRL, OCSP)
  + Certificate lifecycle management (issuance, renewal, revocation)
* Internal PKI setup (Microsoft CA, EJBCA, HashiCorp Vault PKI)
* TLS certificate management
  + Let's Encrypt (ACME protocol) for public certificates
  + Certificate transparency logs
  + Wildcard vs SAN certificates
  + Certificate pinning considerations
* Code signing certificates
* SSH key management (centralized SSH CA, short-lived certificates)

Security Automation and DevSecOps:

* Infrastructure as Code security (see Cloud section)
* CI/CD pipeline security
  + Securing pipeline credentials (no hardcoded secrets)
  + SAST, SCA, and container scanning in CI gates
  + Signed artifacts and build integrity
  + Dependency confusion attack prevention
* Configuration drift detection
  + AWS Config Rules
  + Chef InSpec
  + OSQuery for continuous host monitoring
* Security orchestration and automation (SOAR basics)
* Python and Bash scripting for infrastructure security tasks
* API security for infrastructure management APIs

Physical Security (Awareness):

* Physical access controls (badge systems, biometrics, mantraps)
* Data center security (locked cages, camera surveillance, visitor logs)
* Shoulder surfing and clean desk policies
* Hardware security (tamper-evident seals, asset tagging, BIOS/UEFI passwords)
* Supply chain hardware risks

Compliance and Governance:

* Common compliance frameworks
  + SOC 2 (Trust Service Criteria)
  + ISO 27001
  + PCI DSS (for payment card environments)
  + HIPAA (for healthcare environments)
  + GDPR (for EU data)
  + FedRAMP (for US government cloud)
  + NIST CSF and SP 800-53
* Control mapping across frameworks
* Evidence collection and audit support
* Risk register management
* Third-party and vendor risk management

Tools:

* Nessus / OpenVAS (vulnerability scanning)
* Qualys (cloud vulnerability management)
* CrowdStrike Falcon / SentinelOne / Microsoft Defender for Endpoint (EDR)
* Prisma Cloud / Wiz / Lacework (CSPM)
* HashiCorp Vault (secrets management)
* CyberArk / BeyondTrust (PAM)
* BloodHound / SharpHound (AD attack path analysis)
* Nmap (network discovery and port scanning)
* Lynis (Linux security auditing)
* osquery (host visibility and compliance)
* Ansible / Puppet / Chef (configuration management)
* Terraform + tfsec / Checkov (IaC security)
* AWS Config / Azure Policy / GCP Security Command Center (cloud posture)

Books:

* [Security Engineering by Ross Anderson](https://www.amazon.com/Security-Engineering-Building-Dependable-Distributed/dp/1119642787)
* [Hacking the Cloud by Chris Farris (free online resource)](https://hackingthe.cloud/)
* [Defensive Security Handbook by Lee Brotherston and Amanda Berlin](https://www.amazon.com/Defensive-Security-Handbook-Practices-Infrastructure/dp/1491960388)
* [Active Directory Security by Sean Metcalf (adsecurity.org)](https://adsecurity.org/)
* [AWS Security Best Practices Whitepaper](https://docs.aws.amazon.com/whitepapers/latest/introduction-aws-security/introduction-aws-security.html)

Resources:

* [CIS Benchmarks (free)](https://www.cisecurity.org/cis-benchmarks)
* [HackTricks Cloud](https://cloud.hacktricks.xyz/)
* [AWS Well-Architected Framework — Security Pillar](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html)
* [BloodHound Community Edition](https://github.com/SpecterOps/BloodHound)
* [PayloadsAllTheThings — AD Attacks](https://github.com/swisskyrepo/PayloadsAllTheThings)

Relevant Certifications:

* AWS Certified Security — Specialty
* Google Professional Cloud Security Engineer
* Microsoft SC-900 / SC-300 / AZ-500
* GIAC GCSA (Cloud Security Automation)
* GIAC GCED (Certified Enterprise Defender)
* CompTIA CySA+
* CCSP (Certified Cloud Security Professional)
* CISSP (for senior roles)
