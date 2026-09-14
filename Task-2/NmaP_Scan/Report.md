# Nmap Target Scan Analysis

## 1. Introduction

Nmapis a network scanning tool used to discover hosts, identify open ports, detect running services, and gather information about operating systems.

For this analysis,Nmap scan is used against Metasploitable2 virtual machine in virtual machine. 
---

# 2. Tools Used

- Kali Linux
- Nmap
- Metasploitable2
- Oracle VirtualBox

## Scans Performed


- sudo nmap -p- -sS -oA scans/all_tcp 192.168.56.3

- sudo nmap -sU --top-ports 100 -oA scans/udp_top100 192.168.56.3

- sudo nmap -sS -sV -O -oA scans/service_os 192.168.56.3

- sudo nmap --script vuln -oA scans/vuln 192.168.56.3

---

## 3. Lab Environment

| Component        | Details                      |
| ---------------- | ---------------------------- |
| Attacker Machine | Kali Linux                   |
| Attacker IP      | 192.168.56.4                 |
| Target Machine   | Metasploitable2              |
| Target IP        | 192.168.56.3                 |
| Network          | VirtualBox Host-Only Network |
| Tool             | Nmap                         |

---

## 4. Objectives

The main objectives of the scan were:

1. To check whether the target host was reachable.
2. To identify open TCP/UDP ports.
3. To identify the services and its version running on the open ports.
4. To identify the operating system.
---

# 5. Scanning Methodology
### TCP Port Scan

```sudo nmap -p- -sS -oA scans/all_tcp 192.168.56.3```

This scan checks all TCP ports from **1** to **65535**.

- `-p-` scans all TCP ports.
- `-sS` performs a TCP SYN scan.
- `-oA` saves the output in multiple formats.

### UDP Scan

```sudo nmap -sU --top-ports 100 -oA scans/udp_top100 192.168.56.3```

To checks the top 100 commonly used UDP ports.

### Service and OS Detection

```sudo nmap -sS -sV -O -oA scans/service_os 192.168.56.3```

- `-sV` attempts to identify service versions.
- `-O` attempts to identify the operating system.

### Vulnerability Scan

```sudo nmap --script vuln -oA scans/vuln 192.168.56.3```
---

# 6. Host Discovery

- It identified the host as **up**.

The target responded to an ARP request, confirming that the machine was reachable on the local Host-Only network.

The MAC address detected was:

```08:00:27:AA:89:E1```

The MAC address was identified as belonging to a VirtualBox virtual network interface.

---

# 7. TCP Port Scan Results

The full TCP scan checked all **65,535 TCP ports**.

The result showed:

* **30 open TCP ports**
* **65,505 closed TCP ports**
* The target host was up.

## Open TCP Ports

| Port | Service     | Version / Information      |
| ---: | ----------- | -------------------------- |
|   21 | FTP         | vsftpd 2.3.4               |
|   22 | SSH         | OpenSSH 4.7p1              |
|   23 | Telnet      | Linux telnetd              |
|   25 | SMTP        | Postfix smtpd              |
|   53 | DNS         | ISC BIND 9.4.2             |
|   80 | HTTP        | Apache httpd 2.2.8         |
|  111 | RPC         | rpcbind                    |
|  139 | NetBIOS/SMB | Samba                      |
|  445 | SMB         | Samba                      |
|  512 | rexec       | netkit-rsh rexecd          |
|  513 | rlogin      | login                      |
|  514 | rsh         | shell                      |
| 1099 | Java RMI    | GNU Classpath grmiregistry |
| 1524 | Bind Shell  | Metasploitable root shell  |
| 2049 | NFS         | NFS                        |
| 2121 | FTP         | ProFTPD 1.3.1              |
| 3306 | MySQL       | MySQL 5.0.51a              |
| 5432 | PostgreSQL  | PostgreSQL 8.3.x           |
| 5900 | VNC         | VNC protocol 3.3           |
| 6000 | X11         | X11                        |
| 6667 | IRC         | UnrealIRCd                 |
| 8009 | AJP13       | Apache Jserv               |
| 8180 | HTTP        | Apache Tomcat              |

---

# 8. TCP Service Analysis

## FTP - Port 21

The FTP service was identified as:**vsftpd 2.3.4**

- It has a known backdoor vulnerability.
---

## SSH - Port 22

The service was identified as:**OpenSSH 4.7p1**

SSH is normally used for secure remote administration.

It is an outdated version,which increases security risk if known vulnerabilities exist.

---

## Telnet - Port 23

Telnet was detected on port 23.

Telnet is an old remote-access protocol and does not provide the same protection as SSH for credentials and session data.
---

## HTTP - Port 80

Apache HTTP Server was detected:**Apache httpd 2.2.8**
---

## SMB - Ports 139 and 445

Samba services were detected on ports 139 and 445.

These ports are commonly associated with file and printer sharing.
---

## NFS - Port 2049

NFS was detected on port 2049.
-  It provides network-based file sharing. If incorrectly configured, it can expose files or resources to unauthorized users.
- NFS was also detected through the UDP scan.

---

## MySQL - Port 3306

MySQL was detected on:**3306/tcp**
- Version:**5.0.51a**

A database service being directly accessible over the network increases the attack surface and should normally be restricted to systems that actually require access.

---

## PostgreSQL - Port 5432

PostgreSQL was detected on port 5432.

