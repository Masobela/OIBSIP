# Task 5 — Research Report: Social Engineering Attacks

**Programme:** Oasis Infobyte (OIBSIP) — Cyber Security Internship  
**Author:** Neo Masobela  
**Date:** October 2026  
**Focus:** Phishing, pretexting, baiting, and organisational prevention

## 1. Introduction

Social engineering is the use of deception and psychological manipulation to persuade people to disclose information, grant access, transfer money, or perform actions that weaken security. Rather than directly defeating a firewall, an attacker may impersonate a trusted person and persuade an employee to help them. Social engineering can exploit authority, urgency, fear, curiosity, helpfulness, or the expectation of a reward.

This is an effective attack approach because people routinely respond to messages and requests as part of their work. Technical security controls remain important, but a convincing request can sometimes persuade a person to bypass normal procedures. The **2025 Verizon Data Breach Investigations Report** reported a human element in approximately **60% of breaches**. This figure covers human involvement broadly; it does **not** mean that 60% of breaches were exclusively social engineering attacks [1].

This report examines phishing, pretexting, and baiting, discusses documented incidents and research, and recommends practical controls for organisations.

## 2. Phishing

### 2.1 Definition and how it works

Phishing is a social engineering technique in which attackers send deceptive messages or direct victims to fraudulent sites to steal credentials, obtain sensitive data, or encourage malicious downloads. A typical phishing attempt impersonates a trusted organisation, creates a reason to act quickly, and asks the recipient to click a link, open an attachment, or disclose information.

**Example:** An employee receives a message claiming that their Microsoft 365 account will be suspended unless they immediately sign in through a provided link. The link may lead to a fake login page designed to capture credentials.

### 2.2 Common types

| Type | Description | Example |
|---|---|---|
| Spear phishing | A targeted message tailored to a specific individual or team. | A fake HR document sent to a named employee. |
| Whaling | Targeted phishing directed at senior executives or other high-value individuals. | An impersonated legal notice sent to a CEO. |
| Vishing | Voice-based phishing through telephone or internet calls. | A caller posing as the IT help desk asks for a login code. |
| Smishing | Phishing through SMS or other text messages. | A fake delivery text links to a fraudulent payment page. |

These distinctions are described in CISA's phishing guidance [2].

### 2.3 Documented case study: RSA SecurID breach (2011)

In 2011, attackers sent carefully targeted phishing emails to a small group of employees at RSA's parent company, EMC. The messages included a malicious Excel attachment presented as a recruitment plan. An employee opened the attachment, which exploited a software vulnerability and enabled the attackers to establish a foothold in the network. The broader intrusion led to theft of information relating to RSA's SecurID technology [3].

**Why it matters:** A single deceptive attachment helped initiate a much larger compromise. The case demonstrates that attackers do not need to target a senior administrator first; they may use an ordinary employee account as an entry point.

### 2.4 Four prevention recommendations

1. **Verify unusual requests independently.** Contact the supposed sender through a known phone number or official website rather than replying to the suspicious message.
2. **Use phishing-resistant multifactor authentication (MFA).** Security keys or passkeys can reduce the effectiveness of credential-phishing attacks; employees must still be trained not to approve unexpected authentication requests.
3. **Deploy email and web protections.** Use spam filtering, attachment scanning, domain protections, and browser safeguards, while recognising that no filter is perfect.
4. **Train and test employees.** Teach staff to recognise suspicious domains, unexpected attachments, urgent requests, and credential prompts; provide a simple way to report messages without punishment.

## 3. Pretexting

### 3.1 Definition and attack process

Pretexting occurs when an attacker invents a believable identity or situation (a **pretext**) to persuade someone to share information or perform an action. Unlike a generic phishing email, pretexting often involves an interactive story, such as claiming to be an IT technician fixing an urgent account problem.

A common sequence is:

1. The attacker researches the target organisation or employee.
2. They create a plausible story and impersonate a trusted role.
3. They establish credibility by mentioning real workplace details.
4. They ask the victim to reveal information, visit a site, or approve access.

### 3.2 Documented case study: Twitter account takeover (2020)

In July 2020, attackers phoned Twitter employees while pretending to be members of the company's IT help desk. They claimed to be assisting with VPN problems and directed employees to a lookalike login site. The attackers obtained credentials and persuaded some employees to approve MFA prompts. They subsequently accessed internal tools and took over high-profile accounts, which were used to promote a cryptocurrency scam. A New York State Department of Financial Services investigation documented the role of the false IT-support story in the attack [4].

**Why it matters:** The attackers combined an invented support scenario with real knowledge of remote-work VPN problems. This made the request seem credible and illustrates how help desk impersonation can defeat weak identity-verification procedures.

### 3.3 Three prevention measures

1. **Verify identity through a trusted channel.** For password resets, account changes, and access requests, use approved identity checks and a known help desk contact route.
2. **Require additional approval for sensitive actions.** Apply least privilege and require secondary approval for high-risk changes, especially those involving administrator accounts or MFA resets.
3. **Train staff to challenge authority and urgency claims.** Employees should be allowed to pause, confirm the request, and report suspicious callers even when the caller claims to be a manager or IT technician.

## 4. Baiting

### 4.1 Definition

Baiting uses something attractive or intriguing to tempt a person into taking a risky action. The attacker may exploit curiosity, the desire for free items, or a wish to help someone.

### 4.2 Physical and digital baiting

- **Physical baiting:** A USB drive labelled “Payroll” is left in a public place in the hope that someone will connect it to a work computer. An untrusted drive may contain malicious files or harmful hardware.
- **Digital baiting:** A website advertises a free premium application or exclusive document, but the download is malicious or asks the user to reveal credentials.

