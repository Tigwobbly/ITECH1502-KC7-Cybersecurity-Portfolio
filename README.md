# ITECH1502-KC7-Cybersecurity-Portfolio
This is for the final assignment of ITECH1502

# KC7 Phishing and Account Compromise Investigation

**ITECH1502 Cybersecurity Fundamentals**  
**Student:** Connor Reid  
**Student ID:** 30347026  

## Project Overview

This portfolio documents my completion of the KC7 Cyber challenge **A Rap Beef: An Intro to Security Investigations**. The challenge placed me in the role of a security analyst investigating suspicious activity affecting the fictional organisation OWL Records.

Using Kusto Query Language (KQL), I examined network, DNS, email, employee and authentication records to reconstruct an attack against an employee named Dwake. The investigation followed the attacker from initial reconnaissance through phishing, account compromise and a later file download.

## Project Objectives

The objectives of this investigation were to:

- Use KQL to identify suspicious events and remove irrelevant results.
- Correlate evidence across multiple security datasets.
- Reconstruct a defensible timeline of the attack.
- Explain how publicly available information and phishing defeated account protections.
- Recommend controls that could prevent or reduce similar incidents.

## Tools and Datasets

The investigation was completed in the KC7 Cyber training environment.

The main datasets examined were:

- `InboundNetworkEvents`
- `OutboundNetworkEvents`
- `PassiveDns`
- `Email`
- `Employees`
- `AuthenticationEvents`

Important indicators included:

- Attacker IP address: `18.66.52.227`
- Suspicious domain: `betterlyrics4u.com`
- Targeted username: `dwaudrey`
- Targeted workstation: `10.10.0.5`

## Investigation Method

The investigation used an incremental threat-hunting process. Each confirmed result became the starting point for the next query.

1. Examined website activity associated with the supplied IP address.
2. Identified a password-recovery attempt using information disclosed in Dwake's lyrics.
3. Used Passive DNS to associate the IP address with `betterlyrics4u.com`.
4. Searched email records for
