# Task 1 — Basic Network Scanning with Nmap

## 1. Objective

The objective of this project was to perform a basic network security assessment using Nmap against an intentionally vulnerable Linux virtual machine in an isolated lab environment.

The assessment focused on identifying:

- Open TCP ports
- Running network services
- Service and software versions
- Operating system information
- Potential security risks associated with exposed services

---

## 2. Lab Environment

### Security Testing Machine
- Operating System: Kali Linux
- Tool: Nmap

### Target Machine
- Operating System: Linux
- Purpose: Intentionally vulnerable laboratory target
- Target IP Address: 192.168.56.101

### Network
- VirtualBox isolated/internal network
- Network distance: 1 hop

---

## 3. Methodology

The assessment was performed using the following steps:

1. Identified the target machine's IP address.
2. Tested connectivity between Kali Linux and the target.
3. Performed a basic Nmap TCP port scan.
4. Used Nmap service/version detection with `-sV`.
5. Used Nmap operating system detection with `-O`.
6. Combined service/version and OS detection.
7. Saved the scan results to `nmap_scan.txt`.
8. Reviewed the exposed services and identified areas requiring security attention.
9. Documented recommended security controls.

---

## 4. Nmap Commands Used

### Basic Network Scan

```bash
nmap 192.168.56.101
nmap -sV 192.168.56.101
sudo nmap -O 192.168.56.101
sudo nmap -sV -O 192.168.56.101
sudo nmap -sV -O 192.168.56.101 -oN nmap_scan.txt

