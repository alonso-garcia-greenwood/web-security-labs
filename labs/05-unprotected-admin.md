# Lab 5: Unprotected admin functionality

**Platform:** PortSwigger Web Security Academy  
**Vulnerability class:** Access control  
**Difficulty:** Apprentice  
**Status:** Finished
**Date completed:11/2/2026**  
**Tools used: PortSwigger**  

## Objective
In this lab basically there is a unprotected admin panel that should only be accessible to any administrators and the lab tells us that this is not properly protected and our main objective is to delete the user Carlos. 

## Steps
1. My first step was to go to the actual website
<img width="3792" height="1887" alt="image" src="https://github.com/user-attachments/assets/37b842ed-3354-41ed-b700-e2a7ab3736fe" />
2. we need to think where would a admin panel be hidden so I tried changing the URL by adding /admin and /administrator
<img width="3834" height="2139" alt="image" src="https://github.com/user-attachments/assets/33b0b8af-f2cd-4c27-a97d-f3b505b267ac" />
3. try right clicking and view page source and try to look for a file path that will maybe let us find where an administrator panel could be at
<img width="3834" height="1998" alt="image" src="https://github.com/user-attachments/assets/0164c00b-e285-4abc-b713-a1539f3b4af2" />
4. we found nothing yet on finding the administrator panel so lets see if /robots.txt finds something the web developer was trying to hide like the file path for a admin panel
<img width="3837" height="2118" alt="image" src="https://github.com/user-attachments/assets/5531d9c1-a275-4592-8ac7-e9ea2931a7ef" />
5. we found the file path they want to disallow /administrator panel so no one knows it exist
6. we found the administrator panel to delete the user carlos
<img width="3837" height="2034" alt="image" src="https://github.com/user-attachments/assets/df061be8-1b72-43c5-a45a-2416dca15ad7" />






## Why it works (root cause)
the website exposed the administrator panel through /robots.txt. The worst part is the admin panel does not properly check to see if the visitor has admin privileges before allowing actions that require admin authority 


## Impact
An unauthorized user could potentially find this vulnerability and gain admin privileges which can result in account deletion  

## Remediation
Implement a way for the website to verify whether a user has administrator privileges before allowing them to access the control panel. The main lesson is that developers should not rely on simply hiding the admin panel. Instead, they must prevent unauthorized users from accessing it by enforcing proper access controls on the server.

## What I learned
