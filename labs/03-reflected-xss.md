# Lab 3: Reflected XSS into HTML context with nothing encoded

**Platform:** PortSwigger Web Security Academy  
**Vulnerability class:** Cross-Site Scripting (XSS)  
**Difficulty:** Apprentice  
**Status:** Completed  
**Date completed:** November 1, 2026  
**Tools used:** Google Chrome, PortSwigger Web Security Academy

## Objective

The goal of this lab was to understand and exploit a Reflected Cross-Site Scripting (XSS) vulnerability.

I wanted to learn how a website can accidentally allow someone to insert their own code into a webpage.

The objective was to use the website's search function to make the browser execute JavaScript and display a popup using the `alert()` function.

## Steps

**1. Open the PortSwigger lab.**

I opened the Reflected XSS lab and examined the website.

I noticed that it had a search function where users could enter text.

<img width="3837" height="2013" alt="image" src="https://github.com/user-attachments/assets/b3f9409e-7578-4a45-89cc-8e308c21af29" />


**2. Test the search function.**

I entered:

`test123`

The website responded with:

"0 search results for test123"

This showed that the website was displaying the text I entered back on the webpage.

This is called reflection. It means the website takes information from the user and displays it in its response.
<img width="3804" height="1503" alt="image" src="https://github.com/user-attachments/assets/5c86bf3b-e4b3-4625-b024-6ba9b22da719" />


**3. Test whether the website accepts HTML.**

I entered:

`<b>test123</b>`

The text appeared in bold.

This was important because it showed that the browser was interpreting my input as HTML instead of displaying it as ordinary text.

HTML is the language used to structure webpages. For example, `<b>` tells the browser to make text bold.

<img width="2433" height="747" alt="image" src="https://github.com/user-attachments/assets/9eb57e9d-fbc7-4adc-8bd2-20e72cbd42d6" />


**4. Test whether JavaScript could execute.**

Next, I entered:

`<script>alert(1)</script>`

This time, a popup appeared displaying the number 1.

This proved that the website was allowing JavaScript entered through the search function to execute in the browser.

JavaScript is a programming language that makes webpages interactive. The `alert()` function creates a popup message.

<img width="3807" height="2076" alt="image" src="https://github.com/user-attachments/assets/35602cb2-94fc-45fb-9980-dec2409cd358" />


**5. Confirm the vulnerability.**

The popup confirmed that I had successfully demonstrated reflected XSS.

I did not need to damage the website or access anyone's information. The popup was enough to prove that JavaScript execution was possible.

## Why it works (root cause)

The main problem was that the website did not properly handle the information entered by users before putting it into the webpage.

Normally, a website should treat user input as ordinary text.

However, this website allowed the browser to interpret my input as actual HTML and JavaScript.

Think of it this way:

- I entered text into the search box.
- The website took that text.
- The website placed it into its webpage.
- The browser interpreted the inserted code.
- The JavaScript executed and displayed a popup.

The root cause was the lack of proper output encoding.

Output encoding means converting special characters into a safe format so the browser displays them as text instead of interpreting them as code.

## Impact

Reflected XSS can be dangerous because an attacker may be able to execute JavaScript in another person's browser while they are visiting a vulnerable website.

Depending on the vulnerability and the website's security protections, an attacker could potentially:

- Change what the victim sees on the webpage.
- Access sensitive information available to JavaScript on the page.
- Capture information entered into forms.
- Perform actions using the victim's logged-in session.
- Manipulate the webpage to trick users.

The `alert(1)` popup itself is harmless. However, it demonstrates that JavaScript execution is possible.

This is why even a simple popup can reveal a serious security vulnerability.

## Remediation

Developers can prevent reflected XSS by properly handling information received from users.

Some ways to prevent this vulnerability include:

**1. Output encoding**

Convert special characters into a safe format before displaying user input.

For example, instead of allowing the browser to interpret `<script>` as code, the website should display it as ordinary text.

**2. Use safe methods to display information**

Developers should use methods that treat user input as text rather than allowing it to become HTML.

**3. Input validation**

Check user input and reject information that does not meet the application's requirements. However, input validation alone is not enough to prevent XSS.

**4. Content Security Policy (CSP)**

Use a Content Security Policy to provide an additional layer of protection by restricting which scripts the browser is allowed to execute.

## What I learned

Before completing this lab, I did not fully understand how XSS worked.

I learned:

- What Cross-Site Scripting (XSS) means.
- The difference between reflected, stored, and DOM-based XSS.
- What it means when a website reflects user input.
- How HTML is used to structure webpages.
- How JavaScript can execute inside a browser.
- Why failing to properly encode user input can create security vulnerabilities.
- How a simple `alert(1)` popup can prove that JavaScript execution is possible.
- Why XSS can potentially expose sensitive information or allow unauthorized actions.

**Biggest takeaway:** A website should never blindly trust information entered by its users. If it places that information into a webpage without properly handling it, an attacker may be able to inject and execute JavaScript.

This lab helped me understand how a seemingly harmless search box can become a security vulnerability.
