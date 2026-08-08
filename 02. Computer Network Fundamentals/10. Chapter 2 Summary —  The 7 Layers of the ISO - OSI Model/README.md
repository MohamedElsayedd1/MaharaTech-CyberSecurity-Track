# The 7 Layers of the ISO / OSI Model

A one-page visual walkthrough of how data travels down the OSI stack when a device sends a request, and back up when it receives a reply — layer by layer, from **Application** down to **Physical**.

![The 7 Layers of the ISO/OSI Model](./CH02-infographic.jpg)

---

## 🖥️ Application Layer

- The starting point: the device **sends requests** and **receives replies**.
- Represents **end-to-end** communication between the user's application and the destination.

## 📄 Presentation Layer

- Handles **decryption** and **decompression** of incoming data (in reverse, **encryption** and **compression** on the way out).
- Ensures data is translated into a format the Application layer can use.

## 🔑 Session Layer

- Responsible for session **Establish → Manage → Control → Terminate**, shown as connection states: *Active*, *Reconnecting*, *Terminated*.
- Performs **reassembly** of data using **sequencing identifiers**, which avoid losses and duplication.

## 📦 Transport Layer

- Divides data into small fragments called **segments**, each carrying a **sequencing identifier**, through a process called **segmentation**.
- Two delivery styles:
  - **Connection-oriented** – reliable, acknowledged delivery.
  - **Connectionless-oriented** – "best effort" delivery, no guarantee.

## 🌐 Network Layer

- Converts segments into **packets** by adding **addressing information** (source address + destination address).
- Uses a **sender/receiver unique logical address** (i.e., IP address) to identify hosts across the network.

## 🔗 Data Link Layer

- Converts data into **frames**, split into two sub-layers:
  - **Logical Link Control (LLC)**
  - **Media Access Control (MAC)**
- Adds a **physical (MAC) address** to each frame — a **sender/receiver unique physical address**.
- Ensures **reliability** by checking frames for errors using a **Frame Check Sequence (FCS)**.
- Provides **flow control** to regulate the pace of data transmission.

## ⚡ Physical Layer

- The lowest layer: converts frames into raw bits and transmits them as actual signals over the physical medium.
- Signals travel over different media types — shown here as **wired** (electrical) and **wireless** (radio) connections — carrying the same bitstream (e.g., `1010 0001 0100`) to its destination.

---

## 📁 Repository Structure

```
.
└── README.md
└── CH02-infographic.jpg
```
