🛡️ Cybersecurity Home Lab

Vulnerability Assessment • Web Security • Docker • NGINX • Security Hardening

A hands-on defensive cybersecurity project documenting the process of building an isolated lab, discovering an application’s attack surface, analyzing security weaknesses, implementing compensating controls, troubleshooting their impact, and verifying remediation.

Project workflow: Discovery → Enumeration → Vulnerability Analysis → Risk Assessment → Remediation → Verification → Documentation

🎯 Project Objective

The goal of this project is to develop practical cybersecurity skills through repeatable, evidence-based security testing against systems I own and control.

The lab uses OWASP Juice Shop as an intentionally vulnerable target and Docker to provide an isolated environment. Later phases introduce an NGINX reverse proxy as a defensive security layer.

All testing documented here is performed locally for educational and authorized security training.


🏗️ Lab Architecture

                    Windows Host
                         |
             +-----------+-----------+
             |                       |
        PowerShell / Browser     Docker Desktop
                                     |
                            Isolated Lab Network
                                     |
                      +--------------+--------------+
                      |                             |
               Security Tooling              OWASP Juice Shop
                Nmap / cURL                    Target :3000
                                                    |
                                             NGINX Reverse Proxy
                                              Hardened :8080

The original application is tested on port 3000. During the remediation phase, traffic is routed through NGINX on port 8080, where additional defensive HTTP controls are applied.


🔬 Project Phases

Phase	Focus	Key Work	Status
1	Lab Deployment	Docker environment, Juice Shop target, isolated networking	✅ Complete
2	Network Reconnaissance	Nmap scanning, service detection, HTTP validation	✅ Complete
3	Web Enumeration	WhatWeb, Nikto, Gobuster, endpoint discovery	✅ Complete
4	Vulnerability Analysis	Finding validation, risk analysis, OWASP mapping	✅ Complete
5	Remediation & Hardening	NGINX reverse proxy, CSP and security headers, validation	✅ Complete
6	Security Verification	Before/after validation and remediation verification	🚧 In Progress


🔎 Phase 2 — Network Reconnaissance

Network reconnaissance was performed against the Juice Shop container using Nmap and cURL.

nmap -sV -p 3000 172.19.0.2

The assessment confirmed that the target was reachable and that TCP port 3000 exposed the web application.

HTTP inspection was then used to validate the service rather than relying only on automated scanner identification.

Skills demonstrated: Nmap • TCP/IP • Service Enumeration • HTTP Analysis • Evidence Collection


🌐 Phase 3 — Web Application Enumeration

The application was enumerated using multiple tools to identify technologies, exposed paths, HTTP behavior, and potential attack-surface information.

Tools Used

* WhatWeb
* Nikto
* Gobuster
* DIRB wordlists
* cURL

Interesting paths discovered during the authorized assessment included:

* /ftp
* /promotion
* /robots.txt
* /video
* /assets
* /media

This phase demonstrated why reconnaissance results from different tools should be correlated and manually interpreted.


⚠️ Phase 4 — Vulnerability Analysis & OWASP Mapping

Enumeration results were moved into a structured vulnerability-management workflow.

A validated finding documented application configuration information exposure through an administrative configuration endpoint.

The issue was assessed for security impact and mapped to:

OWASP A05:2021 — Security Misconfiguration

The analysis included:

* Finding description
* Technical evidence
* Security impact
* Severity assessment
* OWASP mapping
* Remediation recommendations
* Validation scope

📄 Read the Phase 4 Vulnerability Analysis


🔐 Phase 5 — Remediation & Security Hardening

Phase 5 moved from identifying weaknesses to implementing defensive controls.

Rather than modifying the Juice Shop source code, I deployed an NGINX reverse proxy in front of the application.

Browser → NGINX :8080 → OWASP Juice Shop :3000

Security Controls Implemented

* Content-Security-Policy
* Referrer-Policy
* Permissions-Policy
* X-Content-Type-Options: nosniff
* X-Frame-Options: SAMEORIGIN

The initial Content Security Policy was restrictive enough to affect the application’s interface.

I reviewed the policy, adjusted it to support required application resources, reloaded NGINX, and retested the application.

This demonstrated an important security-engineering principle:

A security control must reduce risk while preserving required business and application functionality.

📄 Read the Complete Phase 5 Remediation & Hardening Lab


📸 Phase 5 Evidence

Hardened Application

OWASP Juice Shop functioning through the NGINX reverse proxy on port 8080 after CSP troubleshooting.

Security Header Verification

PowerShell and cURL verification showing the hardened endpoint returning HTTP 200 and the additional security headers.


📊 Before vs. After

Security Control	Baseline :3000	Hardened :8080
X-Content-Type-Options	✅ Present	✅ Present
X-Frame-Options	✅ Present	✅ Present
Content-Security-Policy	❌ Not identified	✅ Added
Referrer-Policy	❌ Not identified	✅ Added
Permissions-Policy	❌ Not identified	✅ Added
Application Functional	✅	✅ After CSP adjustment

The result demonstrates a complete defensive workflow rather than simply running vulnerability scanners:

Identify → Analyze → Remediate → Troubleshoot → Verify


🛠️ Tools & Technologies

Area	Technologies
Containerization	Docker Desktop, Docker Networking
Target Application	OWASP Juice Shop
Reconnaissance	Nmap, WhatWeb, Nikto, Gobuster
HTTP Analysis	cURL, PowerShell
Defensive Control	NGINX Reverse Proxy
Systems	Windows, Ubuntu/Linux
Documentation	Git, GitHub, Markdown


🧠 Skills Demonstrated

* Vulnerability assessment and management
* Network reconnaissance and service enumeration
* Web application security assessment
* HTTP security-header analysis
* OWASP Top 10 mapping
* Risk assessment and remediation planning
* NGINX reverse-proxy configuration
* Content Security Policy implementation
* Security-control troubleshooting
* Remediation verification
* Docker container management
* Linux and PowerShell command-line work
* Technical documentation and evidence management


📁 Repository Structure

home-lab/
├── docs/          # Vulnerability analysis and remediation reports
├── evidence/      # Raw command and scanner output
├── screenshots/   # Visual evidence from lab phases
├── nginx/         # Reverse-proxy hardening configuration
└── README.md      # Project case study

This structure separates raw evidence from analysis and final documentation, making the project easier to review as a cybersecurity portfolio case study.


🚧 Next Phase

Phase 6 — Security Verification

The next phase will formally compare the baseline and hardened environments, verify that the implemented controls remain active, validate application functionality, and document the final remediation outcome with repeatable evidence.


⚖️ Ethical Use

All security testing in this repository is performed against an intentionally vulnerable application deployed inside a controlled local lab environment.

No external or production systems are tested.

Security-testing techniques should only be used against systems you own or have explicit authorization to assess.


👤 Author

Cosmos Akpan
Cybersecurity Student • Blue Team • SOC • Network Security

This repository is part of my hands-on cybersecurity portfolio and documents my progression from security discovery through defensive remediation and verification.
