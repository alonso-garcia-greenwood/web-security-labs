# Lab 6: 2FA simple bypass

**Platform:** PortSwigger Web Security Academy  
**Vulnerability class:** Authentication  
**Difficulty:** Apprentice  
**Status:** Not started  
**Date completed:**  
**Tools used:PortSwigger**  

## Objective
The objective was to see if the 2fa was being setup properly and there being no way to skip it 

## Steps
1.Log in as wiener:peter.
<img width="3657" height="1602" alt="image" src="https://github.com/user-attachments/assets/1822fa50-bb77-43dd-bc63-c419d5d816d3" />

2.Observe the 2FA verification page.

3.Open Burp Suite → Proxy → HTTP history.
<img width="3807" height="2232" alt="image" src="https://github.com/user-attachments/assets/40d4e009-4cd0-4ebc-8d7d-676029f53e15" />

3.Inspect the POST /login request and its response.

4.Navigate directly to /my-account without entering a 2FA code.
<img width="3711" height="1446" alt="image" src="https://github.com/user-attachments/assets/c6558464-4ccf-4bb6-b739-f49a085d1dde" />

5.Observe that the account page loads.
<img width="3771" height="1347" alt="image" src="https://github.com/user-attachments/assets/70f89ae7-d4e6-439c-9a55-089e6877642f" />

6.Log out.
7.Log in as carlos:montoya.
8.Repeat the bypass to access Carlos's account.
9.Confirm the lab is solved.

## Why it works (root cause)
The website does not properly verify that users completed 2FA before allowing access to their account.
## Impact
An attacker with a victim's password could bypass 2FA and access their account.
## Remediation
Require successful 2FA verification on the server before granting access to protected pages.
## What I learned
