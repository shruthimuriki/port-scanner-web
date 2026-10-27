# Network Security Port Scanner

A lightweight, multi-threaded **Network Security Port Scanner** built to audit network environments by identifying active hosts and discovering open network entry points. This project satisfies all requirements for evaluating target reachability and identifying exposed services.

---

## 🛠️ Key Features

*   **Flexible Target Input:** Supports multiple target formats including single IPv4 addresses, domain names (FQDNs), and local loopbacks.
*   **Custom Port Range Selection:** Allows users to specify arbitrary port brackets (e.g., standard `1-1024` or individual custom ports) to optimize scanning speeds.
*   **Multi-Threaded Port Scanning:** Utilizes parallel sockets to execute network probes quickly without blocking operations.
*   **Accurate Port State Identification:** Determines whether a target port is explicitly **Open**, **Closed**, or unreachable.
*   **Structured Results Display:** Outputs neatly aligned tables detailing the Port ID, Protocol (TCP), and commonly associated network service headers.
*   **Robust Error Handling:** Safely catches invalid domain resolutions, dropped socket connections, missing arguments, and keyboard interrupts (`Ctrl+C`).

---

## 🚀 Getting Started

### Prerequisites
*   Python 3.8 or higher installed on your machine.
*   Standard library utilities (uses native `socket`, `sys`, and `threading` modules—no external dependencies required).

### Installation
Clone this repository to your local workspace:
```bash
git clone https://github.com
cd network-port-scanner
```

---

## 💻 Usage & Demonstration

Run the scanner directly via the command terminal:

```bash
python port_scanner.py
```

### 1. Target Input & Range Selection
Upon execution, the terminal prompts you to enter the scan parameters:
```text
[+] Enter Target IP Address or Domain (e.g., 192.168.1.1 or scanme.nmap.org): scanme.nmap.org
[+] Enter Starting Port (1-65535): 20
[+] Enter Ending Port (1-65535): 100
```

### 2. Clear Scan Results Layout
Once execution finishes, the application displays a clean overview of the scan duration and discovered states:

```text
============================================================
 Scanning Target: scanme.nmap.org (45.33.32.156)
 Time Started   : 2026-10-27 19:35:12
============================================================

PORT     STATE    SERVICE
-------------------------------------------
22/tcp   OPEN     SSH (Secure Shell)
53/tcp   CLOSED   Domain Name Server
80/tcp   OPEN     HTTP (Web Server)
99/tcp   CLOSED   Metagram

[+] Scan Completed successfully in 4.12 seconds.
```

---

## 🚨 Error Handling Matrix

The application handles standard network exceptions gracefully:

| Trigger Scenario | Code Action | User Output Example |
| :--- | :--- | :--- |
| **Invalid Domain Name** | Resolves `socket.gaierror` safely | `[-] Error: Hostname could not be resolved.` |
| **Unreachable Target IP** | Catches `socket.timeout` anomalies | `[-] Error: Target is offline or firewalled.` |
| **User Manual Exit** | Interrupts with `KeyboardInterrupt` | `\n[-] Scan cancelled by user. Exiting...` |
| **Invalid Numeric Port** | Implements value boundary verification | `[-] Error: Port ranges must sit between 1 and 65535.` |


---

## 🔒 Security Disclaimer
This software is intended **strictly for educational purposes** and authorized network security auditing. Do not launch port scans against target servers or infrastructure without explicit, written permission from the systems owner.
Run `pip install -r requirements.txt` then `python main.py -t scanme.nmap.org -p common`
