# Cryptography Basics
**Cryptography**: It is the science of protecting information using mathematical techniques to ensure confidentiality,integrity,and authentication.
- It encrypts readable data into unreadable form,to prevent unauthorised access and tampering.
- Uses for:
1. Secure communication
2. Digital Signature

## 1.Symmetric vs Asymmetric Encryption.
## Symmetric vs Asymmetric Encryption

| Feature | Symmetric Encryption | Asymmetric Encryption |
|---|---|---|
| Keys Used | One shared secret key | Two keys: Public Key & Private Key |
| Encryption & Decryption | Same key is used | Different keys are used |
| Speed | Faster | Slower |
| Security | Depends on secure key sharing | Private key remains secret |
| Key Distribution | Difficult | Easier because public key can be shared |
| Large Data | Suitable for large amounts of data | Generally not preferred for bulk data |
| Digital Signature | Not typically used | Supports digital signatures |
| Examples | AES, ChaCha20, DES | RSA, ECC |
| Main Use | Data encryption | Authentication, key exchange, digital signatures |
## 2.Hashing (MD5, SHA256)
**Hashing**:It is a mathematical algorithm that convert messages of any arbitrary length into fixed length output,which is also known as hash value/Digest.

Example: SHA-1,SHA-256,MD5,MD6

### MD5
- It produces 128 bit hash value from input data of any size.
- It was designed for data integrity verification.
- It is not secure for modern cryptographic purpose
- *Application*:checksums, digital signatures, and file verification.

### SHA 256
- It is a cryptographic hash that belongs to SHA-2 family.
- It converts input data of any length into fixed _256 bit_ hash value.
- *Application*: security application(data integrity verification, digital signatures), blockchain technology, and password hashing.

## 3.Digital Certificates & SSL/TLS.

### Digital Certificates:
It is a public key,which is used to establish cryptographic link between owner and entity.

It holds metadata of certificate holder,identity information and digital signature of the public key,created by certificate issuer,verifies the legitimacy of a device/server/user.

It is issued by **Certifying Authority**(CA).

#### Types:
##### Extended Validation
It provides comprehensive business authentication,which handle extremely sentive data.
##### Client Certificate
It uniquely identify person/user to one another.
##### Code Signing Certificate
It is used to verify  legitimacy of software or files obtained from the internet.

#### TLS.SSL Certificate
It secure encrypted and confidential communication with its customer.

#### Application:
1. Secure Websites
2. Email Security
3. Verify Identities
4. IoT Device Security

#### Features:
1. Scalability
2. Public Trust
3. Security
### SSL(Secure Socket Layer)
It encrypts data to secure communication beteen devices over a network.
- Developed by Netscape in 1995.
- It is predecessor of TLS,which is standard protocol for secure communications on the internet.


### TLS(Transport Layer Security)
It is designed to provide security at the transport layer.

It ensures no third party can eavesdrop on or tamper with any message transmitted between a client and a server.
### SSL/TLS:
This is used to establish sessions ,which allows client and server to verify each other by transferring series of messages.

It works in 4 phases.
1. Selection of version of protocol to use.
- Client and server exchange hello-packets with each other to confirm connection.
2. Digital Certificate
- Server sends certificate and server-key exchange.
3. Verification
- Client respond to the server by sending certificates and client-exchange-key.
4. Change Cipher Suite
- All verifications are completed after this Handshake Protocol.

## 4.Hands-on: Encrypt and Decrypt messages using OpenSSL
### Encryption process:
<img src="./Images/OpenSSL/Encryption.png" height=200px>

### Encrypted Process:
<img src="./Images/OpenSSL/Encrypted.png" height=200px>


# Tool Familiarization
## 1.Wireshark (packet capture)

It is an packet sniffing open source network protocol analyzer that inspect,analyze network packets,in real time.

*Packet Capture* : Process of collecting netwwork packets travelling through a network interface.

WireShark displays capture packets information such as:
- Source IP address
- Destination IP address
- Protocol
- Source and destination ports
- Packet Size
- Time of Transmission

### Common Protocols Used:
1. *Ethernet*: Local network communication.
2. *ARP*: Maps IP address to MAC address.
3. *IP*:  Logical addressing and routing.
4. *TCP*:  For reliable communication.
5. *UDP*:  Fast,connectionless,unsecure communication.
6. *DNS*:  Converts domain name to IP address.
7. *HTTP*:  Web Communication.
8. *HTTPS*:  Encrypted web communication.
9. *ICMP*:  Network diagnostics.  
### Application:
1. Network troubleshooting
<img src="./Images/Wireshark/ICMP.png" height=200px>
2. Protocol analysis
<img src="./Images/Wireshark/dns.png" height=200px>
- In cmd: nslookup google.com
3. Network performance monitoring
<img src="./Images/Wireshark/tcp_analysis.png" height=200px>
- In cmd: ping 8.8.8.8 -n 20
4. Debugging applications
<img src="./Images/Wireshark/debugging.png" height=200px>
5. Detecting unusual network activity
<img src="./Images/Wireshark/Repeated.png" height=200px>

