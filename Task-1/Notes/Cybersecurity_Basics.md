# Cybersecurity Basics

## Understand the CIA Triad

**CIA** stands for:<br>
**C:** Confidentiality<br>
**I:** Integrity<br>
**A:** Availability

The **CIA Triad** is a fundamental model in cybersecurity that describes the protection of data and systems within an organization.

*Data* is one of the major assets of an organization.

![CIA Triad](https://www.threatscape.com/wp-content/uploads/2024/01/The-CIA-Triad-for-Cyber-Security.png)

## Characteristics

### 1. Confidentiality

**Goal:** To prevent or minimize unauthorized access to data.<br>

**Example:**
- Encryption of data

### 2. Integrity

**Goal:** To ensure the accuracy, trustworthiness, and consistency of data.

**Examples:**
- Hashing to detect changes in data
- Digital signatures

### 3. Availability

**Goal:** To ensure that information and services are accessible to authorized users when required.

**Example:**
- Regular backups
- Disaster Recovery

<hr>

## Explore Threat Types: Phishing, Malware, DDoS, SQL Injection, Brute Force, Ransomware

**Threat:** It is any potential danger or event that can exploit weakness in a system, which may cause harm to organization both financially and reputationally.

### 1. Phishing

It is a social engineering attack, where attackers try to trick users into revealing sensitive information, by impersonating trusted organizations, as human beings are the weakest link of networks.<br>

**Target:** Human (Affects Confidentiality)  
**Ex:** Fake Lottery Emails  
**Prevention:** Social awareness, Fact-check every information.

### 2. Malware

It stands for Malicious Software, that targets systems, for the goal of stealing information, disrupting services.<br>

**Target:** Devices, Systems, Networks (Affects Confidentiality, Integrity, Availability)  
**Ex:** Brain Virus, Morris Worm, Trojan.  
**Prevention:** Not downloading suspicious files or accessing any sites.

### 3. DDoS (Distributed Denial of Service)

It is an attack that overwhelms any servers by flooding the system with requests through various affected systems simultaneously.<br>

**Target:** Service (Affects Availability)  
**Ex:** ICMP flooding, SYN flood attack.  
**Prevention:** Traffic filtering, Rate limiting.

### 4. SQL Injection

It is a web application attack that interferes with an application's database queries due to lack of sanitization of input.<br>

**Target:** Web Application & Databases (Confidentiality)  
**Ex:** Improper input that can be evaluated as a query in the database.  
**Prevention:** Proper sanitization of input, Parameterized queries/prepared statements (Input Validation).

### 5. Brute Force

It is an attempt to gain access by repeatedly trying different login credentials, until the correct combination is found.

- BurpSuite, Hydra, Medusa are used as tools.<br>

**Target:** Authentication Mechanism (Affects CIA)  
**Ex:** Login Page of organization without any CAPTCHA.  
**Prevention:** reCAPTCHA, CAPTCHA, Multi-Factor Authentication.

### 6. Ransomware

It is one of the malware that prevents users from accessing their data or system with ulterior motive of any value such as monetary or any assets.<br>

**Target:** Computer, data, networks (Availability, Integrity)  
**Ex:** Organization not availing services due to lack of access to the service portal.  
**Prevention:** Backups, Patching, Endpoint protection, Access controls.

<hr>

## Study Attack Vectors: Social Engineering, Wireless Attacks, Insider Threats

## Attack Vector

**Attack Vector:** It is the method or means that an attacker uses to gain unauthorized access to a system, network, application, or information.

### Types

- **Social Engineering:** Phishing such as Vishing, Whaling, Spear Phishing, Smishing.
- **Malware:** Virus, Worms, Ransomware.
- **Password Attacks:** Brute Force, Dictionary, Keylogging.
- **Web Application Attacks:** SQL Injection (SQLi), Cross-Site Scripting (XSS), Cross-Site Request Forgery (CSRF).
- **Network Attacks:** Man-in-the-Middle (MitM), ARP Spoofing, DNS Spoofing.
- **Software Vulnerabilities:** Zero-day exploits.
- **Physical Attack Vectors:** USB malware, Device Theft.
- **Cloud-Based Attack Vectors:** Insecure APIs, Stolen cloud credentials.
- **Wireless Attacks:** Misconfigured Firewall, Evil Twin attacks.

## 1. Social Engineering

It is considered that Humans are one of the weakest links in the chain. Hence, it is the act of manipulating, deceiving users by impersonating a trusted entity, to attain PII/SPII (Sensitive Personal Identifiable Information).

### Types

#### 1. Phishing

The act of tricking users into providing information by fraudulent means.

**Attack Vector:** Emails/messages.

#### 2. Smishing

The act of phishing through SMS/Text messages.

**Attack Vector:** SMS.

#### 3. Vishing

The act of phishing through Voice messages.

**Attack Vector:** Phone Call.

#### 4. Baiting

The act of tempting/persuading an individual to attain sensitive Information.

**Attack Vector:** Social Engineering

#### 5. Tailgating

The act of physically following an authorized user into a restricted area.

**Attack Vector:** Physical Access.

### Prevention

- Verify Sender
- Remain calm under pressure
- Be socially aware
- Don't share credentials

## 2. Wireless Attacks

It targets wireless networks, devices, or communication to gain unauthorized access, intercept information, or even compromise the integrity.

### Types

#### 1. Evil Twin Attack

It is an act of impersonating a legitimate wireless access point, with the motive of stealing credentials or intercepting traffic (On-path, Replay, Smurf attack).

**Example:** Connecting to any network having a similar name to an organization, without verifying.

**Prevention:**
- Use of HTTPS
- Avoid unknown/untrusted networks
- Verify Wi-Fi before connecting

#### 2. Packet Sniffing

The process of capturing network traffic to observe communication, which can risk exposing SPII/PII.

**Example:** Being over untrusted networks while transmitting sensitive information.

**Prevention:**
- Encrypted connection
- Use HTTPS

#### 3. Deauthentication Attack

The attack which causes wireless connection to lose its connection to an access point by forging deauthentication management frames, impersonating as target.

**Example:** While transmitting information, losing connection causes discomfort, and the critical information may cause loss.

**Prevention:**
- Network segmentation
- WPA2/WPA3

## 3. Insider Threat

When the threat originates from a legitimate access to an organization's system, network, data due to compliance issues or vulnerabilities.

### Types

#### 1. Malicious Insider

When any individual misuses the authority access to harm organization due to any ulterior motive.

*Example:* Employee accessing confidential files with intention of misusing/exposing information.

#### 2. Negligent/Accidental Insider

When an employee unintentionally causes a security incident due to a mistake.

**Example:** An employee sending confidential files to the wrong recipient, accidentally.

#### 3. Compromised Insider Account

When the authorization of a legitimate employee is compromised by an external attacker.

**Example:**  
An employee who has access to the database is targeted and files are accessed by the attacker.

### Prevention

- Least-privilege access
- Access Control
- Data classification
- Monitoring and Logging
- Regular Permission Reviews