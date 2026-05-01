List of concepts, tools and resources you need to be an awesome detection engineer.

Logging:

* Basics of Logging
  + What makes a good log (timestamp, source, event type, severity, actor, resource, outcome)
  + Log verbosity levels (DEBUG, INFO, WARN, ERROR, CRITICAL)
  + Structured vs unstructured logs
  + Log tampering risks and log integrity protections
* Common Log Types:
  + System Logs (OS events, process creation, privilege use)
  + Network Logs (firewall, NetFlow, DNS queries, proxy logs)
  + Application Logs (web server access logs, authentication logs, error logs)
  + Authentication Logs (login success/failure, MFA events, account lockouts)
  + Audit Logs (file access, database queries, admin actions)
  + Cloud Logs (AWS CloudTrail, GCP Cloud Audit Logs, Azure Activity Logs)
  + Container Logs (Docker daemon logs, Kubernetes audit logs)
  + Email Logs (SMTP relay logs, spam filter events)
* Log aggregation and centralization
  + Syslog (RFC 5424), rsyslog, syslog-ng
  + Log forwarding agents (Filebeat, Fluentd, Vector)
  + Log rotation and retention policies
  + Log compression and archival
* Log enrichment
  + Adding context: GeoIP, hostname resolution, threat intel tagging
  + Asset inventory correlation
  + User identity enrichment

OS Logging:

* Windows Logging (Event Logs)
  + Event Log structure (Channel, EventID, Level, Provider)
  + Critical Event IDs to monitor:
    - 4624 (Logon success), 4625 (Logon failure), 4648 (explicit credential logon)
    - 4720 (account created), 4726 (account deleted), 4732/4733 (group membership changes)
    - 4688 (process creation — requires audit policy), 4104 (PowerShell script block logging)
    - 4663 (object access), 4698/4702 (scheduled task created/modified)
    - 7045 (new service installed), 4697 (service installed in the system)
    - 1102 (audit log cleared), 4719 (audit policy changed)
  + Windows Event Forwarding (WEF) and Windows Remote Management (WinRM)
  + Sysmon (System Monitor) — extended process, network, file, and registry event logging
    - Key Sysmon Event IDs (1: process create, 3: network connect, 11: file create, 13: registry modification, 22: DNS query)
  + Windows audit policy configuration (auditpol)
  + PowerShell logging (Module Logging, Script Block Logging, Transcription)
  + WMI event subscriptions as a persistence/detection vector
* Linux Logging
  + syslog and rsyslog configuration (/etc/rsyslog.conf)
  + systemd Journal (journalctl)
  + /var/log key files: auth.log, syslog, kern.log, secure, messages, cron, dpkg.log
  + auditd (Linux Audit Framework)
    - audit.rules configuration
    - Key events: execve (process execution), openat (file access), connect (network), setuid
    - ausearch and aureport for analysis
  + PAM (Pluggable Authentication Modules) logging
  + Shell history logging and HISTTIMEFORMAT
  + eBPF-based telemetry (Falco, Tetragon)
* macOS Logging
  + Unified Logging System (log show, log stream)
  + Console.app log messages
  + OpenBSM audit framework (/etc/security/audit_control)
  + EndpointSecurity framework (used by modern EDR on macOS)
  + LaunchAgent and LaunchDaemon monitoring for persistence

Network:

* IDS vs IPS
  + Placement (inline vs passive/tap)
  + Signature-based vs anomaly-based detection
  + False positive management and tuning
* Network Intrusion Detection
  + Snort (rules syntax: header + options, rule actions: alert/log/pass/drop)
  + Suricata (multi-threaded, supports EVE JSON output, Lua scripting)
    - Suricata rule structure
    - Protocol keywords (http, tls, dns, ssh)
    - Flow and stream reassembly
  + Zeek (Bro)
    - Zeek logs (conn.log, dns.log, http.log, ssl.log, files.log, weird.log)
    - Zeek scripting language for custom detections
    - Protocol analyzers
