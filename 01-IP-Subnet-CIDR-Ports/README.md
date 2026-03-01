
# Section 1: IP Addresses, Subnets, CIDR & Ports

---

## What You'll Learn

- **IP Addresses** — Unique identifiers for devices on a network
- **IPv4 vs IPv6** — Understanding the difference and why IPv6 matters
- **Binary Conversion** — How computers see IP addresses
- **Subnets** — Dividing networks for security and isolation
- **CIDR Notation** — Defining subnet sizes efficiently
- **Ports** — Identifying applications on devices

---

## Learning Objectives

By the end of this section, you will be able to:

- Understand how IP addresses work and why they're needed
- Convert IP addresses between decimal and binary
- Explain the difference between public and private IPs
- Create and manage subnets for security
- Calculate CIDR ranges for different network sizes
- Identify ports and understand their role in networking

---

## Quick Overview

### IP Addresses

| Type | Format | Bits |
|------|--------|------|
| IPv4 | `192.168.1.1` | 32-bit |
| IPv6 | `2001:db8::1` | 128-bit |

### Subnets

| Type | Internet Access | Use Case |
|------|-----------------|----------|
| Private | No | Internal databases |
| Public | Yes | Web servers |

### CIDR

- **Format**: `172.16.0.0/16`
- **Formula**: `IPs = 2^(32 - slash)`

### Ports

- **Range**: 0 to 65,535
- **Common Ports**: HTTP (80), HTTPS (443), MySQL (3306), SSH (22)

---

## What You Need

- Basic computer knowledge
- A terminal (Windows CMD, Linux, or Mac terminal)

---

## How to Use This Section

1. Read through each topic sequentially
2. Practice the binary conversions and CIDR calculations
3. Use the tables as quick reference guides
4. Try the commands on your own machine (`ipconfig`, `ifconfig`)

---

## Related Topics

- **Prerequisite for**: OSI Model (Section 2)
- **Next Step**: [Section 2: The OSI Model](../02-OSI-Model/README.md)

---

## Key Takeaway

> IP addresses are like house numbers for devices. Subnets group these houses into neighborhoods for security. CIDR tells you how big the neighborhood is, and ports identify which specific door to knock on.

---

## File Structure

```
Networking-Fundamentals/
├── README.md                       # Course Overview
├── .gitignore
├── 01-IP-Subnet-CIDR-Ports/
│   ├── README.md                   # You are here
│   └── 01-IP-Subnet-CIDR-Ports.md  # Detailed content
└── 02-OSI-Model/
    ├── README.md                   # Section overview
    └── 02-OSI-Model.md             # Detailed content
```

---

[Start 01-IP-Subnet-CIDR-Ports →](./01-IP-Subnet-CIDR-Ports.md)
```
