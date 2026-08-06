# Chapter 3 Summary — Firewalls and Honeypots

Part of the **MaharTech – Network Security** course.

## Overview

This chapter summarizes how firewalls work, how attackers try to detect and bypass them, and the different filtering technologies firewalls rely on.

![Chapter 3 Infographic — Firewall Types, Attack Detection, Filtering Technologies, Bypassing Firewalls](CH03-infographic.jpg)

## A. Firewall Types

- **Host-based Firewall** — runs directly on an individual device (like a laptop), filtering traffic to and from that specific host.
- **Network-based Firewall** — a dedicated appliance placed at the network boundary, filtering traffic for all devices behind it (e.g., protecting a web server from Internet traffic).

## B. Firewall Attacks Detection

Attackers probing a firewall from the Internet typically get one of a few responses:

- **Early Negation** — the connection is rejected quickly and cleanly, often at the network edge (least useful info leaked to the attacker).
- **Negation** — the connection is denied, but with less clear timing/behavior.
- **Late Negation** — the request travels further into the network before being denied, potentially revealing more about the internal architecture.

The timing and behavior of these responses can leak information — attackers use it to map how far into the network their traffic gets before being blocked, helping them infer firewall rules and network layout.

## C. Firewall Filtering Technologies

### 1. Packet Filtering
- Filters traffic using a statically configured **Access Control List (ACL)** that permits or denies traffic based on: Source IP, Source Port, Destination IP, Destination Port, and Protocol.
- Effective at Layer 3 (IP) and Layer 4 (port) filtering.
- **Limitations:** stateless (examines each packet individually, not in context of a connection), can't track dynamically negotiated sessions or changing ports, complex ACLs are hard to maintain, and easier to exploit.

### 2. Stateful Inspection
- Maintains a **state table** tracking every active, permitted connection (source/destination IP and port, protocol, flags, sequence/ack numbers).
- Inspects each packet against the state table to confirm it belongs to a legitimate, tracked session — not just matching static rules.
- **Limitation:** still cannot prevent application-layer attacks, since it doesn't inspect the actual application data.

### 3. Proxy
- A proxy server acts as a **gateway/intermediary** between clients and servers — the client talks to the proxy, and the proxy talks to the server on the client's behalf.
- There is **no direct connection** between client and server.
- Inspects traffic at the **application level**, which allows deeper analysis than packet filtering or stateful inspection.
- **Limitation:** deeper inspection takes more processing time, which can slow down real-time traffic.

## D. Bypassing Firewalls

Attackers (or even regular users) can bypass firewall restrictions in several ways:

- **Peer-to-peer software** (e.g., torrent clients) — can fool firewalls by dynamically changing port numbers, making traffic harder to block with static rules.
- **USB Modems** — introduce risk when a device connects directly to an ISP, bypassing the network's firewall entirely. Any system connected through an external ISP link is not protected by the organization's firewall, giving attackers a window of opportunity while that modem connection is active.

## Key Takeaways

| Concept | Main Point |
|---|---|
| Firewall Types | Host-based protects one device; network-based protects everything behind it |
| Attack Detection | How/when a firewall rejects a probe can leak info about network structure |
| Packet Filtering | Fast but stateless and easy to exploit |
| Stateful Inspection | Tracks real sessions, but blind to application-layer attacks |
| Proxy | Deepest inspection (application layer), but slower |
| Bypassing | P2P tools and USB modems can create paths around firewall protection |

---
**Course:** MaharTech – Network Security
**Topic:** Chapter 3 Summary — Firewalls and Honeypots
