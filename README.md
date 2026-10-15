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
4. Searched email records for messages containing the suspicious domain.
5. Correlated email recipients with employee records to identify the targeted roles.
6. Confirmed that Dwake's workstation opened the phishing link.
7. Found a successful login to Dwake's account from the attacker IP.
8. Traced later account activity to the download of `DwakesDirtySecrets.zip`.

## Key Findings

- The attacker discovered the password-recovery answers **Washington** and **Fluffy** from Dwake's lyrics.
- Thirteen campaign emails contained links to `betterlyrics4u.com`.
- The campaign mainly targeted employees with rapper roles.
- Dwake received a phishing email that was classified as `CLEAN`.
- His workstation opened the phishing link at `12:03:12Z` on 15 April.
- A successful login from `18.66.52.227` occurred one hour later.
- Ten later account-related requests were identified.
- The final event downloaded `DwakesDirtySecrets.zip` from Dwake's Drafts folder with HTTP status `200`.
- The logs confirm the download but do not reveal the contents of the archive.

## Recommended Security Controls

OWL Records should:

- Replace knowledge-based recovery questions with identity verification through a trusted channel.
- Require phishing-resistant multifactor authentication.
- Inspect unfamiliar links even when an email passes initial filtering.
- Alert on suspicious external logins and unusual download activity.
- Revoke compromised sessions and reset affected credentials.
- Provide targeted phishing and personal-information awareness training.

These controls support the **Protect, Detect and Respond** functions of the NIST Cybersecurity Framework 2.0.

## What I Learned

This investigation improved my ability to use KQL, interpret structured security records and correlate evidence across different log sources. I learned that no single event normally explains an entire incident. A defensible conclusion requires timestamps, identities, IP addresses and domains to be compared across several datasets.

The activity also demonstrated how public information, weak recovery questions and convincing phishing can allow an attacker to compromise an account without using an advanced technical exploit.

## Portfolio Files

- [Final Project Report](ITECH1502_KC7_Report_Connor_Reid.pdf)
- [Project Presentation](ITECH1502_KC7_Presentation_Connor_Reid.pptx)

## Ethical and Legal Scope

This investigation was completed entirely within the authorised KC7 Cyber training environment. OWL Records, its employees and the investigated activity are part of a simulated cybersecurity scenario. No real systems or accounts were accessed.
