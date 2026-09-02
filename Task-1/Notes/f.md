
## 4.IP Addressing, Subnetting, and NAT

### IP Addressing

**IP Address (Internet Protocol Address)** is a unique address assigned to a device on a network.

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

