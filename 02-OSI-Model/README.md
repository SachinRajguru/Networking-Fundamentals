
# Section 2: The OSI Model

---

## What You'll Learn

- **DNS Resolution** — Translating domain names to IP addresses
- **TCP Handshake** — The 3-way handshake before data transfer
- **OSI Model** — 7 layers of network communication
- **Data Encapsulation** — How data transforms as it travels
- **Layer Functions** — What each OSI layer does

---

## Learning Objectives

By the end of this section, you will be able to:

- Explain the DNS resolution process
- Describe the TCP three-way handshake
- Name all 7 layers of the OSI model in order
- Understand data flow (encapsulation & decapsulation)
- Correlate OSI layers to real-world networking
- Troubleshoot network issues using OSI knowledge

---

## Quick Overview

### Prerequisites

| Topic | Example |
|-------|---------|
| DNS Resolution | `google.com` → `8.8.8.8` |
| TCP Handshake | SYN → SYN-ACK → ACK |

### The 7 OSI Layers

| # | Layer | What It Does | Examples |
|---|-------|--------------|----------|
| 7 | Application | User interface | HTTP, DNS, browsers |
| 6 | Presentation | Encryption, formatting | SSL/TLS, JPEG, PNG |
| 5 | Session | Session management | Cookies, tokens |
| 4 | Transport | Data segments | TCP, UDP |
| 3 | Network | Packets & routing | IP, routers |
| 2 | Data Link | Frames & MAC addresses | Ethernet, switches |
| 1 | Physical | Signals | Cables, WiFi |

### Data Journey

```
Sending (Encapsulation):     Receiving (Decapsulation):
Data → Segments → Packets    Signals → Frames → Packets
       → Frames → Signals          → Segments → Data
```

---

## What You Need

- Basic understanding of IP addresses, subnets, and ports (from Section 1)
- Curiosity about how data travels across networks

---

## How to Use This Section

1. Start with prerequisites: DNS and TCP handshake
2. Learn the 7 layers in order (top to bottom)
3. Visualize the data flow from your browser to the server
4. Connect to real tools like Wireshark, ping, and traceroute

---

## Related Topics

- **Built upon**: Section 1 (IP, Subnets, CIDR, Ports)

### Next Steps

- Practice with network tools (ping, traceroute, netstat)
- Learn about firewalls and load balancers
- Explore cloud networking (VPC, AWS, Azure)

---

## Key Takeaway

> The OSI model is like a postal system: each layer handles a specific job (writing, packaging, addressing, transporting) and passes it to the next. Together, they ensure your data reaches its destination reliably.

---

## OSI Mnemonic

> **A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing

- **A**pplication
- **P**resentation
- **S**ession
- **T**ransport
- **N**etwork
- **D**ata Link
- **P**hysical

---

## File Structure

```
Networking-Fundamentals/
├── README.md                       # Course Overview
├── .gitignore
├── 01-IP-Subnet-CIDR-Ports/
│   ├── README.md                   # Section overview
│   └── 01-IP-Subnet-CIDR-Ports.md  # Detailed content
└── 02-OSI-Model/
    ├── README.md                   # You are here
    └── 02-OSI-Model.md             # Detailed content
```

---

[Start 02-OSI-Model →](./02-OSI-Model.md)
```
