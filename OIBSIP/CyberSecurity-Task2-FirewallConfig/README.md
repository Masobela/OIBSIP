# Task 2: Basic Firewall Configuration with UFW

## What I'm Doing
I'm setting up a **firewall** on a Linux computer using a tool called UFW (Uncomplicated Firewall). A firewall is like a security guard that decides which traffic is allowed in and out of a computer.

I'll turn the firewall on, then write rules like:
- "Let SSH traffic in" (a way to remotely control the computer safely)
- "Block HTTP traffic" (regular, unprotected web traffic)
- Plus a couple of my own extra rules

## Why It Matters
Without a firewall, any program on the internet can try to talk to your computer. A firewall only lets through the traffic you've approved, which blocks a lot of attacks before they even start.

## What I'll Produce
- A script (`ufw_configuration.sh`) that sets up all my rules automatically
- A screenshot of my active firewall rules (`ufw status verbose`)
- Proof that blocked traffic is actually being blocked
- A README explaining what each rule does and why I picked it

## Tools I'm Using
- UFW (the firewall tool)
- A Linux virtual machine (Ubuntu or Kali)

## Status
- [ ] Install UFW
- [ ] Enable UFW
- [ ] Allow SSH
- [ ] Deny HTTP
- [ ] Add 2 extra rules
- [ ] Screenshot of status
- [ ] Test blocked traffic
- [ ] Write the setup script
- [ ] README written