## 2.Nmap (network scanning).
_MetaSploit2 is used as target._
It is an open source network scanning and security auditing tool.
### Basic Syntax
nmap [options] <target>

- scanme.nmap.org :Authorized practice target.
### Host Discovery
#### List Scan (-sL)
It list all target hosts,without actually scanning them.

**nmap -sL <target>**
#### Ping(No port) Scan (-sn/-sP)
It discovers hosts _without_ performing port scans.

**nmap -sn <target>**
<img src="./Images/nmap/sL-Sn.png" height=200px>

#### Skip Host Discovery (-Pn)
It treats the host status as up and proceeds with port/service requests.

It is useful when host is active,but firewall is refraining from discovery.

**nmap -Pn <target>**
<img src="./Images/nmap/Pn.png" height=200px>

#### ICMP Echo Ping (-PE)
It uses traditional ICMP ping mechanism,to discover active/reachable hosts.

**nmap -PE <target>**
<img src="./Images/nmap/PE.png" height=200px>>

#### TCP SYN Ping (-PS)
It sends TCP packets to one or more specified ports to determine if host is reachable or not.

**nmap -PS<port> <target>**
<img src="./Images/nmap/PS.png" height=200px>>

### TCP SYN Scan (-sS)
It is often referred as an *Half-open Scan* or _stealth Scan_, as it doesnt complete TCP connection.
**nmap -sS <target>**
<img src="./Images/nmap/sS.png" height=200px>
<hr>

### Aggressive Scan (-A)
It provides more information than any basic scan and generate more traffic.
**nmap -A <target>**
<img src="./Images/nmap/A.png" height=200px>

### Top Scan
**nmap --top-ports <number> <target>**
<img src="./Images/nmap/top.png" height=200px>

### Ouput
- nmap -oN <name.txt> <target>  :Text File
- nmap -oX <name.xml> <target>  :XML File
- nmap -oA <name> <target> :Creates txt,XML,gnmap File
<hr>

### Application:
1. Discover active hosts on network.
2. Identify open, closed ports.
**nmap -Pp<port_number> <target>**
<img src="./Images/nmap/port.png" height=200px>
3. Detect services running on open ports.
4. Determine service versions.
**nmap -sV <target>**
<img src="./Images/nmap/sV.png" height=200px>

## 3.Burp Suite (web proxy).


<hr>

## 4.Netcat (network debugging)

It is a command-line networking utility used to establish TCP/UDP connections, listen for connections, send/receive data, and test network services.<br>
It is commonly described as a general-purpose networking utility.
### Syntax
nc [options] <host> <port>
### Options
`-l` -	Listen for incoming connections<br>
`-v` -	Verbose output<br>
`-n` -	Do not perform DNS lookup<br>
`-u` -	Use UDP instead of TCP<br>
`-z` -	Zero-I/O; useful for checking ports<br>
`-w` -	Set connection timeout<br>
`-k` -	Keep listening for additional connections<br>
### *Lab Setup*
**Target Machine** :192.168.56.3<br>
**Attacker Machine** :192.168.56.4
**Modes:**<br>
1. Connect mode - acts as a client
2. Listen mode - waits for incoming connections and acts as a server

### Application:
#### Port Scanning
**nc -zv <Target IP> <port>**
It check whether TCP ports are accepting connections using TCP connection.
<img src="./Images/Netcat/Port_scan.png" height=200px>
-z : Doesn't send application data 
-v : Shows connection information

**Application**: Troubleshooting,Security auditing

#### File Transfer
Netcat can be used to transfer a file between two machines by creating a TCP connection between a sender and a receiver.
##### Steps:
- File Creation:
<img src="./Images/Netcat/File_create.png" height=200px>

1. Receiver starts listening
<img src="./Images/Netcat/file_transfer_ms2.png" height=200px>
nc -lv 5000 > received.txt

2. Send File
<img src="./Images/Netcat/file_transfer_linux.png" height=200px>

#### Remote Shell Access
It refers to the interaction of command-line shell on another computer through a network connection.Instead of entering commands directly on the target machine, a user can interact with its shell remotely.

#### Data Tunneling
It is the process of transporting data from one system to another by encapsulating it inside a network communication channel or protocol.
<img src="./Images/Netcat/file_transfer_ms2.png" height=200px>
<img src="./Images/Netcat/chat_linux.png" height=200px>

#### Reverse Shell
It is a type of remote shell connection in which the target machine initiates a connection back to the machine waiting for the connection.
<img src="./Images/Netcat/Kali.png" height=200px>
<img src="./Images/Netcat/shell.png" height=200px>

#### Security auditing
Version of ports can be obtained.
<img src="./Images/Netcat/Banner_Grabbing.png" height=200px>