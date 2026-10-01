# Task 7: Vulnerability Scanning with Nikto

## What I'm Doing
I'm using a tool called **Nikto** to automatically scan a test website (DVWA, running on my own machine) for security weaknesses. Nikto checks for things like outdated software, risky default files, and known weaknesses — all by itself.

## Why It Matters
Doing this by hand would take forever. Tools like Nikto do a fast first pass to flag anything suspicious, so a security analyst knows where to look closer.

## What I'll Produce
- `nikto_scan_results.txt` — the saved scan output
- A list of every finding, sorted by how serious it is (High/Medium/Low/Info)
- An explanation of what each finding means and how to fix it
- Screenshots of Nikto running

## Tools I'm Using
- Nikto (the scanning tool)
- DVWA running locally as the target

## Status
- [ ] Install Nikto
- [ ] Run basic scan
- [ ] Save output to file
- [ ] List and explain findings
- [ ] Sort findings by severity
- [ ] Run SSL check scan
- [ ] Screenshots added
- [ ] README explains Nikto vs Nmap
