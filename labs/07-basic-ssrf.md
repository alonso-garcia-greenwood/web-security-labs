# Lab 7: Basic SSRF against the local server

**Platform:** PortSwigger Web Security Academy  
**Vulnerability class:** SSRF  
**Difficulty:** Apprentice  
**Status:** Completed  
**Date completed:** November 2, 2026  
**Tools used:** Burp Suite Repeater

## Objective
Access the local admin page using SSRF and delete the user Carlos.

## Steps
1. Opened the product stock request in Burp Repeater.
<img width="3837" height="2400" alt="image" src="https://github.com/user-attachments/assets/12d824ad-a464-48ae-a51a-ed127d279a1e" />

2. Found the `stockApi` parameter.

3. Changed the URL to `http://localhost/admin`.
<img width="1365" height="2130" alt="image" src="https://github.com/user-attachments/assets/4e382dd6-6c36-46de-bcc0-7cceee161891" />

4. Sent the request.
<img width="3837" height="2400" alt="image" src="https://github.com/user-attachments/assets/ca015a26-8452-457a-942d-08341fe20578" />

5. Got a 404 error.
6. Added the correct port, `8080`.
7. Found the admin page.
8. Used the delete URL for Carlos.
9. Sent the request and completed the lab.

## Why it works (root cause)
The server trusts user input.
It lets users choose where the server sends requests.

## Impact
An attacker can access local pages.
They may also perform admin actions.

## Remediation
- Block requests to localhost.
- Only allow trusted URLs.
- Check user input.

## What I learned
- SSRF can access local services.
- Different ports run different services.
- Burp Repeater lets us change requests.
- A 404 error can help us find mistakes.
