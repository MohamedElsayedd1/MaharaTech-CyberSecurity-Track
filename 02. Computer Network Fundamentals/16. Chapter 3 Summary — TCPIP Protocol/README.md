# TCP/IP Protocol

A comprehensive, layer-by-layer walkthrough of the **TCP/IP model** — from a client requesting a web page all the way down to how a router forwards the resulting packets — covering the **Application**, **Transport**, **Internet**, and **Network Access** layers.

![TCP/IP Protocol](./CH03-infographic-01.jpg)

---

## 🖥️ Application Layer

A **client** initiates communication using various application protocols, each identified by a well-known port:

| Protocol | Port | Purpose |
|---|---|---|
| HTTP | 80 | Unencrypted web page delivery |
| HTTPS | 443 | Encrypted web page delivery |
| FTP | 21 | File transfer |
| SMTP | 25 | Sending outgoing email |
| POP3 | 110 | Retrieving incoming email |
| DHCP | 546 | Dynamic IP address / network config assignment (IP address, subnet mask, gateway, DNS) |
| DNS | 53 | Domain name resolution |

**DNS resolution example:** When a client requests `www.iti.gov.eg`, the request is resolved hierarchically through DNS servers responsible for `.eg` and `.gov`, ultimately returning an IP address (e.g., `41.33.119.73`) that the client can connect to.

---

## 🚚 Transport Layer

Application data is handed to either **TCP** or **UDP**, each wrapping data into **segments** using its own header format:

### TCP Protocol — Connection-oriented, Reliable Communication
Used by HTTP, HTTPS, FTP, SMTP, POP3, and DHCP (ports 80, 443, 21, 25, 110, 546).

| Field | Size |
|---|---|
| Source port / Destination port | 16 bits each |
| Sequence number | 32 bits |
| Acknowledgment number | 32 bits |
| Header length, flags (URG/ACK/PSH/RST/SYN/FIN, etc.) | 4-bit header length + flags |
| Window size | 16 bits |
| Checksum / Urgent pointer | 16 bits each |
| Options | Variable |

### UDP Protocol — Connectionless-oriented, Best-Effort Communication
Used by protocols like DNS (port 53) and others identified by dynamic port numbers.

| Field | Size |
|---|---|
| Source port / Destination port | 16 bits each |
| UDP length | 16 bits |
| UDP checksum | 16 bits |

---

## 🌐 Internet Layer

The **IP protocol** takes segments from the transport layer and wraps them into **packets**, adding IP addressing information.

- **IPv4 address structure:** 4 bytes (1 byte each), each ranging from **0–255**.
- Each packet includes:
  - **IP destination address**
  - **IP source address**

### IPv4 Address Classes (Network vs. Host, Public vs. Private)

| Class | Type | Range | Network / Host Split |
|---|---|---|---|
| **A** | Public | 1.0.0.0 – 9.255.255.255 | 1 byte network / 3 bytes host |
| | Private | 10.0.0.0 – 10.255.255.255 | |
| | Public | 11.0.0.0 – 126.255.255.255 | |
| **B** | Public | 128.0.0.0 – 172.15.255.255 | 2 bytes network / 2 bytes host |
| | Private | 172.16.0.0 – 172.31.255.255 | |
| | Public | 172.32.0.0 – 191.255.255.255 | |
| **C** | Public | 192.0.0.0 – 192.167.255.255 | 3 bytes network / 1 byte host |
| | Private | 192.168.0.0 – 192.168.255.255 | |
| | Public | 192.169.0.0 – 223.255.255.255 | |

- **Private IP ranges** are reserved for internal use only and are not routable on the public internet.
- **Public IP ranges** can be reached directly over the internet.

### Routing Table

Once a packet reaches a **router**, the router consults its **routing table** to determine where to forward the packet next. Routing tables can be built:

- **Statically** – manually configured by a network administrator.
- **Dynamically** – automatically learned/updated between routers.

---

## 🔌 Network Access Layer

The lowest layer in the TCP/IP model — handles physical transmission of the resulting frames onto the network medium (wired or wireless), completing the journey from application data down to the physical network.

---

## 📁 Repository Structure

```
.
├── README.md
└── CH03-infographic-01.jpg
```
