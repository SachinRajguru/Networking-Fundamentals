
## Section 2: The OSI Model

---

### Prerequisites

#### DNS Resolution

- **What is DNS?** A database mapping domains to IPs
  - Example: `google.com` → `8.8.8.8`
- **Process**: Browser checks local cache → ISP DNS → Resolves if valid
- **Why?** Ensures the domain exists before sending data

---

#### TCP Handshake

- A "hello" between devices to confirm readiness
- **Three-Way Handshake**:

```
Client                              Server
  │                                    │
  ├─────────── SYN (sync) ────────────→│  "Want to connect?"
  │                                    │
  ├←────────── SYN-ACK ───────────────┤  "Ready! Are you?"
  │                                    │
  ├─────────── ACK ──────────────────→│  "Yes, let's go!"
  │                                    │
  └──── Connection Established! ───────┘
```

- **Why?** Ensures the server accepts requests before sending data

---

### What is the OSI Model?

- OSI = **Open Systems Interconnection**
- A **7-layer model** explaining data's journey across networks
- Shows how requests/responses travel from your laptop to a server

---

#### Data Flow Visual
```
SENDING (Encapsulation):          RECEIVING (Decapsulation):
┌─────────────────────┐            ┌─────────────────────┐
│  L7 Application    │  DATA       │  L7 Application    │
│  (Browser)         │  ──────→    │  (Browser)         │
├─────────────────────┤   Segment   ├─────────────────────┤
│  L6 Presentation   │  ──────→    │  L6 Presentation   │
│  (Encryption)     │             │  (Decryption)      │
├─────────────────────┤   Session   ├─────────────────────┤
│  L5 Session        │  ──────→    │  L5 Session        │
│  (Cookie/Auth)     │             │  (Validation)      │
├─────────────────────┤   Packet    ├─────────────────────┤
│  L4 Transport      │  ──────→    │  L4 Transport      │
│  (TCP/UDP)         │             │  (Reassembly)      │
├─────────────────────┤   Frame     ├─────────────────────┤
│  L3 Network        │  ──────→    │  L3 Network        │
│  (IP Routing)      │             │  (IP Processing)   │
├─────────────────────┤   Signal    ├─────────────────────┤
│  L2 Data Link      │  ──────→    │  L2 Data Link      │
│  (MAC Addresses)   │             │  (Frame Handling)  │
├─────────────────────┤            ├─────────────────────┤
│  L1 Physical       │  ──────→    │  L1 Physical       │
│  (Cables/WiFi)     │             │  (Signals)         │
└─────────────────────┘            └─────────────────────┘
```

---

#### OSI vs TCP/IP Model

| OSI Model          | TCP/IP Model      |
|--------------------|-------------------|
| 7 Layers           | 4 Layers          |
| Detailed/Standard  | Simplified        |
| Layers 7-5        | Combined as "Application" |

---

### Detailed OSI Layers

---

#### Layer 7: Application Layer

- **What Happens**: Browser initiates request (HTTP/HTTPS)
- **Handled By**: Your browser (e.g., Chrome)
- **Example**: You type `google.com` → Browser sends HTTP request

---

#### Layer 6: Presentation Layer

- **What Happens**: Data encryption/formatting
- **Handled By**: Browser
- **Why?** Protects data during travel
- **Example**: HTTPS encrypts your request so hackers can't read it

---

#### Layer 5: Session Layer

- **What Happens**: Creates and maintains a session
- **Handled By**: **Browser manages the session** (cookies, tokens) + **OS handles session layer protocol**
- **Why?** Allows persistent connections without re-authenticating
- **Example**: You stay logged into Facebook without re-authenticating because browser stores session cookies

> **Note**: In practice, modern browsers handle session management at the application level, but the OS maintains the actual session state at this layer.

---

#### Layer 4: Transport Layer

- **What Happens**: Segments data into parts + chooses protocol
- **Handled By**: OS/Browser
- **Protocols**:
  - TCP (reliable) - e.g., HTTP
  - UDP (fast) - e.g., DNS
- **Example**: Splits 10GB upload into segments for efficient sending

---

#### Layer 3: Network Layer

- **What Happens**: Adds source/destination IPs → Creates **packets**
- **Handled By**: Router
- **Role**: Router decides the shortest path
- **Analogy**: Traveling from Delhi to Mumbai—add source/destination, choose shortest path

---

#### Layer 2: Data Link Layer

- **What Happens**: Converts packets to **frames** + adds MAC addresses
- **Handled By**: Switches
- **Why?** Switches use frames to route within networks

---

#### Layer 1: Physical Layer

- **What Happens**: Converts frames to **electronic signals**
- **Handled By**: Cables/optical fibers
- **Example**: Data travels as signals through internet cables

---

### Full Data Journey Example

#### Sending Data (Your Laptop → Google Server)

```
Browser (L7) → Encrypts (L6) → Creates session (L5) → Segments (L4)
→ Adds IPs (L3) → Frames (L2) → Signals (L1)
→ Travels via routers/switches/cables
→ Reaches Google server
```

#### Receiving Data (Google Server → Your Laptop)

```
Signals (L1) → Frames (L2) → Packets (L3) → Segments (L4)
→ Validates session (L5) → Decrypts (L6) → Processes request (L7)
→ Sends HTML response back (reverse journey)
```

---

### Why OSI Matters for DevOps/Engineers

- **Good to Have**: High-level understanding suffices
- **Deep Dives**: For core networking roles only
- **Relevance**: Explains data flow, troubleshooting, and tools like Wireshark

---

### Key Takeaway

> OSI shows data transformation through 7 layers. TCP/IP is similar but simpler (combines top layers).

---

## Conclusion and Tips

### Overall Workflow

```
DNS Resolution → TCP Handshake → OSI Layers (Send/Receive Data)
```

### Practice Exercises

1. Convert IP `172.16.3.1` to binary
2. Calculate IPs for CIDR examples above
3. Use online CIDR calculators for practice

### Resources

- Search: "CIDR calculator"
- Search: "TCP handshake"
- Search: "OSI model diagram"

### Final Tip

> Networking is automated today, but this knowledge builds intuition. Review the material for deeper understanding. Good luck!
