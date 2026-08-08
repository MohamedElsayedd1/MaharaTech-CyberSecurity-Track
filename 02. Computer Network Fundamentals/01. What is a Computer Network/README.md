# Chapter 1 Summary — Computer Network Fundamentals

Part of the **MaharTech – Computer Network Fundamentals** course.

## Overview

This chapter ties together three foundational building blocks of any computer network — **the core network model**, **connecting devices**, and **transmission media** — into a single picture of how data actually moves from an end device out to the Internet.

![Network overview](network-overview.png)

## 1. The Core Network Model

Every network is built from the same basic pieces working together:

- **Computer** — the end-user machine (desktop or laptop) that sends and receives data.
- **Computer peripherals** — devices such as printers that reach the network through a connected computer.
- **Connecting device** — a central device (e.g., a router) that links computers and peripherals together and provides a path out to the wider network.
- **Transmission media** — the physical or wireless pathways that carry data between devices.
- **Internet** — the wider network the connecting device provides access to.

Data generated on a computer or its peripherals travels over transmission media to a connecting device, which then routes it either to another local device or out to the Internet.

## 2. Connecting Devices

Connecting devices are the hardware responsible for linking computers, peripherals, and networks together:

- **Router** — sits at the top of the network and connects the local network to the Internet (WAN), routing traffic in and out.
- **Switch** — connects multiple **wired** devices (computers, printers, scanners, laptops) within the same local network.
- **Access Point** — provides **wireless** connectivity, letting devices join the network over Wi-Fi instead of a cable.

![Connecting devices](connecting-devices.png)

A typical network stacks these together: Router → Switch / Access Point → end devices, so both wired and wireless clients can reach the Internet through the same router.

## 3. Transmission Media

Transmission media is the physical or wireless path data actually travels along between devices:

- **Wired media** — physical cables (e.g., copper/Ethernet, fiber) connecting devices directly to a switch; used by desktops, laptops, printers, and scanners.
- **Wireless media** — radio signals used by an Access Point to connect devices without a cable; used by phones, tablets, and other Wi-Fi-enabled devices.

![Transmission media](transmission-media.png)

The choice between wired and wireless media comes down to a trade-off between **stability** (wired) and **mobility** (wireless).

## Putting It All Together

| Concept | Purpose |
|---|---|
| Core Network Model | Defines *what* pieces make up a network (computers, peripherals, connecting device, media, Internet) |
| Connecting Devices | Defines *how* devices are linked together (Router, Switch, Access Point) |
| Transmission Media | Defines *what carries* the signal between devices (wired vs. wireless) |

A working network applies all three together: the core model defines the pieces, connecting devices link them, and transmission media carries the actual signal between them — wired for stability, wireless for mobility.

---
**Source:** [Mahara-Tech.gov.eg](https://maharatech.gov.eg)
**Course:** MaharTech – Computer Network Fundamentals
**Topic:** Chapter 1 Summary
