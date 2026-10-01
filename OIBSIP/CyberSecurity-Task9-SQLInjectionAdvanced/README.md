# Task 9: Exploit a SQL Injection Vulnerability (Advanced)

## What I'm Doing
This is the "level up" version of Task 3. Instead of just logging in with a trick, I'm trying to:
- Pull out the names of hidden database tables
- Pull out column names from those tables
- Compare doing this by hand vs. using an automatic tool called **sqlmap**

I'm also using **Burp Suite** to watch the actual web request being sent, like looking under the hood of a car while it's running.

## Why It Matters
This shows the full danger of SQL Injection — it's not just "logging in without a password," it can mean an attacker reading an entire database. It also teaches the real fix: parameterised queries (a way of writing database code so this trick can't work).

## What I'll Produce
- A log of every payload and what it revealed
- A comparison of my manual results vs sqlmap's results
- A screenshot of the intercepted request in Burp Suite
- `sql_injection_exploit.sh` — my steps written as a commented script
- A fix guide for developers, with code examples in Python and PHP
- A plain-English summary for a non-technical manager

## Tools I'm Using
- DVWA (Medium security, local only)
- sqlmap (optional, local only)
- Burp Suite (optional)

## ⚠️ Safety Rule
Only used on my own local DVWA setup. Never on real systems without written permission.

## Status
- [ ] Set DVWA to Medium security
- [ ] Craft manual payloads
- [ ] Document payloads & output
- [ ] Try sqlmap (bonus)
- [ ] Capture request in Burp Suite
- [ ] Write exploit script
- [ ] Write remediation section with code examples
- [ ] Write manager-friendly summary
