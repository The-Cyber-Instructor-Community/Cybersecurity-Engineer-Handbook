Here is the list of concepts you need to learn to become an awesome DFIR professional (Digital Forensics and Incident Response)

Digital Forensics:

* Basics of Digital Forensics
  + Goals of digital forensics (identification, preservation, analysis, documentation, presentation)
  + Locard's Exchange Principle applied to digital environments
  + Admissibility of digital evidence (legal considerations)
  + Order of volatility (RAM → swap → network state → processes → disk → logs → archives)
* Types of Evidence
  + Volatile evidence (RAM, network connections, running processes, logged-in users)
  + Non-volatile evidence (disk images, logs, backups, cloud storage)
  + Network evidence (PCAP, NetFlow, firewall logs)
  + Cloud evidence (API logs, audit trails, object storage)
  + Mobile evidence (device images, application data, location data)
* Chain of Custody
  + Documentation requirements (who, what, when, where, how)
  + Evidence handling and packaging
  + Hash verification (MD5, SHA1, SHA256) to prove integrity
  + Evidence storage and access control
  + Legal implications of broken chain of custody
* Evidence Acquisition
  + Forensic imaging principles (bit-for-bit copies)
  + Write blockers (hardware and software)
  + Imaging tools: dd, dcfldd, FTK Imager, Guymager, dc3dd
  + Disk image formats: RAW/dd, E01 (EnCase), AFF (Advanced Forensic Format)
  + Hashing before and after acquisition to verify integrity
  + Acquiring RAM (LiME on Linux, winpmem on Windows, Magnet RAM Capture)
  + Network forensics acquisition (PCAP collection, NetFlow)
  + Cloud evidence acquisition (API-based collection, preservation orders)
  + Mobile device acquisition modes (logical, filesystem, physical, chip-off)

Computer System Forensics:

* File Systems
  + File system fundamentals (inodes, directory entries, metadata)
  + Allocated vs unallocated space
  + File carving (recovering deleted files from unallocated space)
  + Slack space and its forensic significance
  + Alternate data streams (ADS) on NTFS
* NTFS File System Structure
  + Master File Table (MFT) — structure and forensic value
  + $MFT, $LogFile, $USNJrnl (Update Sequence Number Journal)
  + $RECYCLE.BIN analysis
  + NTFS timestamps (MACE: Modified, Accessed, Created, Entry Modified)
  + Timestomping and anti-forensics detection
  + Volume Shadow Copies (VSS) — accessing previous file versions
  + Prefetch files (%SystemRoot%\Prefetch) — evidence of execution
  + ShellBags — evidence of folder access
  + LNK files — evidence of file access and origin
  + Jumplists — recent file activity
  + Windows Search Index (Windows.edb)
* FAT File System Structure
  + FAT12, FAT16, FAT32 differences
  + Directory entries and file allocation chains
  + Deletion and recovery in FAT
* Ext File System Structure (Linux)
  + Ext2/Ext3/Ext4 differences
  + Inodes, directory entries, and block groups
  + Journal (Ext3/4) — evidence of file system operations
  + Superblock and group descriptors
  + Deleted file recovery on Ext4
  + /proc filesystem — volatile system state
  + Bash history, .bash_profile, cron jobs, /etc/passwd, /etc/shadow
* macOS Forensics
  + HFS+ vs APFS file systems
  + macOS plist files (property lists) — configuration and artifacts
  + Spotlight metadata (.DS_Store, Spotlight-V100)
  + macOS Keychain artifacts
  + Unified Logs as forensic evidence
  + LaunchAgents/LaunchDaemons — persistence artifacts
  + Safari/Chrome browser artifacts
  + macOS quarantine attribute (com.apple.quarantine)
* Windows Registry Forensics
  + Registry structure (hives: SYSTEM, SOFTWARE, SAM, SECURITY, NTUSER.DAT, UsrClass.dat)
  + Key forensic registry locations:
    - HKLM\SYSTEM\CurrentControlSet\Services (services and drivers)
    - HKCU\Software\Microsoft\Windows\CurrentVersion\Run (persistence)
    - HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList (user profiles)
    - UserAssist (GUI program execution — ROT13 encoded)
    - MUICache (executed program names)
    - ShimCache / AppCompatCache (evidence of execution)
    - AmCache.hve (file execution and installation evidence)
    - BAM/DAM (Background Activity Moderator — execution times)
  + Registry transaction logs (.LOG files) and their forensic value
* Windows Artifact Analysis
  + Prefetch analysis (execution count, timestamps, loaded DLLs)
  + Event Log forensics (key Event IDs — see detection-engineer.md)
  + $MFT analysis
  + Browser artifacts (history, cache, cookies, downloads, saved passwords)
    - Chrome: SQLite databases in User Data\Default\
    - Firefox: places.sqlite, cookies.sqlite
  + Email artifacts (PST/OST files, Outlook attachments)
  + Recycle Bin artifacts ($I and $R files)
  + Windows Search Database (Windows.edb)
  + SRUM (System Resource Usage Monitor) — network and application usage history
  + WMI repository — persistence and lateral movement artifacts
  + Scheduled Tasks XML files (%SystemRoot%\System32\Tasks\)

