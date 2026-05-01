Here is the list of concepts you need to learn to become an awesome application security engineer:

Web Application Security:

* OWASP Top 10 Vulnerabilities (current edition)
  + Broken Access Control
  + Cryptographic Failures
  + Injection (SQL, NoSQL, LDAP, OS command, XXE)
  + Insecure Design
  + Security Misconfiguration
  + Vulnerable and Outdated Components
  + Identification and Authentication Failures
  + Software and Data Integrity Failures
  + Security Logging and Monitoring Failures
  + Server-Side Request Forgery (SSRF)
* Mitigations for each OWASP Top 10 vulnerability
* OWASP Application Security Verification Standard (ASVS)
* OWASP Testing Guide (OTG)
* Cross-Site Scripting (XSS)
  + Reflected XSS
  + Stored XSS
  + DOM-based XSS
  + Defenses: Content Security Policy (CSP), output encoding, input validation
* SQL Injection
  + In-band SQLi (error-based, union-based)
  + Blind SQLi (boolean-based, time-based)
  + Out-of-band SQLi
  + Defenses: parameterized queries, prepared statements, ORMs, input validation
* Cross-Site Request Forgery (CSRF)
  + CSRF tokens
  + SameSite cookie attribute
* Server-Side Request Forgery (SSRF)
  + Cloud metadata endpoint abuse (e.g., 169.254.169.254)
  + Defenses: allowlisting, disabling unnecessary URL schemes
* XML External Entity (XXE) Injection
* Insecure Direct Object Reference (IDOR)
* Security Misconfiguration
  + Default credentials
  + Exposed debug endpoints
  + Missing security headers
* Clickjacking
  + X-Frame-Options
  + CSP frame-ancestors
* HTTP Security Headers
  + Content-Security-Policy (CSP)
  + Strict-Transport-Security (HSTS)
  + X-Content-Type-Options
  + Referrer-Policy
  + Permissions-Policy
* Cookie security attributes (HttpOnly, Secure, SameSite)
* Open Redirect vulnerabilities
* Path traversal and local file inclusion (LFI)
* Remote file inclusion (RFI)
* Template injection (SSTI)
* Business logic vulnerabilities
* Mass assignment vulnerabilities
* Insecure deserialization
  + Java, Python, PHP deserialization attacks
  + Defenses: input validation, signed tokens, avoid deserializing untrusted data
* Web cache poisoning
* HTTP request smuggling
* Race conditions and time-of-check time-of-use (TOCTOU)

API Security:

* OWASP API Security Top 10
  + Broken Object Level Authorization (BOLA/IDOR)
  + Broken Authentication
  + Broken Object Property Level Authorization (BOPLA)
  + Unrestricted Resource Consumption
  + Broken Function Level Authorization
  + Unrestricted Access to Sensitive Business Flows
  + Server-Side Request Forgery (SSRF)
  + Security Misconfiguration
  + Improper Inventory Management
  + Unsafe Consumption of APIs
* REST API security principles
* GraphQL security (introspection abuse, DoS via deeply nested queries, batching attacks)
* gRPC security considerations
* API rate limiting and throttling
* API key management and rotation
* API versioning and deprecation security implications
* JWT (JSON Web Tokens)
  + Structure (header, payload, signature)
  + Common JWT attacks (alg=none, RS256 to HS256, weak secrets, key confusion)
  + Best practices: short expiry, refresh tokens, RS256, token revocation

Threat Modeling:

* STRIDE
  + Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege
* PASTA (Process for Attack Simulation and Threat Analysis)
* DREAD (Damage, Reproducibility, Exploitability, Affected Users, Discoverability)
* LINDDUN (privacy threat modeling)
* Attack trees
* Data Flow Diagrams (DFDs) for threat modeling
* Trust boundaries
* Abuser stories
* MITRE ATT&CK mapping to application threats
* Threat modeling tools (OWASP Threat Dragon, Microsoft Threat Modeling Tool, IriusRisk)

Secure Development and Testing:

* SDLC (Software Development Lifecycle) and where security fits in each phase
* Secure SDLC (SSDLC) models (Microsoft SDL, OWASP SAMM, BSIMM)
* Secure Coding Practices
  + Input validation and sanitization
  + Output encoding
  + Error handling (avoid leaking stack traces)
  + Secure logging (avoid logging secrets, PII)
  + Dependency management and SCA
* Static Application Security Testing (SAST)
  + How SAST works (AST, data flow analysis, taint tracking)
  + Tools: Semgrep, CodeQL, Checkmarx, SonarQube, Bandit (Python), Brakeman (Ruby)
  + False positives and tuning
* Dynamic Application Security Testing (DAST)
  + How DAST works (black-box automated scanning)
  + Tools: OWASP ZAP, Burp Suite, Nikto
  + Authenticated vs unauthenticated scans
