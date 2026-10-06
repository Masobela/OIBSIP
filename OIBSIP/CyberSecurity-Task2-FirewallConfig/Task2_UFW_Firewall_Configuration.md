# Task 2 — Basic Firewall Configuration with UFW

## Overview

This project demonstrates the configuration and testing of a basic Linux firewall using UFW (Uncomplicated Firewall).

The objective was to configure firewall policies, allow required services, block specific ports, and verify that the firewall was functioning correctly.

The practical work was performed in a controlled local virtual machine lab using Kali Linux and Metasploitable 2.

---

## Objectives

- Install and configure UFW.
- Set the default incoming traffic policy to deny.
- Set the default outgoing traffic policy to allow.
- Allow SSH traffic on port 22.
- Deny HTTP traffic on port 80.
- Add two additional firewall rules.
- Enable the firewall.
- Test allowed and blocked traffic.
- Verify the final firewall configuration.

---

## Lab Environment

| Component | Details |
|---|---|
| Firewall System | Kali Linux |
| Target/Test System | Metasploitable 2 |
| Firewall Tool | UFW |
| Kali Lab IP | 192.168.56.102 |
| Metasploitable 2 IP | 192.168.56.101 |
| Network | Local isolated virtual lab |

---

## Step 1 — Install UFW

UFW was initially not installed on the Kali Linux system.

The package was installed using:

```bash
sudo apt update
sudo apt install ufw -y
```

The installation was verified with:

```bash
ufw --version
```

The installed version was:

```text
ufw 0.36.2
```

---

## Step 2 — Configure Default Firewall Policies

The default incoming traffic policy was configured to deny incoming connections:

```bash
sudo ufw default deny incoming
```

The default outgoing traffic policy was configured to allow outgoing connections:

```bash
sudo ufw default allow outgoing
```

This creates a basic security posture where unsolicited incoming connections are blocked unless specifically allowed by a firewall rule.

---

## Step 3 — Configure Firewall Rules

### Allow SSH

SSH was allowed on TCP port 22:

```bash
sudo ufw allow 22/tcp
```

This allows SSH connections to the Kali system.

### Deny HTTP

HTTP traffic on TCP port 80 was explicitly denied:

```bash
sudo ufw deny 80/tcp
```

### Additional Rules

Two additional firewall rules were configured.

Allow HTTPS:

```bash
sudo ufw allow 443/tcp
```

Deny FTP:

```bash
sudo ufw deny 21/tcp
```

The final configured rules were:

| Port | Protocol | Action | Purpose |
|---|---|---|---|
| 22 | TCP | ALLOW | SSH |
| 80 | TCP | DENY | HTTP |
| 443 | TCP | ALLOW | HTTPS |
| 21 | TCP | DENY | FTP |

---

## Step 4 — Enable UFW

The firewall was enabled using:

```bash
sudo ufw enable
```

The system confirmed that the firewall was active and enabled on system startup.

This ensured that the firewall was active and would remain enabled after system startup.

---

## Step 5 — Verify Firewall Rules

The configured firewall rules were verified using:

```bash
sudo ufw status numbered
```

The output confirmed that the firewall was configured with the required allow and deny rules.

The corresponding IPv6 rules were also automatically configured.

---

## Step 6 — Test Firewall Behaviour

The Kali Linux and Metasploitable 2 virtual machines were configured on the same isolated local lab network.

The lab systems were:

```text
Kali Linux:       192.168.56.102
Metasploitable 2: 192.168.56.101
```

### Network Connectivity Test

Connectivity between the two virtual machines was verified using:

```bash
ping -c 4 192.168.56.101
```

The test was successful with zero percent packet loss.

### SSH Test

The SSH service was started on Kali Linux and verified to be listening on port 22.

From Metasploitable 2, the connection was tested using:

```bash
nc -zv 192.168.56.102 22
```

The connection to port 22 was successful, demonstrating that the SSH allow rule permitted the connection.

### HTTP Test

HTTP traffic was tested from Metasploitable 2 using:

```bash
nc -zv 192.168.56.102 80
```

The connection did not receive a response and was interrupted with Ctrl+C.

This behaviour was consistent with the configured deny rule for TCP port 80.

---

## Step 7 — Final Verification

The final firewall configuration was verified using:

```bash
sudo ufw status verbose
```

The output confirmed:

```text
Status: active
Default: deny (incoming), allow (outgoing)
```

The final configuration included:

```text
TCP port 22  — ALLOW
TCP port 80  — DENY
TCP port 443 — ALLOW
TCP port 21  — DENY
```

The firewall was also confirmed to be enabled on system startup.

---

## Security Considerations

A firewall helps reduce the attack surface of a system by controlling which network connections are permitted.

The configuration in this project follows a basic deny-by-default approach for incoming connections. Only services that are specifically required should be allowed.

Important security considerations include:

- Disable unnecessary network services.
- Avoid exposing administrative services unnecessarily.
- Use secure protocols such as SSH instead of Telnet.
- Restrict firewall rules to trusted IP addresses where possible.
- Review firewall rules regularly.
- Monitor firewall logs for suspicious activity.
- Keep operating systems and services patched.
- Only allow network ports that are required for legitimate services.

---

## Evidence

The practical demonstration was screen recorded during the configuration and testing process.

Supporting evidence includes screenshots showing:

- UFW installation
- UFW version
- Default firewall policies
- Firewall rule configuration
- UFW enabled
- SSH connectivity test
- HTTP blocking test
- Final UFW status
- Final firewall rules

A demonstration video was also recorded showing the configuration and testing process from start to finish.

---

## Conclusion

This task demonstrated the basic configuration and testing of a Linux firewall using UFW.

The firewall was successfully configured with a deny-by-default incoming policy and an allow-by-default outgoing policy. SSH traffic was permitted, HTTP and FTP traffic were denied, and HTTPS was explicitly allowed.

The firewall configuration was tested using a controlled local virtual machine environment consisting of Kali Linux and Metasploitable 2.

The final verification confirmed that UFW was active and configured with the intended firewall rules.

This practical exercise demonstrates how firewall rules can be used to reduce a system's exposed attack surface and control network access.

---

## Disclaimer

All firewall configuration, connectivity testing, and security testing activities were performed in a controlled local virtual machine environment for educational and cybersecurity training purposes.

No external or unauthorized systems were targeted.
