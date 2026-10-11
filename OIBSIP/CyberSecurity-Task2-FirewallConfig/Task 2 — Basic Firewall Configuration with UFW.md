# Task 2 — Basic Firewall Configuration with UFW: Findings

**Intern:** Neo Masobela  |  **Track:** Cyber Security  |  **Internship:** Oasis Infobyte (OIBSIP)
**Environment:** Isolated local virtual lab (no external systems involved)

---

## 1. Summary

UFW (Uncomplicated Firewall) was set up on Kali Linux with a **deny-by-default** policy for incoming traffic. Four rules were added (SSH and HTTPS allowed, HTTP and FTP denied), the firewall was enabled, and the result was tested from a second machine (Metasploitable 2).

**Main result:** the firewall worked as configured. The allowed SSH connection succeeded, and the denied HTTP connection got no response.

---

## 2. Lab Environment

| Component | Details |
|---|---|
| Firewall system | Kali Linux — `192.168.56.102` |
| Test system | Metasploitable 2 — `192.168.56.101` |
| Firewall tool | UFW 0.36.2 |
| Network | Local isolated virtual network |

---

## 3. Key Findings

| # | Finding | Evidence in the recording |
|---|---|---|
| F1 | UFW 0.36.2 was installed and working | Install output and `ufw --version` → `ufw 0.36.2` |
| F2 | Default policies were set: incoming = **deny**, outgoing = **allow** | `ufw default deny incoming` and `ufw default allow outgoing` confirmed; final `ufw status verbose` shows `Default: deny (incoming), allow (outgoing)` |
| F3 | Four rules were added, and UFW also created the matching **IPv6** rules | `ufw status numbered` lists 8 rules (4 IPv4 + 4 IPv6) |
| F4 | The firewall was **inactive** until it was enabled | `ufw status numbered` → `Status: inactive`, then `ufw enable` → "Firewall is active and enabled on system startup" |
| F5 | The two VMs could talk to each other | `ping -c 4 192.168.56.101` → 4 sent, 4 received, **0% packet loss** |
| F6 | The **allowed** SSH port worked once the SSH service was running | `nc -zv 192.168.56.102 22` from Metasploitable 2 → `(ssh) open` |
| F7 | The **denied** HTTP port gave **no response** | `nc -zv 192.168.56.102 80` hung with no reply until it was interrupted |
| F8 | Final check matched the intended configuration | `ufw status verbose` → `Status: active`, logging on (low), all four rules present |

### Final rule set

| Port | Protocol | Action | Purpose |
|---|---|---|---|
| 22 | TCP | ALLOW IN | SSH |
| 80 | TCP | DENY IN | HTTP |
| 443 | TCP | ALLOW IN | HTTPS |
| 21 | TCP | DENY IN | FTP |

(The same four rules also exist for IPv6.)

---

## 4. Detailed Observations

### 4.1 Network preparation
- At first, Kali's `eth0` interface had **no IPv4 address**. Only `eth1` (`10.0.3.15`) had one.
- The address `192.168.56.102/24` was assigned to `eth0`, and the interface was brought up.
- The first attempt had a typing mistake (`eht0`), which gave `Cannot find device "eht0"`. The corrected command worked, and `ip -4 addr show eth0` then showed `192.168.56.102/24`.
- Metasploitable 2 showed `192.168.56.101` in its `ifconfig` output.

### 4.2 SSH test: two stages
1. **Before the SSH service was started**, the connection to port 22 was **refused**. This happened both when testing from Kali itself and from Metasploitable 2.
2. A typo (`sudo system start ssh`) gave `command not found`. The correct command, `sudo systemctl start ssh`, was then used.
3. `sudo ss -lntp | grep ':22'` showed `sshd` listening on `0.0.0.0:22` and `[::]:22`.
4. **After that**, the test from Metasploitable 2 returned `(ssh) open`.

**What this tells us:** a firewall rule that allows a port does not make a service available by itself. The service must also be running. The "refused" result came from no service listening, not from the firewall.

### 4.3 HTTP test
- From Metasploitable 2, the connection to port 80 received **no reply** and stayed stuck for roughly 45 seconds until it was interrupted.
- Nothing was listening on port 80 on Kali. With no firewall, a closed port normally answers right away with "Connection refused". The silent hang is therefore **consistent with** the firewall dropping the packets because of the `deny 80/tcp` rule.

---

## 5. Security Analysis

- **Deny-by-default is a good baseline.** Only traffic that is allowed on purpose gets through.
- **The explicit `deny` rules for ports 80 and 21 are partly redundant**, because the default incoming policy already blocks them. They are still useful for showing intent and for staying safe if a broader allow rule is added later.
- **SSH is open to anyone** (`22/tcp ALLOW IN Anywhere`). This is fine in a lab, but a real system should limit it to trusted IP addresses.
- **Port 443 is allowed**, but no HTTPS service was running in this test, so the rule is untested in practice.

---

## 6. Recommendations

1. Limit SSH to trusted IP addresses instead of "Anywhere".
2. Keep only the services that are really needed, and stop the SSH service when it is not in use.
3. Keep firewall logging on, and check the logs for suspicious activity.
4. Review the rule list regularly and remove rules that are no longer needed.
5. Keep the operating system and services patched.

---

## 7. Limitations

- **Not tested:** ports 443 and 21 (no service was listening on them), and the IPv6 rules.
- **HTTP block:** the test shows behaviour consistent with the deny rule. It was not compared against the same test with the rule removed.
- **Installation:** the recording starts after the install. The install output and the version check are visible, but the `apt update` and `apt install` commands themselves are not shown.
- **Lab only:** all results come from a small isolated lab and do not prove how the firewall behaves in a production network.

---

## 8. Conclusion

UFW was configured with a deny-by-default incoming policy and four explicit rules. Testing from a second machine confirmed that the allowed SSH traffic worked (once the service was running) and that the denied HTTP traffic got no response. The final status check confirmed the intended configuration. This shows how a simple firewall reduces a system's exposed attack surface.

---

## 9. Evidence

| File | Shows |
|---|---|
| `task2-screenshots/01_ufw_installation_and_version.png` | Install output and UFW version |
| `task2-screenshots/02_default_firewall_policies.png` | Default policies |
| `task2-screenshots/03_firewall_rules_configured.png` | The four rules |
| `task2-screenshots/04_ufw_enabled.png` | Firewall enabled |
| `task2-screenshots/05_ufw_status_numbered.png` | Rules table with IPv6 |
| `task2-screenshots/06_connectivity_ping_test.png` | Ping with 0% loss |
| `task2-screenshots/07_ssh_test_allowed.png` | SSH port open |
| `task2-screenshots/08_http_test_blocked.png` | HTTP test with no response |
| `task2-screenshots/09_final_ufw_status_verbose.png` | Final status |

*Demonstration video: `Neo_Masobela_Task2_UFW_Firewall_Demo.mp4` (full) and `Neo_Masobela_Task2_UFW_LinkedIn_2min.mp4` (2-minute cut).*

---

**Disclaimer:** All activity was performed in a controlled local virtual machine environment for educational and cybersecurity training purposes. No external or unauthorized systems were targeted.