### 4.3 Documented research case: University of Illinois USB study (2016)

Researchers dropped **297 USB flash drives** around a university campus to study whether people would pick them up and connect them. The study found that people frequently connected found drives; a published summary reported that approximately **48%** of the drives were picked up, plugged in, and had files opened. This was a **controlled research experiment**, not evidence that the researchers infected participants' computers or that an actual breach occurred [5][6].

**Why it matters:** Curiosity and the desire to identify a lost drive's owner can lead people to interact with untrusted removable media.

### 4.4 Three prevention measures

1. **Never connect unknown USB devices to work computers.** Hand found devices to IT or security personnel according to company policy.
2. **Restrict removable media and downloads.** Use device-control policies, endpoint protection, approved software catalogues, and least-privilege permissions.
3. **Educate staff about attractive offers and lost-media traps.** Teach employees to obtain software only from approved sources and to report suspicious files or devices.

## 5. Bonus: Quid Pro Quo

Quid pro quo means **“something for something.”** In this attack, a scammer offers a benefit or service in exchange for information or an unsafe action. For example, a person posing as technical support might promise to repair a computer if the employee provides a password or installs a remote-access tool.

**Prevention:** Use official support channels, verify technicians' identities, never disclose passwords or MFA codes, and require authorisation before installing remote-access software.

## 6. Comparison of attack types

| Attack type | Primary target | Psychological lever exploited | Best countermeasure |
|---|---|---|---|
| Phishing | Email or message recipients | Fear, urgency, trust | Independently verify messages and use phishing-resistant MFA |
| Pretexting | Employees with information or access | Authority, credibility, helpfulness | Strong identity verification and approval procedures |
| Baiting | Curious users or employees | Curiosity, reward, helpfulness | Block untrusted media and use approved downloads |
| Quid pro quo | Employees seeking assistance | Reciprocity and promised benefits | Verify support requests and prohibit password sharing |

## 7. Organisational security awareness training: five-point checklist

- [ ] **Recognise common warning signs:** Train employees to identify suspicious links, unexpected attachments, false urgency, and impersonation.
- [ ] **Verify identity before acting:** Require staff to confirm unusual financial, access, password-reset, and MFA requests through approved channels.
- [ ] **Protect accounts:** Teach strong unique passwords, password-manager use, and phishing-resistant MFA where available.
- [ ] **Handle devices and downloads safely:** Prohibit unknown USB drives and unapproved software; explain how to report found devices.
- [ ] **Practise reporting and response:** Conduct realistic, authorised awareness exercises and make it easy to report suspicious messages, calls, and mistakes promptly.

**How to measure effectiveness:** Track training completion, employee reporting rates, time to report suspicious requests, and whether help desk staff consistently follow verification procedures. Use results to improve training rather than shame employees.

## 8. Recommendations for IT support and SOC teams

**IT support teams** should follow a documented identity-verification process before resetting passwords, unlocking accounts, changing MFA methods, or granting permissions. They should record support tickets and escalate unusual requests.

**SOC teams** should monitor suspicious sign-ins, repeated MFA prompts, unusual account changes, and reported phishing messages. They should correlate alerts with help desk activity and escalate potential compromises according to incident-response procedures.

Both teams should reinforce a simple rule: **a convincing story is not proof of identity**.

## 9. Conclusion

Social engineering shows that cybersecurity depends on both technology and human decision-making. Phishing uses deceptive messages, pretexting relies on invented identities or situations, and baiting tempts victims with objects or offers. The RSA and Twitter incidents demonstrate the serious consequences that can follow successful manipulation, while the USB study illustrates how ordinary curiosity can create security exposure.

Organisations can reduce risk by combining awareness training, identity verification, phishing-resistant MFA, least-privilege access, technical safeguards, and rapid reporting. For IT support and SOC analysts, recognising and responding to social engineering is an essential practical skill.

## 10. References

1. Verizon. (2025). *2025 Data Breach Investigations Report*. https://www.verizon.com/business/resources/reports/dbir/
2. Cybersecurity and Infrastructure Security Agency (CISA). (2024). *Phishing: Types of phishing, signs and protections*. https://www.cisa.gov/sites/default/files/2024-02/Update%20to%20Phishing%20General%20Security%20Postcard_01.01.2024.pdf
3. Zetter, K. (2011). *Researchers Uncover RSA Phishing Attack, Hiding in Plain Sight*. WIRED. https://www.wired.com/2011/08/how-rsa-got-hacked/
4. New York State Department of Financial Services. (2020). *Twitter Investigation Report*. https://www.dfs.ny.gov/reports-and-publications/other-reports/Twitter_Report
5. Tischer, M., et al. (2016). *Users Really Do Plug in USB Drives They Find*. IEEE Symposium on Security and Privacy. https://experts.illinois.edu/en/publications/users-really-do-plug-in-usb-drives-they-find/
6. University of Illinois Grainger College of Engineering. (2016). *IT security: strange flashdrives*. https://grainger.illinois.edu/news/media-mentions/25366
7. CISA. *Require Multifactor Authentication*. https://www.cisa.gov/audiences/small-and-medium-businesses/secure-your-business/require-multifactor-authentication
8. CISA. *Secure Our World: Recognize and Report Phishing*. https://www.cisa.gov/be-cyber-smart/report-incident

---

*Research and educational report. No live social engineering attacks or unauthorised tests were conducted as part of this assignment.*
