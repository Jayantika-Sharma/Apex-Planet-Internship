# Reconnaissance
- It is the information gathering phase of a cybersecurity assessment.

**Goal**:To understand a target's attack surface,infrastructure, technologies.domains,hosts,services and publically exposed information,before exploitation.

## Types

1. Active Reconnaissance
2. Passive Reconnaissance

### Active Reconnaissance
_Direct interaction_ between target and attacker systems,to understand vulnerabilities and risk.
- _High risk_ of getting detected and logged.

**Example**: Ping Sweep,Port Scanning,Banner Grabbing,Enumeration.

### Passive Reconnaissance
_Indirect interaction_ between target and attacker systems,to understand vulnerabilities and risk.
- _Low risk_ of getting detected and logged.

**Example**: Search engines,WHOIS,Certificate Transparency,Shodan.
<hr>
<hr>

# Passive Reconnaissance
## 1. Whois
It is a protocol/service used to retrieve registration information about majorly public internet resources,especially domain names.

### List of Information

1. *Domain Name*: Registered domain
2. *Registar*: Company managing
3. *Registry*: Organization
4. *Creation date*: Registration date
5. *Updated Date*: Last Registration date
6. *Expiration Date*: Current expiration date
7. *Domain Status*: Status Code
8. *Name Servers*: DNS servers associated
9. *Registrant*: Registrant information
10. *Administrative Contact/Technical Contact*: May be disclosed.

### Limitation

1. All sub-domain
2. Open parts
3. Open ports

### Information Exposed

1. Phishing/Social Engineering
Email,owner name and registrant information

2. To steal domain
Expiry Date

3. To understand structure
Nameserver

### Methods

#### _1.Website_
*URL*:https://www.whois.com
<img src="../Image/Whois_site.png" alt="Whois_website" width="250">
<br>
*Public Google information*

#### _Kali Linux_
It is preinstalled in Kali Linux.
*Commands*:
1. whois <Domain/Public IP>: To extract information. 
2. whois <Domain/Public IP> <path of file>: To store the output
<hr>

## 2. Nslookup
It is a command line query tool thet retrieve information about a domain name,hostname,dns record.
- Stands for Nameserver Lookup.

### Record Types
_nslookup -TYPE=<RECORD> <Domain/Public IP>_
- A : Domain(IPv4 address)
- AAAA : Domain(IPv6 address)
- MX : Mail Server
- NS : Authoritative nameserver
- CNAME: Alias for hostname
- TXT : Text/verification/security information
- SOA : Start of Authority information
- PTR : IP -> hostname
### Commands
1. nslookup <Domain/Public IP>
2. nslookup -TYPE=<RECORD> <Domain/Public IP>

## 3. Google Dorking
It is used to find specific information that search engines have already indexed & advance search operator.
- It is also known as *Google Hacking*.
### Common Operators
#### site:
site:<domain>
#### filetype
filetype:<extension>
#### intitle
intitle:<keyword>
#### inurl
inurl: <url>
#### intext
intext:<keyword>
#### Exact Phrase
"<Phrase>"
#### "-" (To exclude term)
-<word>
#### OR(Alternative)
site:<site> <Term1> OR <Term2>
*Operators can be combined*
<hr>

## 4. Shodan
It is a search engine for internetconnected devices and services.
It indexes information about servers, routers, webcams, databases, IoT devices, systems.

### Query
1. org:<org name>
2. hostname: <domain>
3. net: <IP/CIDR range>
4. port:<port number>
5. country: <first two letter>
6. product: <name>
7. os: <name of os>
8. ssl: <domain>

<hr><hr>

# Active Reconnaissance
## Ping Sweep
It is a host-discovery technique used to determine which hosts (devices) are reachable/alive within a network range.
- Instead of checking one IP,it checks multiple hosts.
- It doesn't scan ports.
### Commands
- nmap -sn <x.x.x.1-20>
- nmap -sn <x.x.x.0/24>
- nmap -sn <IP-1> <IP-2>....
### Limitation
-  It is not accurate,as:
1. Host is offline
2. Blocks ICMP
3. Firewall filter
4. Host is configured to not respond. 

## Banner Grabbing
It is an active reconnaissance technique used to identify information about a network service running on a target host.
### Commands
- nmap -sV -p <port no> <IP addr>
- nmap -sV -p <port 1>,<port 2>... <IP addr>
- nmap -sV -p <port start>-<port end> <IP addr>