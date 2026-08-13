# Phase 5 – Remediation and Security Hardening



## Objective



The objective of this phase is to develop remediation recommendations for the security finding identified during Phase 4 of the cybersecurity home lab.



The goal is not only to identify a potential weakness, but also to demonstrate how security professionals evaluate risk, recommend defensive controls, and verify that remediation has been implemented correctly.



## Finding Reviewed



During Phase 4, HTTP response headers from the locally hosted OWASP Juice Shop environment were reviewed.



The assessment identified opportunities to improve HTTP security header configuration.



## Security Risk



Missing or improperly configured HTTP security headers can reduce the browser's ability to protect users from certain web-based attacks.



Depending on the affected header and application configuration, potential risks may include:



- Cross-site scripting (XSS)

- Clickjacking

- Content injection

- MIME-type interpretation issues

- Unauthorized loading of external resources



## Recommended Remediation



The following defensive controls should be considered:



### 1. Content Security Policy



Implement a restrictive Content-Security-Policy (CSP) that defines trusted sources from which scripts, styles, images, and other resources may be loaded.



### 2. Clickjacking Protection



Use the Content-Security-Policy `frame-ancestors` directive to restrict unauthorized websites from embedding the application.



### 3. MIME-Type Protection



Configure:



`X-Content-Type-Options: nosniff`



This helps prevent browsers from interpreting files as a different MIME type than declared by the server.



### 4. Referrer Policy



Implement an appropriate `Referrer-Policy` to limit the amount of potentially sensitive URL information transmitted to external websites.



### 5. Permissions Policy



Configure `Permissions-Policy` to restrict unnecessary browser capabilities such as camera, microphone, and geolocation access.



## Defense-in-Depth



Security headers should not be treated as the application's only security control.



They should complement:



- Secure application development

- Input validation

- Output encoding

- Authentication and authorization controls

- Patch management

- Secure server configuration

- Logging and monitoring

- Regular vulnerability assessments



## Verification



After remediation, HTTP responses should be reviewed again to confirm that the recommended security headers are present and configured correctly.



The results should then be compared with the original Phase 4 evidence.



## Lab Scope



This assessment was conducted in an isolated local Docker environment running OWASP Juice Shop for authorized educational cybersecurity practice.



No external production systems were tested.



## Skills Demonstrated



- Web application security assessment

- HTTP security header analysis

- Vulnerability documentation

- Risk assessment

- Security remediation planning

- Defense-in-depth

- OWASP security concepts

- Technical reporting

