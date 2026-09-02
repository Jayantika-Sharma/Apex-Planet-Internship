# Networking Basics
## 1.OSI Model Layers & Functions
*OSI*:Open Systems interconnection
- It was created bt International Organization for standardization,which enables  devices to communicate over a network.
**Layers**<br>
1. Physical Layer
2. Data Link Layer 
3. Network Layer
4. Transport Layer
5. Session Layer
6. Presentation Layer 
7. Application Layer
### Physical Layer
- The Physical Layer is the lowest layer of the OSI model.
- It deals with the actual transmission of raw bits (0s and 1s) through a physical medium,by voltage supply.

#### Main functions:
1. Transmits bits through cables, fiber, or wireless signals.
2. Converts digital data into electrical, optical, or radio signals.
#### Data unit: Bits
#### Examples:
1. Ethernet cables
2. Fiber-optic cables
#### Devices:
Hub,Repeater

### Data Link Layer 
It provides node-to-node communication and is responsible for transferring data between devices on the same network.

#### Main functions:
1. Converts packets into frames.
2. Uses MAC addresses to identify devices.
3. Detects errors in transmitted frames.
Controls access to the transmission medium.

- It has two sublayers:
1. LLC (Logical Link Control)
2. MAC (Media Access Control)
#### Data unit: Frame
#### Examples:
1. Ethernet
2. Wi-Fi (802.11)

#### Devices:
Switch, Bridge

### Network Layer
It is responsible for logical addressing and routing. It determines how packets should travel from the source network to the destination network.
#### Main functions:
1. Provides logical addressing using IP addresses.
2. Performs routing.
3. Selects the best path between networks.

#### Data unit: Packet
#### Examples:
1. IPv4/IPv6
2. ICMP

#### Device: 
Router

### Transport Layer
It is responsible for end-to-end delivery of data between applications. It provides reliable or fast communication depending on the protocol used.

#### Main functions:
1. Provides reliable data delivery using TCP.
2. Provides fast connectionless delivery using UDP.
3. Uses port numbers to identify applications.
#### Data unit: Segment (TCP) / Datagram (UDP)
#### Examples:
1. TCP
2. UDP
#### Device:
Firewall, Load Balancer

### Session Layer
It is responsible for establishing, managing, and terminating communication sessions between applications.

#### Main functions:
1. Establishes communication sessions.
2. Maintains and manages sessions.
3. Terminates sessions when communication is complete.
#### Data unit: Data
#### Examples:
1. RPC
2. NetBIOS
#### Device:No specific dedicated device

### Presentation Layer
It is responsible for translating, encrypting, and compressing data so that different systems can understand it.

#### Main functions:
1. Performs data translation and format conversion.
2. Provides encryption and decryption.
3. Performs data compression and decompression.
#### Data unit: Data
#### Examples:
1. ASCII/Unicode
2. JPEG/PNG
3. SSL/TLS
#### Device:
No specific dedicated device

### Application Layer
It is responsible for providing network services directly to applications and users.
#### Main functions:
1. Provides services such as web browsing, email, and file transfer.
2. Allows applications to communicate over a network.
3. Provides protocols for different network services.
#### Data unit: Data
#### Examples:
1. HTTP/HTTPS
2. FTP
3. SMTP
4. DNS
#### Device:
No specific dedicated device

## 2.TCP/IP Protocol Suite
The **TCP/IP Protocol Suite** is a collection of communication protocols used to connect devices and transfer data over networks, including the Internet. It defines how data is **addressed, transmitted, routed, and received**.
**Layers**:
1. Application
2. Transport
3. Internet
4. Network Access

### Application Layer

It is responsible for providing network services directly to applications and users.<br>
It combines the functions of the **Application, Presentation, and Session layers** of the OSI model.

#### Main functions:
1. Provides services such as web browsing, email, and file transfer.
2. Provides protocols for application-to-application communication.
3. Handles data representation and session-related functions.
#### Data unit: Data
#### Examples:
1. HTTP/HTTPS
2. FTP/SMTP
3. DNS
4. SSH
#### Device:
No specific dedicated device

### Transport Layer
It is responsible for providing **end-to-end communication** between applications on different devices.

