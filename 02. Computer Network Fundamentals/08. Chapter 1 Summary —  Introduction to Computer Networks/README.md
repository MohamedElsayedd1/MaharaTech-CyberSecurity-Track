# Introduction to Computer Networks

A one-page visual summary of **Chapter 1: Introduction to Computer Networks**, covering transmission media, network devices, network categories, and network topologies.

![Introduction to Computer Networks](./CH01-infographic.jpg)

*Copyrights: MAHARA-TECH Platform*

---

## 🧵 1. Transmission Media

Physical/wireless media used to carry data, divided into **Copper**, **Fiber Optic**, and **Wireless**.

**Copper Cables**
- **Coaxial** – Uses a **BNC connector**. Variants: 10BASE5, 10BASE2. Used for video transfer.
- **Shielded Twisted Pair (STP)** – Protected against electromagnetic interference, but harder to install.
- **Unshielded Twisted Pair (UTP)** – Uses **RJ45 connector**. Easy to install, less expensive, but susceptible to electromagnetic interference. Categories:
  | Category | Use / Speed |
  |---|---|
  | Category 1 | Voice only (telephone wire) |
  | Category 5 | Up to 100 Mbps |
  | Category 5e | Up to 1 Gbps |
  | Category 6 | 1–10 Gbps |

**Fiber Optic**
- Sends data as light pulses over a glass medium.
- Very expensive, hard to work with, but free of electromagnetic interference and supports extremely high data transfer rates.
- **Single mode** – Single light ray, ~9 micron core, extends great distances.
- **Multi-mode** – Multiple light rays, ~50 micron core, limited distance, used in submarine connections.

**Wireless**
- Less secure, but offers **mobility and flexibility**.
- Standard: **IEEE 802.11 (a, b, g, n, ...)**.
- Frequencies used: **2.4 GHz – 5 GHz**.
- Example: **Wi-Fi (LAN) = Wireless Fidelity**.

---

## 🔌 2. Devices (NIC – Switch – Router – Access Point)

Typical data path: **Internet → Router → Switch/Hub → NIC (Computers) → Computer peripherals**, with an **Access Point** providing a wireless branch off the switch.

- **Router** – Connects the local network to the internet/other networks; sits at the top of the transmission chain.
- **Hub** – Connects multiple devices but **allows collisions** (shared collision domain).
- **Switch** – Connects devices more intelligently, giving each port its own collision domain.
- **Access Point** – Provides wireless connectivity, using:
  - **SSID (Service Set Identifier)** to identify the wireless network.
  - **RJ45 connector** and **antenna** to bridge wired and wireless traffic.
  - **CSMA/CA** (Carrier Sense Multiple Access/Collision Avoidance), using an **RTS (Request to Send) / CTS (Clear to Send)** handshake to avoid collisions.
- **NIC (Network Interface Card)** – Connects computers and peripherals to the network.

---

## 🗂️ 3. Categories

Networks are classified along three dimensions: **Transmission mode**, **Geographical area**, and **Administration type**.

### Transmission Mode
- **Simplex** – Data flows in one direction only.
- **Half-Duplex** – Data flows both ways, but not simultaneously.
- **Full-Duplex** – Data flows both ways at the same time.

### Geographical Area
- **Wide Area Network (WAN)** – Large-scale network (e.g., the internet via ISPs). Low speed; under **ISP administrative control**.
- **Local Area Network (LAN)** – Small-scale network (e.g., home/office). High speed; under **user administrative control**.

### Administration Type
| | Client/Server Network | Peer-to-Peer Network |
|---|---|---|
| Server | Client machines connect to a central server | No central server |
| Storage | All files/folders on dedicated server storage | Each machine shares files equally |
| OS | Server OS (Windows Server 2012, 2016, ...) | Client OS (Windows 7, 10, ...) |
| Typical use | Large enterprises | Home / Small office |

---

## 🔷 4. Topologies

The physical/logical arrangement of devices in a network.

- **Point to Point** – Direct connection between exactly two devices.
- **Bus**
  - ✅ Easy to install, inexpensive (coaxial cable & BNC connectors)
  - ❌ Less secure (allows sniffing), collisions, slows down under high traffic
- **Ring**
  - ✅ Easy to install, inexpensive
  - ❌ Expansion affects operation; entire network fails if one machine fails; slows under high traffic
- **Star**
  - ✅ Unaffected if one machine fails; simple to expand
  - ❌ If the central device (e.g., switch) fails, the whole network fails
- **Mesh**
  - ✅ Secure (multiple redundant paths)
  - ❌ Expensive due to redundancy (many connections required)

---

## 📁 Repository Structure

```
.
├── README.md
└── CH01-infographic.jpg
```