Memory Forensics:

* Why memory forensics matters (credentials, encryption keys, injected code live in RAM)
* RAM acquisition tools
  + LiME (Linux Memory Extractor) — Linux kernel module
  + winpmem — Windows
  + Magnet RAM Capture — Windows (GUI)
  + FTK Imager (RAM capture mode)
* Volatility Framework (version 2 and version 3)
  + Core workflow: identify OS profile → run plugins → analyze output
  + Key Volatility plugins:
    - pslist, pstree, psscan (process listing — psscan finds hidden processes)
    - cmdline, dlllist (per-process command line and loaded DLLs)
    - netscan, netstat (network connections)
    - malfind (injected code detection — RWX memory regions)
    - handles (open handles per process)
    - filescan, dumpfiles (recover files from memory)
    - hivelist, printkey (registry hive analysis)
    - hashdump (extract password hashes)
    - shimcachemem, mftparser
  + Detecting process injection (malfind, hollowing indicators)
  + Detecting rootkits (hidden processes via psscan vs pslist discrepancy)
* Memory analysis for malware
  + Identifying packed/obfuscated code
  + Carving strings from process memory
  + Yara scanning against memory dumps
* Hibernation file (hiberfil.sys) and pagefile.sys as memory sources

Network Forensics:

* PCAP analysis with Wireshark
  + Display filters vs capture filters
  + Following TCP/UDP streams
  + Extracting files from PCAP (HTTP objects, SMB files, email attachments)
  + Identifying C2 communication patterns (beaconing, long connections, unusual ports)
  + DNS query analysis in PCAP
  + TLS traffic analysis (SNI extraction, JA3 fingerprinting)
* Zeek log analysis for forensic reconstruction
* NetFlow analysis for timeline reconstruction
* Proxy and firewall log analysis
* Email forensics
  + Email header analysis (Received headers, SPF/DKIM/DMARC results)
  + Identifying phishing artifacts (spoofed sender, mismatched domains)
  + Attachment analysis (file type, embedded macros, links)

Malware Analysis:

* Static analysis
  + File identification (file command, TrID, YARA)
  + PE (Portable Executable) structure (headers, sections, imports/exports)
  + Strings extraction (strings, FLOSS for obfuscated strings)
  + Import analysis (suspicious APIs: VirtualAlloc, WriteProcessMemory, CreateRemoteThread)
  + Packing detection (PEiD, Detect-It-Easy)
  + Hash lookup (VirusTotal, MalwareBazaar)
* Dynamic analysis
  + Sandbox environments (Cuckoo Sandbox, Any.Run, JoeSandbox, VirusTotal sandbox)
  + Behavioral analysis (process creation, network connections, file drops, registry changes)
  + Monitoring tools: Process Monitor (ProcMon), Process Hacker, Autoruns, Regshot
  + Network simulation in sandbox (FakeNet-NG, INetSim)
* Code analysis basics
  + x86/x64 assembly fundamentals for malware analysis
  + Disassemblers: Ghidra (free), IDA Pro, Binary Ninja, Radare2
  + Decompilers: Ghidra, JD-GUI (Java), dnSpy (.NET)
  + Debugging: x64dbg (Windows), GDB (Linux)
  + Identifying common malware capabilities in code (keylogging, screenshot capture, lateral movement)
* Malware families and their TTPs
  + RATs (Remote Access Trojans)
  + Infostealers
  + Banking trojans
  + Ransomware (file encryption mechanics, shadow copy deletion)
  + Rootkits (kernel vs user space)
  + Botnets and C2 protocols (HTTP, DNS tunneling, domain generation algorithms)
  + Fileless malware (PowerShell, WMI, reflective DLL injection)

Incident Response:

* Incident Response Cycle (NIST SP 800-61)
  + Preparation
  + Detection and Analysis
  + Containment, Eradication, and Recovery
  + Post-Incident Activity (lessons learned)
* SANS PICERL Model (Preparation, Identification, Containment, Eradication, Recovery, Lessons Learned)
* Preparation
  + IR plan and playbooks
  + Asset inventory and baseline
  + Contact lists and escalation procedures
  + Legal and regulatory obligations (breach notification timelines)
  + Tabletop exercises and IR drills
  + Log collection and retention readiness
  + EDR and forensic tool deployment
* Detection and Analysis
  + Triaging alerts from SIEM, EDR, and user reports
  + Scoping the incident (what systems, what data, what timeframe)
  + Initial timeline construction
  + Identifying patient zero and initial access vector
  + Malware identification
* Containment
  + Short-term containment (isolating affected systems, blocking IOCs)
  + Long-term containment (rebuilding compromised systems on isolated network)
  + Evidence preservation during containment
  + Credential reset procedures
  + Network segmentation enforcement
