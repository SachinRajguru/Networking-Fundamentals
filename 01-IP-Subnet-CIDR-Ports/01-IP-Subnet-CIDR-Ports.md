
## Section 1: IP Addresses, Subnets, CIDR, and Ports

---

### 1. IP Addresses

#### What is an IP Address?

- An IP address is a **unique identification number** assigned to each device connected to a network
- It acts like a "house number" for devices, allowing you to identify and manage them

#### Why is it Needed?

- Without unique IDs, you can't track or control devices
- Example: In a home network with 4 devices, if one device accesses a payment site, you need to know which one to block

#### Analogy

Imagine a house with 4 people, each with devices. If one device causes issues (e.g., a kid accessing Instagram), you need unique IDs to block just that device without affecting others.

---

#### IPv4 vs IPv6

##### IPv4 (Focus of This Guide)

- **Format**: `192.168.1.2` or `172.16.3.4`
- Divided into **4 parts (octets)** separated by dots
- Each octet ranges from **0 to 255**

##### Why 0-255?

- Each octet is **8 bits** (1 byte)
- With 8 bits, you can represent 256 values (2^8 = 256, from 0 to 255)

##### Total Unique Addresses in IPv4

- 4 octets × 8 bits = **32 bits total**
- 2^32 possible addresses (about 4.3 billion)

##### IPv6 (The Future)

- **Format**: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
- Uses **128 bits** (much larger address space)
- Solves IPv4 exhaustion problem (~4.3 billion → ~340 undecillion addresses)
- Not covered in this guide, but good to know exists

---

#### Binary Representation Example

IP: `192.168.1.2`

| Octet | Decimal | Binary   |
|-------|---------|----------|
| 1st   | 192     | 11000000 |
| 2nd   | 168     | 10101000 |
| 3rd   | 1       | 00000001 |
| 4th   | 2       | 00000010 |

Full 32-bit string: `11000000101010000000000100000010`

---

#### Subnet Mask Quick Look

| CIDR | Subnet Mask (Binary)      | Subnet Mask (Decimal) |
|------|---------------------------|----------------------|
| /24  | 11111111.11111111.11111111.00000000 | 255.255.255.0     |
| /16  | 11111111.11111111.00000000.00000000 | 255.255.0.0       |
| /8   | 11111111.00000000.00000000.00000000 | 255.0.0.0         |

The `1` bits = network portion, `0` bits = host portion

---

#### Valid vs Invalid Examples

- **Valid**: `172.16.3.4`, `10.1.2.4`, `192.168.12.4`
- **Invalid**: `600.12.254.10` (600 > 255)

#### How to Check Your IP

- **Windows**: Run `ipconfig` in terminal
- **Linux/Mac**: Run `ifconfig` in terminal

---

#### Key Takeaway

> IP addresses uniquely identify devices. IPv4 uses 32 bits in a dotted format (0-255 per octet). IPv6 expands this to 128 bits.

---

### 2. Subnets

#### What is a Subnet?

- A subnet is a **subdivision of a larger network**
- Provides **security, privacy, and isolation**

#### Why is it Needed?

- In a shared network, if one device gets hacked, the hacker can access everything
- Subnets prevent this by isolating groups

#### Analogy

An office with 65,000 IP addresses (like a VPC in AWS):

- **Finance Subnet**: For sensitive data (e.g., payroll)
- **General Subnet**: For everyone

If a hacker infects one device in the general subnet, they can't reach finance.

---

#### Types of Subnets

| Type          | Internet Access | Use Case                    |
|---------------|-----------------|-----------------------------|
| Private       | No              | Internal databases         |
| Public        | Yes             | Web servers                 |

#### How to Enable Internet Access (AWS Example)

- Attach a route table to the subnet
- Add destination `0.0.0.0/0` pointing to an internet gateway

---

#### Benefits of Subnets

- **Security**: Hackers can't jump between subnets
- **Privacy**: Sensitive data stays isolated
- **Isolation**: Easier management

---

#### Examples

- **Home Wi-Fi**: Create subnets for "heavy appliances" vs. "kids' devices"
- **Office**: Secure subnet for HR data, free subnet for general use

---

#### Key Takeaway

> Subnets split networks for security. Private = no internet; Public = internet access via gateways.

---

### 3. CIDR (Classless Inter-Domain Routing)

#### What is CIDR?

- CIDR defines **how many IP addresses** are in a subnet
- Format: `172.16.3.0/24`

#### Understanding the Slash Notation

| Slash | Number of IPs | Formula          |
|-------|---------------|------------------|
| /24   | 256           | 2^(32-24) = 2^8  |
| /27   | 32            | 2^(32-27) = 2^5  |
| /30   | 4             | 2^(32-30) = 2^2  |
| /16   | 65,536        | 2^(32-16) = 2^16 |

> **Note**: For /30 (and similar small subnets), typically 2 IPs are reserved for network/broadcast addresses, leaving **2 usable IPs** for endpoints.

---

#### How to Choose CIDR

1. Pick an IP from your VPC range (e.g., VPC: `172.16.0.0/16`)
2. Represent it in 32 bits (8 bits per octet)
3. Decide how many IPs you need

| Required IPs | CIDR Notation |
|--------------|---------------|
| 256          | /24           |
| 64           | /26           |
| 32           | /27           |
| 2            | /31           |

---

#### CIDR Examples

- **VPC**: `172.16.0.0/16` (65,536 IPs)
- **Finance Subnet**: `172.16.3.0/24` (256 IPs)
  - Range: 172.16.3.0 to 172.16.3.255
- **Small Subnet**: `172.16.3.0/30` (4 IPs, 2 usable)
  - Range: 172.16.3.0 to 172.16.3.1 (for two devices)

---

#### Private IP Ranges

Defined in **RFC 1918** to avoid conflicts with public IPs:

| Private Range              | Example              |
|---------------------------|----------------------|
| 10.0.0.0/8                | 10.1.2.3             |
| 172.16.0.0/12             | 172.16.3.4           |
| 192.168.0.0/16            | 192.168.1.1          |

---

#### Key Takeaway

> CIDR specifies subnet size. Formula: IPs = 2^(32 - slash).

---

### 4. Ports

#### What is a Port?

- A port is a **unique number** for an application on a device
- Distinguishes different apps running on the same device

#### Port Range

- **0 to 65,535**
- Avoid reserved ports

#### Common Reserved Ports

| Port  | Service    |
|-------|------------|
| 80    | HTTP       |
| 443   | HTTPS      |
| 3306  | MySQL      |
| 8080  | Jenkins    |

---

#### Why Are Ports Needed?

- A server can run multiple apps
- Ports route requests to the correct application

#### Examples

- Web app on port 9191: Access via `publicIP:9191`
- Another app on port 5162: Access via `publicIP:5162`

---

#### Key Takeaway

> Ports identify apps on a device. Choose unique, non-reserved numbers (e.g., 9000+).
