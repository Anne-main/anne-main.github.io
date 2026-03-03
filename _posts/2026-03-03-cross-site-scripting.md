---
title: cross-site scripting
categories: Cybersecurity Labs
tags: [xss]
layout: post
---

#Cross-Site Scripting (XSS) — PortSwigger Lab

Platform: PortSwigger Web Security Academy
Vulnerability Types Studied: Reflected XSS & Stored XSS

#Lab Overview

Using the PortSwigger Web Security Academy lab, I identified a Reflected XSS vulnerability in a search feature where user input was returned to the page without proper sanitization or encoding.

By injecting:

<script>alert('XSS')</script>

I confirmed arbitrary JavaScript execution in the browser.

#Methodology

1️⃣ Input Field Testing

Tested search parameters with basic HTML and script payloads.

Observed how the application handled user input in responses.

Identified lack of output encoding.

2️⃣ Payload Injection

Injected JavaScript into the search field.

Verified execution through browser alert.

3️⃣ Impact Evaluation

Analyzed how the vulnerability could escalate beyond proof-of-concept alerts.

Common Injection Points Used by Attackers
🔎 Search Boxes (Reflected XSS)

Attackers:

Inject malicious payloads into URL parameters or search fields.

Send crafted links to victims.

When the victim clicks, the payload executes in their browser.

This requires social engineering because the victim must click the malicious link.

💬 Comment Sections (Stored XSS)

Attackers:

Submit malicious JavaScript into comment forms, feedback forms, or profile fields.

The payload is stored in the database.

Every user who views the page executes the malicious script automatically.

This is more dangerous because:

No user interaction is required.

The attacker does not need to send a malicious link.

It scales to multiple victims.

#Exploitation Scenario: Cookie Theft & Session Hijacking

Once JavaScript execution is achieved:

1️⃣ Cookie Theft

If session cookies are accessible:

document.cookie

An attacker can send the session cookie to an external server they control.

If the victim is logged in:

The session token is active.

The attacker can reuse the stolen cookie.

This allows account impersonation without knowing the password.

This is especially dangerous while the victim is still active.

#HttpOnly Protection

The HttpOnly cookie flag:

Prevents JavaScript from accessing document.cookie.

Helps mitigate cookie theft via XSS.

However:

It does not stop the XSS vulnerability itself.

Attackers may still perform authenticated actions through the victim’s browser.

Why Stored XSS is More Dangerous

Stored XSS is more severe because:

The malicious payload is permanently stored.

Every visitor becomes a potential victim.

No social engineering is required.

The attacker can gain repeated access opportunities.

Key Takeaways

XSS is not just an alert popup — it can lead to session hijacking.

Search fields and comment sections are common attack surfaces.

HttpOnly protects cookies but does not eliminate XSS risk.

Stored XSS presents higher impact and scalability.

Proper input validation, output encoding, and CSP are critical defen