* Eradication
  + Removing malware and persistence mechanisms
  + Patching exploited vulnerabilities
  + Resetting compromised credentials
  + Removing attacker-created accounts and backdoors
* Recovery
  + Restoring systems from clean backups
  + Monitoring restored systems for re-compromise
  + Validating system integrity before returning to production
* Post-Incident Activity
  + Lessons learned meeting (blameless post-mortem)
  + Root cause analysis
  + Updating detection rules and playbooks
  + Reporting to leadership, regulators, and affected parties
  + Threat intelligence extraction from the incident
* IR Playbooks for Common Incidents
  + Ransomware response
  + Business Email Compromise (BEC) response
  + Data breach response
  + Insider threat response
  + Cloud account compromise response
  + DDoS response
* Legal and regulatory considerations
  + Evidence handling for legal proceedings
  + Breach notification laws (GDPR 72-hour rule, US state laws, HIPAA)
  + Law enforcement engagement
  + Chain of custody for legal proceedings

Cloud Forensics and Incident Response:

* Shared responsibility in cloud incidents
* AWS forensics
  + CloudTrail log analysis (who did what, when, from where)
  + VPC Flow Logs (network forensics)
  + GuardDuty findings
  + EC2 instance memory and disk acquisition (snapshot → forensic workstation)
  + S3 access logs
  + Lambda function logs (CloudWatch)
* Azure forensics
  + Azure Activity Log and Diagnostic Logs
  + Microsoft Defender for Cloud alerts
  + Azure AD Sign-In and Audit logs
  + Azure Storage logging
* GCP forensics
  + Cloud Audit Logs (Admin Activity, Data Access, System Event)
  + VPC Flow Logs
  + Cloud Storage access logs
* Container and Kubernetes forensics
  + Kubernetes audit logs
  + Container runtime logs
  + Acquiring container state before deletion
  + Detecting container escape techniques

Tools:

* Acquisition: LiME, winpmem, FTK Imager, Guymager, dd, dcfldd
* Memory Analysis: Volatility 3, Rekall
* Disk Forensics: Autopsy, Sleuth Kit (TSK), FTK, X-Ways Forensics
* Registry Analysis: RegRipper, Registry Explorer (Eric Zimmermann Tools)
* Windows Artifact Analysis: Eric Zimmermann's Tools (MFTECmd, LECmd, JLECmd, PECmd, ShellBagsExplorer, WxTCmd, KAPE)
* Timeline Analysis: log2timeline/Plaso + Timesketch
* Network Forensics: Wireshark, tcpdump, NetworkMiner, Zeek
* Malware Analysis: Ghidra, x64dbg, Process Monitor, Cuckoo Sandbox, Any.Run, FLOSS, Detect-It-Easy, PEiD
* Threat Intel: VirusTotal, MalwareBazaar, OTX AlienVault, MISP
* KAPE (Kroll Artifact Parser and Extractor) — triage collection tool
* Velociraptor — endpoint visibility and remote forensic collection
* IRIS (Incident Response Investigation Solution) — open source IR case management

Books:

* [Blue Team Handbook by Don Murdoch](https://www.amazon.com/Blue-Team-Handbook-condensed-Responder/dp/1500734756)
* [File System Forensic Analysis by Brian Carrier](https://www.amazon.com/System-Forensic-Analysis-Brian-Carrier/dp/0321268172)
* [The Art of Memory Forensics by Ligh, Case, Levy, Walters](https://www.amazon.com/Art-Memory-Forensics-Detecting-Malware/dp/1118825098)
* [Incident Response and Computer Forensics by Luttgens, Pepe, Mandia](https://www.amazon.com/Incident-Response-Computer-Forensics-Third/dp/0071798684)
* [Practical Malware Analysis by Sikorski and Honig](https://www.amazon.com/Practical-Malware-Analysis-Hands-Dissecting/dp/1593272901)
* [The Hacker Playbook 3 by Peter Kim](https://www.amazon.com/Hacker-Playbook-Practical-Penetration-Testing/dp/1980901759)

Resources:

* [SANS DFIR Posters and Cheat Sheets](https://www.sans.org/posters/)
* [Eric Zimmermann's Forensic Tools](https://ericzimmerman.github.io/)
* [Volatility Documentation](https://volatility3.readthedocs.io/)
* [Magnet Forensics Free Tools](https://www.magnetforensics.com/free-tools/)
* [13Cubed YouTube Channel (DFIR)](https://www.youtube.com/c/13Cubed)
* [DFIR.training — curated DFIR resources](https://www.dfir.training/)
* [CTF: DFIR Challenges on BlueTeamLabs Online](https://blueteamlabs.online/)

Relevant Certifications:

* GCFE (GIAC Certified Forensic Examiner)
* GCFA (GIAC Certified Forensic Analyst)
* GNFA (GIAC Network Forensic Analyst)
* GREM (GIAC Reverse Engineering Malware)
* EnCE (EnCase Certified Examiner)
* CFCE (Certified Forensic Computer Examiner — IACIS)
