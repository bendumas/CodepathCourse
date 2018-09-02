# Project 8 - Pentesting Live Targets

Time spent: **5** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: SQL Injection (SQLi - Exploit3.gif)

![Alt text](Exploit3.gif?raw=true "SQLi Proof")

Vulnerability #2: Session Hijacking/Fixation (Exploit6.gif)

![Alt text](Exploit6.gif?raw=true "Session Hijacking Proof")


## Green

Vulnerability #1: Username Enumeration (Exploit1.gif)

![Alt text](Exploit1.gif?raw=true "Username Enumeration Proof")

Vulnerability #2: Cross-Site Scripting (Exploit4.gif)

![Alt text](Exploit4.gif?raw=true "XSS Exploit")


## Red

Vulnerability #1: Insecure Direct Object Reference (Exploit2.gif)

![Alt text](Exploit2.gif?raw=true "IDOR Proof")

Vulnerability #2: Cross-Site Request Forgery (Exploit5.gif)

![Alt text](Exploit5.gif?raw=true "CSRF Proof")


## Notes

I ran into challenges searching for the SQLi vulnerability. I had previously done SQLi with login fields, and this was my first time working with vulnerable GET parameters where the query is blind.
