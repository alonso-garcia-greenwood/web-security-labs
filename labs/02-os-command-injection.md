# Lab 2: OS command injection, simple case

**Platform:** PortSwigger Web Security Academy  
**Vulnerability class:** OS command injection  
**Difficulty:** Apprentice  
**Status:** Completed  
**Date completed: 10/30/2026**  
**Tools used: Port Swigger, Burp Suite**  

## Objective
The main goal of this lab was to learn how a OS Injection exploit is used towards applications and websites by using port swigger and Burp suite I was able to perform OS command injection 

## Steps
1.Get into the portswigger lab 
<img width="3837" height="1896" alt="image" src="https://github.com/user-attachments/assets/8a8ae78f-6bc9-4622-b0a4-abe13194daaa" />
2. click on one of the products notice how there is only a drop down section this limits us from being able to run or see if we can run any shell commands 
<img width="3780" height="1965" alt="image" src="https://github.com/user-attachments/assets/db31bda9-cfe5-4b1f-bbdb-2ecc2a90fecf" />
3. We are gonna need a proxy in order to intercept the http request between the browser and the web application which would allows us to modify what request is going to be sent to the application server 
4. Download Burp suite than open it
<img width="2376" height="1347" alt="image" src="https://github.com/user-attachments/assets/a988aff2-3883-49c8-891d-cb2d0ce2666f" />
5. click the proxy tab make sure things are running on port 8080
<img width="2253" height="219" alt="image" src="https://github.com/user-attachments/assets/54b05f0a-5521-46a5-b470-f9065cf6c0b2" />
6. open burps browser 
<img width="2394" height="1347" alt="image" src="https://github.com/user-attachments/assets/054f6c4c-8247-47da-b449-f47797c430d1" />
7. enable intercept
8. once you are in the open burp browser go into the lab and click view http requests
<img width="3210" height="1554" alt="image" src="https://github.com/user-attachments/assets/33579c6e-caee-479a-9a0e-fa526ebaaefb" />
9. return to burp suite and view the http requests you should see POST and GET requests 
10. Go to Proxy → Intercept.
11. click a product in the browser than go back to burb
12. <img width="3837" height="2244" alt="image" src="https://github.com/user-attachments/assets/cd8b1c80-ccc1-4de1-8265-c2d6f4d43c66" />








## Why it works (root cause)

## Impact

## Remediation

## What I learned
