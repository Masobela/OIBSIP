# Task 3: SQL Injection on DVWA (Low Security)

## What I'm Doing
I'm practicing a well-known hacking technique called **SQL Injection** on a website that was built on purpose to be hackable — DVWA (Damn Vulnerable Web Application). I only run this on my own computer, never on a real website.

SQL Injection means typing special text into a login box (like `' OR '1'='1`) that tricks the website's database into giving up information it shouldn't — sometimes even logging you in without a real password.

## Why It Matters
This is one of the oldest and most common website weaknesses. Understanding how it works helps me understand how to prevent it when I build or review real applications.

## What I'll Produce
- A log of each payload (trick text) I tried and what happened (`sql_injection_notes.md`)
- Screenshots of each attempt
- A plain-language explanation of what SQL Injection is and how to fix it (using "prepared statements")

## Tools I'm Using
- DVWA (running only on my own local server)
- A web browser

## ⚠️ Safety Rule
This is only done on DVWA running on my own machine. I never try this on a real website — that would be illegal.

## Status
- [ ] Set up DVWA locally
- [ ] Set security level to Low
- [ ] Try first payload
- [ ] Try a second payload
- [ ] Screenshot each attempt
- [ ] Write notes file
- [ ] README written
