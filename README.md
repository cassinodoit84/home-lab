\# Cybersecurity Home Lab – Docker Network \& OWASP Juice Shop



\## Project Overview



This project documents the development of a containerized cybersecurity home lab designed for hands-on practice with networking, reconnaissance, service enumeration, vulnerability assessment, and security testing.



The lab uses Docker to create an isolated network containing an intentionally vulnerable OWASP Juice Shop web application and a separate Ubuntu-based security workstation.



The objective is to simulate a small cybersecurity testing environment where security tools can be used safely against systems that I own and control.



\## Lab Objectives



\- Build an isolated cybersecurity lab using Docker.

\- Deploy OWASP Juice Shop as an intentionally vulnerable target.

\- Configure a separate Ubuntu container as a security workstation.

\- Understand Docker networking and container-to-container communication.

\- Perform network reconnaissance using Nmap.

\- Identify open ports and exposed services.

\- Analyze HTTP responses and security headers.

\- Collect and document security-testing evidence.

\- Practice troubleshooting and interpreting scanner results.



\## Technologies \& Tools



\- Docker Desktop

\- Docker Bridge Networking

\- Ubuntu 24.04

\- OWASP Juice Shop

\- Nmap

\- cURL

\- Windows PowerShell

\- Git \& GitHub



\## Lab Architecture



The environment currently consists of two Docker containers connected to an isolated Docker bridge network.



&#x20;   Windows Host

&#x20;        |

&#x20;        |-- Browser --> localhost:3000

&#x20;        |

&#x20;        +-- Docker Desktop

&#x20;              |

&#x20;        cyber-lab-network

&#x20;              |

&#x20;         +----+----+

&#x20;         |         |

&#x20;   security-tools  juice-shop

&#x20;     Ubuntu         OWASP

&#x20;         |           |

&#x20;         +-----> 172.19.0.2:3000



The `security-tools` container is used for reconnaissance and security testing.



The `juice-shop` container acts as the intentionally vulnerable target.



\## Initial Reconnaissance



After confirming connectivity between the containers, I performed service enumeration against the Juice Shop target using Nmap.



Command:



&#x20;   nmap -sV -p 3000 172.19.0.2



The scan confirmed that:



\- The target host was reachable.

\- TCP port 3000 was open.

\- The service returned HTTP application data.

\- Nmap could not confidently identify the service using its default fingerprint.



This demonstrated an important security-analysis principle: automated scanner results should be validated rather than accepted without interpretation.



The complete scan output is stored in:



&#x20;   evidence/juice-shop-nmap.txt



\## Skills Demonstrated



\- Docker container deployment

\- Network isolation

\- Linux command-line administration

\- TCP/IP networking

\- Network reconnaissance

\- Nmap service enumeration

\- HTTP analysis

\- Security evidence collection

\- Technical troubleshooting

\- Cybersecurity documentation



\## Ethical Use



All security testing documented in this project is performed in a controlled lab environment against systems intentionally deployed for security training. The techniques demonstrated here should only be used against systems you own or have explicit authorization to test.



\## Project Status



🚧 Work in Progress



Future stages will expand the lab with additional reconnaissance, vulnerability analysis, web application security testing, monitoring, and defensive security exercises.

