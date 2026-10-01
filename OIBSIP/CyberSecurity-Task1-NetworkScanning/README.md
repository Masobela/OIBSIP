# Task 1: Basic Network Scanning with Nmap

## What I'm Doing
I'm using a tool called **Nmap** to scan a computer on my own network and find out:
- Which "doors" (ports) are open on it
- What programs (services) are running behind those doors
- What operating system it's using

Think of it like knocking on every door of a house to see which ones are unlocked, and figuring out who lives behind each one.

## Why It Matters
Every open port is a possible way into a computer. Security people scan networks to find these open doors BEFORE a hacker does, so they can close the ones that don't need to be open.

## What I'll Produce
- A text file (`nmap_scan_results.txt`) with my scan results
- Screenshots of my terminal while scanning
- Notes on each open port: what it does and whether it's risky
- A README explaining what Nmap is and the rules for using it safely

## Tools I'm Using
- Nmap (the scanning tool)
- A virtual machine (a "practice computer" inside my computer, so I'm not scanning anyone else's real device)

## ⚠️ Safety Rule
I only scan machines that belong to me, inside my own test VM. I never scan computers or networks that aren't mine — that would be illegal.

## Status
- [ ] Install Nmap
- [ ] Basic scan
- [ ] Service version scan
- [ ] OS detection scan
- [ ] Document open ports & risks
- [ ] Screenshots added
- [ ] README written