#### Main functions:
1. Provides reliable communication using TCP.
2. Provides fast connectionless communication using UDP.
3. Uses port numbers to identify applications.
4. Performs flow and error control.
#### Data unit: Segment (TCP) / Datagram (UDP)
#### Examples:
1. TCP
2. UDP
#### Device:
Firewall, Load Balancer

### Internet Layer
It is responsible for **logical addressing and routing** of packets between different networks.
#### Main functions:
1. Provides IP addressing.
2. Performs routing and packet forwarding.
3. Determines the path for packets between networks.
4. Handles communication between different networks.
#### Data unit: Packet
#### Examples:
1. IPv4/IPv6
2. ICMP
#### Device:
Router

### Network Access Layer
It is responsible for transferring data between devices over the **physical network medium**.<br>
It combines the functions of the **Data Link and Physical layers** of the OSI model.
#### Main functions:
1. Converts packets into frames.
2. Uses MAC addresses for local communication.
3. Transmits data through cables, fiber, or wireless signals.
#### Data unit: Frame / Bit
#### Examples:
1. Ethernet/Wi-Fi
2. ARP
#### Device:
Switch, Hub, Repeater

## 3.DNS & HTTP/HTTPS Deep Dive

## DNS (Domain Name System)
DNS is responsible for **converting domain names into IP addresses** so that devices can locate servers on a network.

For example: www.google.com -> IP address of Google Server

### Main functions:
1. Converts domain names into IP addresses.
2. Helps locate servers and network services.
3. Provides information such as mail servers using different DNS records.
4. Makes websites accessible using easy-to-remember domain names.
### How DNS works:
When you enter: www.example.com<br>
The following process generally occurs:
1. Your browser checks its DNS cache.
2. The operating system checks its local DNS cache.
3. The request is sent to a **DNS resolver**.
4. The resolver queries the DNS hierarchy if the answer is not already cached.
5. The resolver may contact the **Root DNS server**.
6. The Root server directs it toward the appropriate **TLD server** such as `.com`.
7. The TLD server directs the resolver to the domain's **authoritative DNS server**.
8. The authoritative server provides the IP address.
9. The resolver returns the IP address to your device.
10. Your browser can then connect to the server.
### DNS Hierarchy:
Root → TLD → Authoritative DNS Server → IP Address
Example:www.example.com
* . -> Root
* .com-> Domain (TLD)
* www → Subdomain/hostname

### Important DNS Records:

**A Record:** Maps a domain name to an IPv4 address.
**AAAA Record:** Maps a domain name to an IPv6 address.
**CNAME Record:** Creates an alias for another domain name.
**MX Record:** Specifies mail servers for a domain.
**NS Record:** Specifies authoritative name servers.
**TXT Record:** Stores text information, commonly used for domain verification and email-security policies.

### DNS Port:
**UDP 53** → Common DNS queries
**TCP 53** → Used when TCP is required, such as some larger responses and DNS zone transfers.

## HTTP (HyperText Transfer Protocol)

HTTP is an **application-layer protocol** used to transfer resources such as web pages, images, and other data between a client and a server.

Example:
- Browser → HTTP Request → Web Server
- Web Server → HTTP Response → Browser

### Main functions:
1. Allows clients and servers to communicate.
2. Transfers web resources.
3. Uses requests and responses.
### HTTP Request
A client sends a request to a server.
Example structure:
```text
GET /index.html HTTP/1.1
Host: example.com
```
_*Important parts*_:
**Method:** Specifies what action is requested.
**URL/Path:** Specifies the resource.
**Headers:** Provide additional information.
**Body:** Contains data sent to the server when required.
### Common HTTP Methods:
**GET:** Requests data from a server.
**POST:** Sends data to a server, commonly for submitting forms.
**PUT:** Replaces or updates a resource.
**PATCH:** Partially updates a resource.
**DELETE:** Requests deletion of a resource.
### HTTP Response
The server sends a response back to the client.
Example:
```text
HTTP/1.1 200 OK
Content-Type: text/html
```
### HTTP Status Codes
**1xx – Informational**
Request is being processed.
**2xx – Success**
200 OK -> Request successful
201 Created -> Resource created
**3xx – Redirection**
301 Moved Permanently -> Resource permanently moved
302 Found -> Temporary redirection

