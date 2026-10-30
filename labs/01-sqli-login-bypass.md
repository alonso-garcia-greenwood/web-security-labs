# Lab 1: SQL injection vulnerability allowing login bypass

**Platform:** PortSwigger Web Security Academy  
**Vulnerability class:** SQL injection  
**Difficulty:** Apprentice  
**Status:** Completed  
**Date completed: (10/30/2026)**  
**Tools used: Burp Suite**  

## Objective
Exploit a SQL injection vulnerability in the login function of a PortSwigger lab app in order to log in as the administrator user without knowing their password.

## Steps
1. Opened the lab and went to the login page
2. in the username part write administrator'-- 
<img width="2445" height="993" alt="image" src="https://github.com/user-attachments/assets/0879f9fc-6093-4c4b-824c-4fb4fc6bc2cb" />

3. password fill it in it can be anything 
## Why it works (root cause)
This works because this website is connected to a database server the way this works is when a user puts the username and password a query is written into this database server imaging someone with the user "Dolphin" AND password being "Fish233" when this is imputed a query is being written Select * FROM users WHERE username = 'Dolphin' AND password = 'Fish233' however the problem is this is written in sql which at times can be played with in a hackers advantage when putting administrator'-- you are altering the query you are making the password section of the query be a comment so its not gonna be used so all u need is the real username to get in.
<img width="3837" height="1899" alt="image" src="https://github.com/user-attachments/assets/d7c2c7cf-166b-4807-872f-6d1505f9e455" />


## Impact
An attacker could get administrator access without needing a password. If this were a real application, the attacker would get access to sensitive data, which could lead to a data breach, because the administrator could typically view and modify other users' accounts and information, change application settings, and delete data.

## Remediation
Database developers should use parameterized queries instead of building queries where you join user input into a string so it treats inputs as data and not part of the command of the query


