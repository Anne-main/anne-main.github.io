----
title: SQL Injection Lab
categories: cybersecurity-labs
tags: [sqli-lab, burpsuite, database]
layout: post
---
## Platform
PortSwigger Web Security Academy

## Tools Used
- Burp Suite (Community Edition)
- Browser Developer Tools

## Overview
This lab focused on identifying and exploiting SQL Injection vulnerabilities in web applications. The objective was to understand how improper input validation can allow attackers to manipulate backend database queries.

## Methodology

### 1. Confirming the Vulnerability
The first step was testing for SQL Injection using boolean-based payloads to determine whether user input was being interpreted directly within SQL queries.

By modifying parameters and observing changes in server responses, I confirmed the presence of an injection vulnerability.

### 2. Extracting Database Information
After confirming the vulnerability, I analyzed how SQL queries could be manipulated to retrieve additional data from the database.

Through controlled input manipulation, it was possible to extract structured data from database tables by leveraging string-based query behavior.

### 3. Enumerating User Credentials
The lab demonstrated how authentication mechanisms can be bypassed when user input is not properly sanitized.

By crafting structured payloads, it was possible to enumerate database content, including user-related data.

### 4. Password Extraction Techniques
In advanced scenarios, automated techniques such as Burp Suite Intruder can be used to systematically test and extract credential data.

Since I was using the Burp Suite Community Edition (which has limited automation features), I manually performed the extraction process by modifying payloads and analyzing server responses step-by-step.

This strengthened my understanding of:
- Query logic behavior
- Response-based inference
- Manual enumeration techniques

## Key Learnings
- Importance of parameterized queries and prepared statements  
- Risks of dynamic SQL query construction  
- How attackers confirm and escalate SQL Injection vulnerabilities  
- Practical defensive awareness from an attacker’s perspective  

## Security Reflection
This lab reinforced the importance of secure coding practices, proper input validation, and database protection mechanisms to prevent SQL Injection vulnerabilities.
