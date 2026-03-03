---
title: cross-site scripting
categories: Cybersecurity Labs
tags: [xss]
layout: post
---

# Cross-Site Scripting (XSS) — PortSwigger Lab

**Platform:** PortSwigger Web Security Academy  
**Vulnerability Types Studied:** Reflected XSS & Stored XSS

---

## Lab Overview

Using the PortSwigger Web Security Academy lab, I identified a **Reflected XSS vulnerability** in a search feature where user input was returned to the page without proper sanitization or encoding.

By injecting:

```html
<script>alert('XSS')</script>