**4xx – Client Error**
400 Bad Request -> Invalid request
403 Forbidden -> Server refuses required
404 Not Found -> Resources not found

**5xx – Server Error**
500 Internal Server Error -> Server encountered an error
503 Service Unavailable -> Server temporarily unavailable


# HTTPS

HTTPS stands for **HyperText Transfer Protocol Secure**.

It is HTTP transmitted over a **secure TLS connection**.

HTTPS provides:

1. **Encryption** – Protects data from being read by unauthorized parties.

2. **Authentication** – Helps verify that you are communicating with the intended website.

3. **Integrity** – Helps detect whether data has been modified during transmission.

## 4.IP Addressing, Subnetting, and NAT

### IP Addressing

**IP Address (Internet Protocol Address)** is a logical address assigned to device/interface,such that it can identify and communicate.

#### Application

- Identifies a device on a network.
- Helps locate a device.
- Allows devices to communicate with each other.

#### Types of IP Address
**Types:**
1. IPv4 (32-bit address)
2. IPv6 (32-bit address)

#### IPv4

An IPv4 address consists of **4 octets**.
Each octet has a value from **0 to 255**.

```text
192 . 168 . 1 . 10
```

### Private IP Address Ranges
**Range**    
                       
- `10.0.0.0 – 10.255.255.255`     
- `172.16.0.0 – 172.31.255.255`   
- `192.168.0.0 – 192.168.255.255` 

_Example:_

```text
192.168.1.10
```

#### Public IP Address

A **Public IP** is used to communicate over the Internet.

Example:

```text
8.8.8.8
```

---

### Subnetting

**Subnetting** is the process of dividing one large network into smaller networks called **subnets**.

#### Advantages:

- Reduces network traffic.
- Improves network performance.
- Makes network management easier.
- Improves security and network isolation.
- Uses IP addresses efficiently.

#### Example

A network:

```text
192.168.1.0/24
```

can be divided into:

```text
192.168.1.0/26
192.168.1.64/26
192.168.1.128/26
192.168.1.192/26
```

Each `/26` subnet has:

```text
64 total addresses
62 usable host addresses
```

The network address and broadcast address are normally not assigned to hosts.

---

### Subnet Mask

A **Subnet Mask** identifies the **network portion** and **host portion** of an IP address.

_Example:_

```text
IP Address:   192.168.1.10
Subnet Mask:  255.255.255.0
CIDR:         /24
```

#### Common Subnet Masks

| CIDR  | Subnet Mask       | Total Addresses |
| ----- | ----------------- | --------------: |
| `/8`  | `255.0.0.0`       |      16,777,216 |
| `/16` | `255.255.0.0`     |          65,536 |
| `/24` | `255.255.255.0`   |             256 |
| `/25` | `255.255.255.128` |             128 |
| `/26` | `255.255.255.192` |              64 |
| `/27` | `255.255.255.224` |              32 |
| `/28` | `255.255.255.240` |              16 |
| `/30` | `255.255.255.252` |               4 |

## Usable Host Formula

```text
Usable Hosts = 2^h - 2
```

Where `h` is the number of host bits.
### NAT

**NAT (Network Address Translation)** translates private IP addresses into public IP addresses and vice versa.

NAT is commonly performed by a **router or firewall**.

#### Uses:

- Allows private devices to access the Internet.
- Conserves public IPv4 addresses.
- Allows multiple devices to share a public IP.
- Keeps internal private addresses from being directly exposed to the Internet.

### Example

Private network:

```text
PC      → 192.168.1.10
Phone   → 192.168.1.11
Laptop  → 192.168.1.12
```

The router can use one public IP:

```text
Public IP → 203.0.113.10
```

The router performs the translation between the private and public addresses.

---

# 6. Types of NAT

| Type            | Description                                                           |
| --------------- | --------------------------------------------------------------------- |
| **Static NAT**  | One private IP is mapped to one public IP                             |
| **Dynamic NAT** | Private IPs are mapped to a pool of public IPs                        |
| **PAT**         | Multiple private IPs share one public IP using different port numbers |

