# Task 8: Capture Network Traffic with Wireshark

## What I'm Doing
I'm using **Wireshark** to watch and record the actual data traveling over my own network — like putting a camera on the information highway. Then I filter it to look at specific types of traffic (web traffic, DNS lookups, etc.) and study how a connection is set up step by step.

## Why It Matters
This shows me, in real time, what data looks like when it's sent unprotected over a network — and why that's risky. It also teaches how HTTPS (the padlock in your browser) protects that same data.

## What I'll Produce
- A saved capture file (`wireshark_capture.pcap`)
- Screenshots of HTTP, DNS, and TCP filtered traffic
- An annotated TCP "handshake" (the 3-step greeting computers do before talking)
- An example of unencrypted data I could actually read
- A glossary of key terms, written in my own words

## Tools I'm Using
- Wireshark

## ⚠️ Safety Rule
I only capture traffic on networks I own. I never do this on public Wi-Fi, work networks, or anyone else's network.

## Status
- [ ] Install Wireshark
- [ ] Capture 2+ minutes of traffic
- [ ] Filter HTTP traffic
- [ ] Filter DNS traffic
- [ ] Filter + annotate TCP handshake
- [ ] Export .pcap file
- [ ] Find unencrypted data example
- [ ] Write glossary + explanation