* Interactive Application Security Testing (IAST)
* Software Composition Analysis (SCA)
  + Identifying vulnerable open-source dependencies
  + Tools: OWASP Dependency-Check, Snyk, Dependabot, Black Duck
  + License compliance
* Fuzz testing (fuzzing)
  + Coverage-guided fuzzing (AFL, libFuzzer)
  + Protocol fuzzing
* Penetration testing for web applications
  + Manual testing techniques
  + Burp Suite for web app pentesting
* Security regression testing
* Code review (security-focused)
  + Identifying security antipatterns
  + Peer review checklists
* DevSecOps
  + Integrating security into CI/CD pipelines
  + SAST and SCA in CI gates
  + Secret scanning (truffleHog, GitLeaks, GitHub Secret Scanning)
  + Container image scanning (Trivy, Grype)
  + IaC scanning (Checkov, tfsec, KICS)
* Dependency confusion and supply chain attacks
* Software Bill of Materials (SBOM)
* Secure defaults and hardening (disabling debug modes, removing unused endpoints)

Authentication and Authorization:

* Authentication vs Authorization (AuthN vs AuthZ)
* OAuth 2.0
  + Authorization Code Flow (with PKCE)
  + Client Credentials Flow
  + Implicit Flow (deprecated, why)
  + Device Authorization Flow
  + Common OAuth attacks (CSRF on redirect_uri, open redirects, token leakage)
* OpenID Connect (OIDC)
* SAML 2.0 (assertions, SP-initiated vs IdP-initiated, XML signature wrapping attacks)
* Zero Trust (never trust, always verify, least privilege)
* Session management
  + Session token generation (entropy requirements)
  + Session fixation attacks
  + Session hijacking via XSS or network eavesdropping
  + Secure session termination
* Password security
  + Secure password storage (bcrypt, Argon2, scrypt — never MD5/SHA1 for passwords)
  + Password strength requirements
  + Account lockout and throttling vs credential stuffing resilience
* Multi-Factor Authentication (MFA) integration in applications
* Passwordless authentication (FIDO2/WebAuthn, passkeys)
* Privilege escalation in application context (horizontal vs vertical)
* Broken access control patterns and how to test for them

Mobile Application Security:

* OWASP Mobile Top 10
* iOS security model (sandboxing, entitlements, Keychain)
* Android security model (permissions, intents, content providers)
* Insecure data storage on mobile (unencrypted local storage, logs, caches)
* Insecure communication (certificate pinning, custom TLS validation)
* Binary protections (obfuscation, anti-tampering, jailbreak/root detection)
* Mobile application penetration testing basics

Cryptography for AppSec:

* Proper use of cryptographic libraries (avoid rolling your own crypto)
* Symmetric vs asymmetric encryption in application context
* TLS configuration (strong cipher suites, certificate validation, HSTS)
* Secrets management
  + Never hardcode secrets in source code
  + Environment variables, secrets managers (HashiCorp Vault, AWS Secrets Manager, Azure Key Vault)
  + Secret rotation
* Key management in applications
* Cryptographic random number generation

Cloud Application Security:

* Shared responsibility model
* Security implications of serverless (Lambda, Cloud Functions)
* Container security in applications (image hardening, no root, read-only filesystems)
* Cloud storage security (S3 bucket misconfiguration, GCS bucket policies)
* Environment variable security in cloud deployments
* Least privilege IAM roles for applications

Tools:

* Burp Suite (intercepting proxy, scanner, intruder, repeater)
* OWASP ZAP
* Semgrep
* Snyk
* OWASP Dependency-Check
* Nikto
* SQLmap (for understanding and testing SQLi)
* jwt.io (for JWT inspection and debugging)
* Postman / Insomnia (API security testing)
* Shodan (for discovering exposed app instances)

Relevant Books:

* [The Web Application Hacker's Handbook](https://www.amazon.com/Web-Application-Hackers-Handbook-Exploiting/dp/1118026470)
* [Real-World Bug Hunting by Peter Yaworski](https://www.amazon.com/Real-World-Bug-Hunting-Field-Hacking/dp/1593278616)
* [The Tangled Web by Michal Zalewski](https://www.amazon.com/Tangled-Web-Securing-Modern-Applications/dp/1593273886)
* [API Security in Action by Neil Madden](https://www.amazon.com/API-Security-Action-Neil-Madden/dp/1617296024)
* [Alice and Bob Learn Application Security by Tanya Janca](https://www.amazon.com/Alice-Bob-Learn-Application-Security/dp/1119687357)

Resources:

* [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
* [PortSwigger Web Security Academy](https://portswigger.net/web-security) (free, hands-on labs)
* [HackTheBox Academy - Web Application Modules](https://academy.hackthebox.com/)
* [PentesterLab](https://pentesterlab.com/)

Relevant Certifications:

* GWEB (GIAC Web Application Penetration Tester)
* BSCP (Burp Suite Certified Practitioner)
* OSWE (Offensive Security Web Expert)
* CEH (Certified Ethical Hacker)
