# OIBSIP Cybersecurity Internship
## Task 4: Research Report on Common Network Threats

**Prepared by:** Neo Masobela  
**Track:** Cybersecurity  
**Task:** Common Network Threats  
**Purpose:** To identify common network threats, explain their potential impact, and recommend ways to reduce cybersecurity risks.

---

## 1. Introduction

A computer network connects devices so that they can communicate and share information. Organisations rely on networks to access applications, store data, communicate with customers, and perform daily operations.

However, networks can be targeted by cybercriminals seeking to steal information, disrupt services, or gain unauthorised access to systems.

This report examines six common network threats: malware, phishing, Distributed Denial-of-Service (DDoS) attacks, Man-in-the-Middle (MITM) attacks, spoofing, and packet sniffing. It also discusses their potential impact and the security measures organisations can use to reduce these risks.

## 2. Common Network Threats

### 2.1 Malware

**Definition:** Malware is malicious software designed to damage systems, steal information, spy on users, or provide attackers with unauthorised access.

**How it works:** An attacker may trick a user into downloading an infected attachment or installing a harmful application. Once executed, the malware may steal data, monitor activity, or spread to other systems.

**Potential impact:**
- Theft of sensitive information.
- Damage to files and computer systems.
- Unauthorised access to company networks.
- Business disruption and financial losses.

**Prevention measures:**
- Keep operating systems and applications updated.
- Use reputable anti-malware and endpoint protection tools.
- Avoid suspicious downloads and attachments.
- Maintain regular, protected backups.

### 2.2 Phishing

**Definition:** Phishing is a social engineering attack in which an attacker impersonates a trusted person or organisation to trick victims into revealing information or performing an unsafe action.

**How it works:** A victim may receive a fake bank email, SMS, or message containing a link to a fraudulent website. If the victim enters their login details, the attacker may use the stolen credentials to access their account.

**Potential impact:**
- Stolen usernames and passwords.
- Unauthorised access to accounts.
- Financial fraud.
- Malware infections and data breaches.

**Prevention measures:**
- Check unexpected messages and website addresses carefully.
- Avoid opening suspicious links or attachments.
- Use multi-factor authentication (MFA).
- Provide cybersecurity awareness training and report suspicious messages.

### 2.3 Distributed Denial-of-Service (DDoS) Attacks

**Definition:** A DDoS attack attempts to make a website, server, or network service unavailable by overwhelming it with traffic or requests from multiple sources.

**How it works:** An attacker may use many compromised devices to send large amounts of traffic to a target. The target may struggle to handle legitimate users alongside the malicious traffic.

**Potential impact:**
- Websites or services becoming unavailable.
- Disruption of business operations.
- Loss of customer trust.
- Financial losses caused by downtime.

**Prevention measures:**
- Use DDoS protection services.
- Apply traffic filtering and rate limiting.
- Monitor network traffic for unusual patterns.
- Develop an incident response plan for service disruptions.

### 2.4 Man-in-the-Middle (MITM) Attacks

**Definition:** A Man-in-the-Middle attack occurs when an attacker secretly intercepts or relays communication between two parties.

**How it works:** For example, an attacker may exploit an insecure network connection to observe communication between a user and an online service. Depending on the circumstances, the attacker may also attempt to alter the communication.

**Potential impact:**
- Exposure of sensitive information.
- Theft of login credentials.
- Manipulation of transmitted data.
- Loss of confidentiality and trust.

**Prevention measures:**
- Use HTTPS and other properly configured encrypted connections.
- Avoid connecting to untrusted Wi-Fi networks for sensitive activities.
- Verify website certificates and security warnings.
- Use secure VPN connections when appropriate.

### 2.5 Spoofing

**Definition:** Spoofing is when an attacker falsifies identifying information to make a communication, device, or source appear to be something it is not.

**How it works:** In IP spoofing, an attacker sends network packets with a forged source IP address. Other forms include email spoofing, where a message is made to appear as if it came from a trusted sender.

**Potential impact:**
- Deception of users or systems.
- Assistance in certain denial-of-service attacks.
- Attempts to bypass weak trust controls.
- Increased difficulty identifying the true source of malicious traffic.

**Prevention measures:**
- Configure network devices to filter invalid source addresses.
- Use authentication rather than trusting an IP address alone.
- Apply anti-spoofing controls at network boundaries.
- Verify unexpected requests through a separate trusted channel.

### 2.6 Packet Sniffing

**Definition:** Packet sniffing is the process of capturing and examining data travelling across a network.

**How it works:** Network administrators and cybersecurity analysts use tools such as Wireshark to troubleshoot connections and investigate suspicious activity. However, attackers may misuse packet-capturing tools to inspect unencrypted traffic and look for sensitive information.

**Potential impact:**
- Exposure of unencrypted data.
- Discovery of network devices and services.
- Possible theft of credentials sent through insecure protocols.
- Unauthorised monitoring of network communications.

**Prevention measures:**
- Encrypt network communications using secure protocols.
- Avoid insecure protocols that transmit sensitive data in plaintext.
- Protect Wi-Fi networks with appropriate security settings.
- Restrict physical and administrative access to network equipment.

## 3. General Impact of Network Threats

Network threats can affect both individuals and organisations. Their consequences may include:

- **Confidentiality loss:** Sensitive information is exposed to unauthorised people.
- **Integrity loss:** Information is changed without permission.
- **Availability loss:** Systems and services become inaccessible.
- **Financial damage:** Organisations may face recovery costs, fraud, or lost revenue.
- **Reputational damage:** Customers may lose confidence in an organisation.

The severity of an incident depends on the type of attack, the systems affected, and the effectiveness of existing security controls.

## 4. Recommended Network Security Practices

Organisations should use several layers of protection instead of relying on one security tool.

1. **Firewalls:** Control incoming and outgoing network traffic according to security rules.
2. **Regular patching:** Fix known software vulnerabilities by installing updates.
3. **Access control:** Give users only the permissions needed for their roles.
4. **Multi-factor authentication:** Add another verification step beyond a password.
5. **Encryption:** Protect information while it travels across networks.
6. **Network monitoring:** Review traffic and system logs for suspicious activity.
7. **Security awareness training:** Teach employees to recognise phishing and other social engineering attempts.
8. **Backups and incident response:** Maintain recoverable copies of important data and prepare for security incidents.

These measures reduce risk but cannot guarantee that every attack will be prevented.

## 5. Conclusion

Network threats can compromise information, interrupt services, and cause financial and reputational damage. Malware and phishing may target users and devices, while DDoS attacks can disrupt availability. MITM attacks, spoofing, and packet sniffing can threaten the security or trustworthiness of network communications.

Organisations can reduce these risks through secure configurations, encryption, firewalls, timely updates, access controls, monitoring, user education, and incident response planning.

Understanding these threats is an important step towards identifying security weaknesses and protecting network infrastructure.

## 6. References

1. National Institute of Standards and Technology (NIST), *Network Sniffing — Computer Security Resource Center Glossary*. https://csrc.nist.gov/glossary/term/Network_Sniffing

2. National Institute of Standards and Technology (NIST), *Spoofing — Computer Security Resource Center Glossary*. https://csrc.nist.gov/glossary/term/spoofing

3. Cybersecurity and Infrastructure Security Agency (CISA), *#StopRansomware Guide*. https://www.cisa.gov/stopransomware/ransomware-guide

4. NIST, *Technical Guide to Information Security Testing and Assessment (SP 800-115)*. https://csrc.nist.gov/pubs/sp/800/115/final
