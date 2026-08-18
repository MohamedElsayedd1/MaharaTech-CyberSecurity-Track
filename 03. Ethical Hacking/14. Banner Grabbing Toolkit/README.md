# Banner Grabbing Toolkit

A hands-on walkthrough of **banner grabbing** — the reconnaissance technique used to identify the software, version, and OS running on a remote service by capturing the text ("banner") it returns on connection. This repo documents several methods (active and passive) using `netcat`, `telnet`, `nmap`, and `ID Serve`.

> ⚠️ **Disclaimer:** These techniques should only be used against systems you own or have explicit written permission to test. Unauthorized scanning may be illegal.

---

## What is Banner Grabbing?

Banner grabbing is the process of connecting to an open port on a target host and reading the response it sends back. Many services (SSH, HTTP, FTP, SMTP, etc.) announce their software name and version by default — information that's extremely useful during the reconnaissance phase of a penetration test, since known versions can be checked against public vulnerability databases.

There are two broad approaches:

- **Active banner grabbing** — directly connecting to a service and sending a request to trigger a banner (netcat, telnet).
- **Passive/automated banner grabbing** — using tools that do the connecting and parsing for you (nmap, ID Serve).

---

## 1. Netcat (`nc`) — SSH Banner Grab

Connecting directly to port 22 with netcat immediately reveals the SSH server software and version, without needing to authenticate.

```bash
nc -vv 192.168.22.185 22
```

![Netcat SSH banner grab](images/ssh-netcat.png)

**Result:** `SSH-2.0-OpenSSH_10.0p2 Debian-8` — the target is running OpenSSH 10.0p2 on Debian.

---

## 2. Netcat — HTTP Banner Grab

The same technique works against web servers. Since HTTP servers don't respond until they receive a valid request, an empty `GET` is enough to trigger an error response that still leaks the `Server` header.

```bash
nc -vv 192.168.22.62 80
GET
```

![Netcat HTTP banner grab](images/netcat-http-get.png)

**Result:** `Server: Microsoft-HTTPAPI/2.0` — reveals the host is running a Windows HTTP stack, not Apache/Nginx.

---

## 3. Telnet — Port Connectivity + Banner Grab

Before grabbing a banner, `Test-NetConnection` (PowerShell) confirms the port is open and reachable. `telnet` is then used to manually connect and read the response.

```powershell
Test-NetConnection 192.168.17.158 -Port 80
telnet 192.168.17.158 80
```

![PowerShell connectivity test + telnet](images/telnet-test-netconnection.png)

Sending a bare `GET` request over the telnet session returns the full HTTP response headers, confirming the web server software and OS:

![Telnet HTTP response](images/telnet-http-response.png)

**Result:** `Server: Apache/2.4.65 (Debian)` — target is running Apache on Debian Linux.

---

## 4. Nmap — Automated Service/Version Detection

Instead of grabbing banners one port at a time, `nmap -sV` scans all open ports on a host and automatically fingerprints the service and version running on each.

```bash
nmap -sV 192.168.22.62
```

![Nmap service version scan](images/nmap-service-scan.png)

**Result:** A full picture of the host's exposed services in one scan — including `Microsoft IIS httpd 10.0` on port 80, `Microsoft Windows RPC`, `netbios-ssn`, `ms-wbt-server (RDP)`, and even `National Instruments LabVIEW` on port 5580. This is far more efficient than manual grabbing when profiling an entire host.

---

## 5. ID Serve — GUI Banner Grabbing Tool

For a quick, no-command-line option (especially on Windows), **ID Serve** by Gibson Research Corp queries a target URL/IP and reports the identified server software.

![ID Serve GUI](images/idserve-gui.png)

**Result:** Querying `certifiedhacker.com` identifies the server as `nginx/1.29.8`.

---

## Summary Table

| Tool | Type | Target Example | Info Revealed |
|------|------|----------------|----------------|
| `netcat` | Manual/active | SSH (22), HTTP (80) | Raw service banner |
| `telnet` | Manual/active | HTTP (80) | Raw HTTP headers |
| `nmap -sV` | Automated | Full host scan | Service + version for every open port |
| ID Serve | Automated (GUI) | Web server URL/IP | Server software identification |

## Repo Structure

```
.
├── README.md
└── images/
    ├── ssh-netcat.png
    ├── netcat-http-get.png
    ├── telnet-test-netconnection.png
    ├── telnet-http-response.png
    ├── nmap-service-scan.png
    └── idserve-gui.png
```

## Key Takeaways

- Banners often leak more than intended — software name, version, and sometimes OS.
- Defensive teams should **suppress or obfuscate banners** (e.g., `ServerTokens Prod` in Apache) to reduce this attack surface.
- Automated tools (`nmap`, `ID Serve`) save time when profiling many services/hosts, while manual tools (`netcat`, `telnet`) give finer control for a single target.