* Network Traffic Analysis (NTA)
  + NetFlow / IPFIX / sFlow collection and analysis
  + Full packet capture (PCAP) and analysis with Wireshark and tcpdump
  + Detecting beaconing, data exfiltration, lateral movement via traffic patterns
  + DNS anomaly detection (high-frequency queries, long domain names, NX domains — DGA indicators)
  + Encrypted traffic analysis (TLS fingerprinting — JA3/JA3S, JARM)
* Network Detection and Response (NDR) concepts
* Firewall and proxy log analysis
  + Identifying outbound connections to suspicious destinations
  + URL categorization bypass techniques

SIEM (Security Information and Event Management):

* SIEM architecture and components
  + Log collection → normalization → indexing → correlation → alerting → dashboarding
* Common SIEM platforms
  + Splunk (SPL — Splunk Processing Language, data models, lookup tables, saved searches)
  + Elastic Stack (ELK: Elasticsearch, Logstash, Kibana + Elastic SIEM/Security)
    - KQL (Kibana Query Language)
    - Elastic Common Schema (ECS) for log normalization
  + Microsoft Sentinel (KQL, analytics rules, workbooks, UEBA)
  + Google Chronicle (YARA-L, UDM — Unified Data Model)
  + IBM QRadar
  + Wazuh (open source SIEM + XDR)
* Log normalization and parsing
  + Field extraction (regex, Grok patterns)
  + Common Information Model (CIM) alignment
  + Timestamp normalization (UTC)
* Correlation rules
  + Threshold-based rules
  + Sequence/chaining rules
  + Aggregation rules
  + Baseline deviation rules
* Alert tuning
  + Reducing false positives without increasing false negatives
  + Allowlisting and exception management
  + Alert fatigue and its consequences
* SIEM use case library
  + Brute force and credential stuffing detection
  + Lateral movement detection (Pass-the-Hash, Pass-the-Ticket)
  + Data exfiltration detection
  + Ransomware activity (mass file renames, shadow copy deletion)
  + Living-off-the-land binaries (LOLBins) abuse

Threat Detection Concepts:

* Detection engineering lifecycle
  + Identify adversary behavior → define detection logic → test → deploy → tune → retire
* Detection types
  + Signature-based detection
  + Behavioral / anomaly-based detection
  + Heuristic detection
  + ML-based detection
* MITRE ATT&CK for Detection
  + Mapping detections to Tactics and Techniques
  + ATT&CK Navigator for coverage visualization
  + Prioritizing detection coverage (high-frequency, high-impact TTPs)
* Pyramid of Pain (IOC classification: hash → IP → domain → artifacts → tools → TTPs)
* Diamond Model of Intrusion Analysis
* Cyber Kill Chain and detection at each stage
* Threat-informed detection (using CTI to drive detection priorities)
* Coverage gap analysis
* Detection as Code
  + Version-controlling detection rules
  + CI/CD pipelines for rule testing and deployment
  + Testing detections with adversary emulation (Atomic Red Team, Caldera)

Pattern Matching and Rule Writing:

* Yara
  + Rule structure (meta, strings, condition)
  + String types (text, hex, regex)
  + Wildcards, jumps, and character classes
  + Modules (pe, elf, math, hash, time)
  + Yara rule best practices and performance considerations
  + Testing Yara rules (yarGen, retrohunting in VirusTotal)
* Sigma rules
  + Sigma rule format (YAML: title, logsource, detection, condition)
  + Sigma backends and converters (converting to Splunk SPL, KQL, Elasticsearch)
  + Sigma rule repositories (SigmaHQ)
* Snort/Suricata rule writing (see Network section above)
* Regular expressions for log parsing and pattern matching

Endpoint Detection:

* EDR (Endpoint Detection and Response) concepts
  + What EDRs monitor (process, file, registry, network, memory)
  + EDR telemetry vs traditional AV
  + Common EDR platforms: CrowdStrike Falcon, SentinelOne, Microsoft Defender for Endpoint, Carbon Black
