# Lab 8: Information disclosure in error messages

**Platform:** PortSwigger Web Security Academy  
**Vulnerability class:** Information disclosure  
**Difficulty:** Apprentice  
**Status:** Solved  
**Date completed:** November 2, 2026  
**Tools used:** Burp Suite Repeater, Web browser

## Objective

Find the framework version by causing an error and reading the error message.

## Steps

1. Opened the lab website.
   <img width="3813" height="2052" alt="image" src="https://github.com/user-attachments/assets/82aa6adf-61e8-4f1e-bd7e-760ee91dd066" />

3. Opened a product page.
   
5. Captured the product request in Burp Suite.
   <img width="3837" height="2193" alt="image" src="https://github.com/user-attachments/assets/5c18d6be-f681-4691-b0e3-0d5fcfae4eef" />

7. Sent the request to Repeater.
8. Changed `productId=1` to `productId=1'`.
9. Clicked Send.
    <img width="3837" height="2127" alt="image" src="https://github.com/user-attachments/assets/b9a1042a-4546-479a-8cef-ad0a6c239382" />

11. Received a `500 Internal Server Error`.
12. Read the error message and found Apache Struts version `2.3.31`.
13. Submitted the version number and solved the lab.

## Why it works (root cause)

The website showed detailed error messages.

These messages revealed internal information, including the framework name and version.

## Impact

An attacker could learn about the website's technology.

This information could help them find other vulnerabilities.

## Remediation

- Hide detailed error messages.
- Use generic error messages.
- Turn off debugging on live websites.
- Keep frameworks updated.
- Do not reveal internal system details.

## What I learned

I learned how to use Burp Suite Repeater to trigger an error.

I also learned how error messages can reveal hidden information about a website.