The scan identified the version as being in the PostgreSQL 8.3 range.

This is an old database version.
---

## VNC - Port 5900

VNC was detected on port 5900 using protocol 3.3.

VNC provides remote graphical access.
---

# 9. UDP Scan Results

The UDP scan checked the top 100 UDP ports.

The scan identified the following ports as definitively open:

|     Port | Service              |
| -------: | -------------------- |
|   53/udp | DNS                  |
|   68/udp | DHCP client          |
|  111/udp | RPCbind              |
|  137/udp | NetBIOS Name Service |
| 2049/udp | NFS                  |

Some additional ports were reported as:
**open|filtered**
- The UDP results show that the target exposes services through both TCP and UDP.

---

# 10. Operating System Detection

The OS detection scan identified the target as approximately:
**Linux 2.6.9 - 2.6.33**
---

# 11. Vulnerability Scan

**sudo nmap --script vuln -oA scans/vuln 192.168.56.3**

The purpose was to check the target against vulnerability-related NSE scripts.
---

# 12. Major Vulnerability Findings

## vsFTPd 2.3.4 Backdoor

**Port:** `21/tcp`

**Service:** FTP

**Version:** `vsftpd 2.3.4`

The Nmap vulnerability script identified the well-known backdoor condition associated with vsFTPd 2.3.4.

The scan also reported an exploitable condition and root-level command output.

### Risk

This is a **critical finding** because the vulnerable service can potentially result in unauthorized system access.

### Recommendation

- Remove the vulnerable version of vsFTPd.
- Upgrade to a supported version.
- Disable FTP if it is not required.
- Restrict access to the service using firewall rules.

---

## Java RMI Remote Code Execution Risk

**Port:** `1099/tcp`

The Java RMI registry was detected on port 1099.

The vulnerability script reported that the service allows remote class loading, creating a potential remote-code-execution risk.

### Risk

This is a **high-risk finding** because an exposed Java RMI service with unsafe configuration can potentially allow an attacker to execute code remotely.

### Recommendation

- Disable Java RMI if it is not required.
- Restrict access to trusted hosts.
- Upgrade or properly configure the Java environment.
---
# 13. Web Application Findings

The vulnerability scan also identified several interesting paths under the web application.

Examples included possible:

```text
/admin/
```

and several JSP and upload-related paths.

The scan also reported possible SQL-injection locations in the Mutillidae application.

However, these results should be treated carefully.

Nmap's result indicates that these locations are **potentially interesting**, but this scan alone does not prove that every reported location is exploitable.

Further manual testing would be required to confirm individual web vulnerabilities.
---

# 14. Overall Risk Assessment

Based on the scan results, the target has a **high overall security exposure**.

The main reason is not only one vulnerability. The system has:

* Many open network services.
* Several old software versions.
* Legacy protocols such as Telnet and rsh.
* Exposed database services.
* Exposed file-sharing services.
* Remote administration services.
* Multiple web services.
* Known vulnerable software.
* Weak/obsolete cryptographic configurations.

### Risk Summary

| Area                   | Risk            |
| ---------------------- | --------------- |
| FTP                    | **Critical**    |
| Java RMI               | **High**        |
| SSL/TLS configuration  | **High**        |
| Legacy remote services | **High**        |
| SMB/NFS exposure       | **High**        |
| Web services           | **Medium–High** |
| Database exposure      | **Medium–High** |
| Excessive open ports   | **High**        |

---

# 15. Recommendations

Based on the scan, the following actions would improve the security of the system:

1. **Remove vulnerable software versions.**
2. Upgrade the FTP service.
3. Disable unnecessary services.
4. Replace Telnet with SSH for remote administration.
5. Restrict SMB and NFS access to trusted systems.
6. Restrict database ports using firewall rules.
7. Disable unnecessary Java RMI exposure.
8. Upgrade the Apache and Tomcat services.
9. Disable obsolete SSL/TLS protocols.
10. Replace weak cryptographic parameters.
11. Disable HTTP TRACE.
12. Configure secure session-cookie attributes.
13. Review web application upload functionality.
14. Regularly scan the system after applying security updates.
15. Use firewall rules to reduce the externally accessible attack surface.

---

# 16. Limitations of the Scan

Nmap is very useful for reconnaissance and vulnerability identification, but its results should not always be considered proof of a vulnerability.

For example:

* `open|filtered` does not necessarily mean a port is open.
* A version number does not automatically mean the service is vulnerable.
* NSE vulnerability scripts can identify possible vulnerability conditions.
* Some web application findings require manual verification.
* A complete security assessment would require additional testing and configuration review.

Therefore, the results in this report are based specifically on the Nmap scans performed against the lab target.

---

# 17. Conclusion

This Nmap scan helped me understand how a network scanner can be used to analyze a target system.

The scan showed that the Metasploitable2 machine had a large number of open TCP and UDP services. Service and OS detection provided additional information about the software and operating system running on the machine.

Overall, the target had a very large attack surface, which is expected from a deliberately vulnerable system such as Metasploitable2. This exercise gave me practical experience with Nmap port scanning, service enumeration, OS detection, UDP scanning, and NSE-based vulnerability analysis.

---

## Final Observation

The scan demonstrated how much information can be collected from a single target using Nmap. Starting with port discovery and then moving to service detection, OS detection, and vulnerability scanning made it easier to understand the security posture of the target step by step.