* Host-based indicators of compromise (IOCs)
  + File hashes (MD5, SHA1, SHA256)
  + Persistence mechanisms (registry run keys, scheduled tasks, services, startup folders)
  + Suspicious process trees (cmd.exe spawned by Word, PowerShell with encoded commands)
  + Unusual parent-child process relationships
* Memory-based detections
  + Process injection indicators (unusual memory regions, unbacked executable pages)
  + Reflective DLL injection
  + Process hollowing

Threat Intelligence Integration:

* Threat intelligence types (strategic, operational, tactical, technical)
* Indicators of Compromise (IOCs): IPs, domains, file hashes, URLs, email addresses
* Threat intel platforms (MISP, OpenCTI, ThreatConnect, Anomali)
* STIX/TAXII for threat intelligence sharing
* Automating IOC ingestion into SIEM and EDR
* Threat actor profiling (TTPs, motivation, targets)

Incident Triage and Response (Detection Side):

* Alert triage workflow
  + Acknowledge → Investigate → Classify → Escalate or close
* True positive vs false positive vs false negative analysis
* Building and maintaining runbooks/playbooks for common alert types
* SOAR (Security Orchestration, Automation and Response) concepts
  + Automating repetitive triage tasks
  + Platforms: Splunk SOAR (Phantom), Palo Alto XSOAR, Microsoft Sentinel Playbooks, Shuffle
* Escalation procedures and SLAs

Metrics and Program Development:

* Detection coverage metrics (% of MITRE ATT&CK covered)
* Mean Time to Detect (MTTD)
* Alert volume, true positive rate, false positive rate
* SIEM query performance optimization
* Detection backlog management

Tools:

* Splunk
* Elastic SIEM / OpenSearch
* Microsoft Sentinel
* Wazuh (open source)
* Snort
* Suricata
* Zeek (Bro)
* Sysmon
* OSSEC
* Velociraptor (endpoint visibility and hunting)
* Sigma (rule format)
* Yara
* Atomic Red Team (adversary emulation for detection testing)
* MITRE Caldera (automated adversary emulation)
* VirusTotal (retrohunting, IOC lookups)
* MISP (threat intel sharing)
* CyberChef (log decoding and transformation)

Resources:

* [Detection resources — Awesome Threat Detection](https://github.com/0x4D31/awesome-threat-detection)
* [IDS/IPS module on HackTheBox Academy](https://academy.hackthebox.com/course/preview/working-with-idsips)
* [Splunk on Linux tutorial](https://www.geeksforgeeks.org/linux-unix/how-to-install-splunk-on-linux/)
* [SigmaHQ rule repository](https://github.com/SigmaHQ/sigma)
* [MITRE ATT&CK](https://attack.mitre.org/)
* [Atomic Red Team](https://github.com/redcanaryco/atomic-red-team)
* [Elastic Detection Rules](https://github.com/elastic/detection-rules)
* [Chronicle Detection Rules (YARA-L)](https://github.com/chronicle/detection-rules)
* [Florian Roth's Yara Rules](https://github.com/Neo23x0/signature-base)

Books:

* [The Practice of Network Security Monitoring by Richard Bejtlich](https://www.amazon.com/Practice-Network-Security-Monitoring/dp/1593275099)
* [Threat Hunting with Elastic Stack by Andrew Pease](https://www.amazon.com/Threat-Hunting-Elastic-Stack-Andrew/dp/1801073783)
* [Applied Network Security Monitoring by Chris Sanders](https://www.amazon.com/Applied-Network-Security-Monitoring-Collection/dp/0124172083)
* [Blue Team Handbook by Don Murdoch](https://www.amazon.com/Blue-Team-Handbook-condensed-Responder/dp/1500734756)

Relevant Certifications:

* GIAC GCIA (Certified Intrusion Analyst)
* GIAC GCDA (Certified Detection Analyst)
* Splunk Core Certified Power User
* Elastic Certified Analyst
* Microsoft SC-200 (Security Operations Analyst)
