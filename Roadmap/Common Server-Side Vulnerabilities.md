Common Server-Side Vulnerabilities
Learn to identify and exploit common server-side web application vulnerabilities. To ensure you understand a vulnerability, ask yourself - what is it, what is the root cause, how to exploit, mitigation

### Command Injection

- What is Command Injection
- Command Injection vs Code Injection
- Command Injection Examples
- Mitigations

### SQL Injection

- Understand SQL Injection Root Cause
- In-Band SQL Injection (Union and Error Based)
- Blind SQL Injection (Time/Boolean)
- Out of Band SQL Injection
- 2nd Order SQL Injection
- RCE From SQL Injection Root Cause
- SQL Injection Mitigation
- Writing Your Own Script to Exploit the Bug
- Bonus: Try Exploit the Bug in MySQL/Oracle/SQLite - What is the Difference

### Server-Side Template Injection (SSTI)

- What is Template Engines and How Does it Work?
- Write Simple Python App with Jinja2
- SSTI Root Cause
- Exploitation of SSTI
- Does Same Concept Apply for Smarty PHP?
- Mitigation For SSTI

### NoSQL Injection

- What is NoSQL Databases
- MongoDB Example
- NoSQL Injection Root Cause
- Solving Labs
- What is Redis Injection?
- Gopher Protocol

### Server-Side Request Forgery (SSRF)

- What is SSRF
- SSRF Root Cause
- How to Identify SSRF From Client Side Request
- SSRF Examples
- SSRF in AWS Case Study
- SSRF To RCE Gopher Example
- SSRF Read Local Files
- PDF Generators SSRF
- SSRF Mitigation

### File Upload Attacks

- Understand File Upload Process
- What is Unrestricted File Upload
- What Environment Unrestricted File Upload Can Lead to RCE
- Bypass Common Mitigations
- File Upload Attacks Mitigations
- Arbitrary File Write Bug
- What is ZipSlip Vulnerability ?

### Broken Access Control

- What is Access Control
- How Does Access Control Applied in Web Apps
- Broken Access Control Impact
- Broken Object Level Authorization
- Broken Function Level Authorization
- Solving Labs
- Mitigations

### Insecure Deserialization

- What is Serialization in Software
- What are Serialization Formats
- Understand Process of Serializing/Deserializing
- When Does Deserialization Becomes Dangerous?
- What are Gadgets
- What are Common Vulnerable Functions in Languages
- Solving Labs PHP/Java
- Mitigations

### XML Attacks

- What is XML Format
- What is XPATH
- XPATH Injection
- External XML Entity Injection
- Understand Root Cause of XML Attacks
- Mitigations

### Authentication Attacks

- SQL Injection in Authentication
- Bypass Authentication Flow
- Bypass 2FA Examples
- Host Header Injection in Forget Password Link
- Weak Token Generated
- Bypass Rate Limiting
- Missing Rate Limit on OTP
- Bypass Account Verification
- Bypass Captcha
- Mitigations

### Race Condition

- What is Race Condition
- Race Condition Example in File Upload
- Race Conditions Example in Bypassing Server-Side Restrictions
- Race Conditions Root Cause
- Race Conditions Mitigations

### Vulnerable and Outdated Components

- Identify Outdated Components Used by Backend
- How to Search for CVEs and Exploits Online

### API Attacks

- What is Authorization Headers
- What are APIs
- RESTful APIs vs SOAP vs GraphQL
- API Documentation
- API Versioning Attacks
- How to Interact with APIs Without Web App
- Mass Assignment Vulnerabilities
- API Rate Limiting
- API Fuzzing and Testing
- GraphQL Attacks

### Directory Traversal Attacks

- What is Directory Traversal
- Arbitrary File Write
- Arbitrary File Read
- LFI vs RFI vs LFD in PHP
- Mitigations

### Prototype Pollution

- What is a Prototype
- Root Cause of Prototype Pollutions
- Examples in Node.js EJS Engine
- Mitigations

### Improper Session Handling

- Session Fixation
- Session Puzzling
- Improper Session Validation
- Inactive Sessions Remain Valid After Logout
- Mitigations

### Cryptographic Attacks (Optional)

- Weak Generation Function For Tokens
- AES CBC Oracle Attacks
- Hash Length Extension Attacks
- Hash Collisions (MD5, SHA-1)
- Padding Oracle Attacks
- Timing Attacks on Cryptographic Operations
- Weak Random Number Generation
- Cryptographic Implementation Flaws
- Mitigations

### Logic Bugs

- Logic bugs depend on application business itself
- Check multi-step process - can you drop one step and continue or does it check sequence?
- Check response manipulation bugs
- Check what data inputs can cause errors - does it have to be a positive number?

### Web Caching Attacks

- What is Caching Systems
- Cache Keys vs Cache Rules
- URL Normalization & Different URL Delimiters
- Web Cache Poisoning
- Web Cache Deception

### HTTP Request Smuggling

- What is HTTP Request Smuggling
- Understanding Content-Length and Transfer-Encoding Headers
- How Backend and Frontend Servers Process HTTP Requests Differently
- CL.TE Request Smuggling (Front-end uses Content-Length, Back-end uses Transfer-Encoding)
- TE.CL Request Smuggling (Front-end uses Transfer-Encoding, Back-end uses Content-Length)
- Impact of HTTP Request Smuggling
- Mitigation from Backend Server
- Mitigation from Proxy/Load Balancer
