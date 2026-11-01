# Lab 4: File Path Traversal, Simple Case

**Platform:** PortSwigger Web Security Academy  
**Vulnerability class:** Path Traversal  
**Difficulty:** Apprentice  
**Status:** Not started  
**Date completed:** N/A  
**Tools used:** Burp Suite Community Edition, Web Browser

## Objective
Retrieve the contents of the `/etc/passwd` file by exploiting a path traversal vulnerability in the product image feature.

## Steps
1. Opened the lab website.
<img width="3783" height="1995" alt="image" src="https://github.com/user-attachments/assets/2ef306bb-ff1b-45c9-9c0f-814d3e095432" />

2. Intercepted the product image request using Burp Suite.
<img width="3765" height="2196" alt="image" src="https://github.com/user-attachments/assets/6c88b3f9-d400-439c-86e9-ce94240c4cbf" />

3. Sent the request to Burp Repeater.

4. Located the `filename` parameter in the HTTP request.
<img width="3756" height="2199" alt="image" src="https://github.com/user-attachments/assets/4ebc6d8b-2567-4f35-be8a-d2d854de8e39" />

5. Tested directory traversal using `../` sequences to access a file outside the image directory.
6. Attempted to retrieve `/etc/passwd`.

## Why it works (root cause)
The application does not properly validate user input in the filename parameter. This allows an attacker to use `../` to navigate outside the intended directory and access other files.

## Impact
An attacker could read sensitive files from the server, potentially exposing usernames, system information, and configuration data.

## Remediation
- Validate user input.
- Restrict file access to the intended directory.
- Avoid using user-provided file paths directly.
- Use safe file identifiers instead of accepting raw filenames.

## What I learned
I learned how path traversal works, how `../` moves between directories, and how Burp Suite Repeater can be used to modify HTTP requests and test web application vulnerabilities.
