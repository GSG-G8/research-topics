# Attacks


## What is attack (cyber attack) ?
A cyber attack is any type of offensive action that targets computer information systems, infrastructures, computer networks or personal computer devices, using various methods to steal, alter or destroy data or information systems.


### The Top 10 OWASP(Open Web Application Security Project) vulnerabilities in 2020 are:

1-Injection

2-Broken Authentication

3-Sensitive Data Exposure

4-XML External Entities (XXE)

5-Broken Access control

6-Security misconfigurations

7-Cross Site Scripting (XSS)

8-Insecure Deserialization

9-Using Components with known vulnerabilities

10-Insufficient logging and monitoring


## Man in the middle attack (MITM)

![](https://media.discordapp.net/attachments/663671271376289792/684025460719747132/download.png)

### What is MITM attack
A man in the middle (MITM) attack is a general term for when a perpetrator positions himself in a conversation between a user and an application—either to eavesdrop or to impersonate one of the parties, making it appear as if a normal exchange of information is underway.

### The goal of an attack 
is to steal personal information, such as login credentials, account details and credit card numbers.

 Targets are

 typically the users of financial applications, SaaS businesses, e-commerce sites and other websites where logging in is required.


Information obtained during an attack could be used for many purposes, including identity theft, unapproved fund transfers or an illicit password change.
Interception
The first step intercepts user traffic through the attacker’s network before it reaches its intended destination.

The most common (and simplest) way of doing this is a passive attack in which an attacker makes free, malicious WiFi hotspots available to the public. Typically named in a way that corresponds to their location, they aren’t password protected. Once a victim connects to such a hotspot, the attacker gains full visibility to any online data exchange.

Attackers wishing to take a more active approach to interception may launch one of the following attacks:

_IP spoofing
_ARP spoofing 
-DNS spoofing
2- Decryption :
After interception, any two-way SSL traffic needs to be decrypted without alerting the user or application.
How To Avoid MiTM Attacks?
The key to avoiding man-in-the-middle attacks is the same as with most other attacks: 
be careful and keep your systems updated. 


## What is cross-site scripting (XSS)?


### Cross-Site Scripting (XSS) attacks
 are a type of injection, in which malicious scripts are injected into trusted websites. XSS attacks occur when an attacker uses a web application to send malicious code, generally in the form of a browser side script, to a different end user. Flaws that allow these attacks to succeed are quite widespread and occur anywhere a web application uses input from a user within the output it generates without validating or encoding it.
 


### Stored and Reflected XSS Attacks
XSS attacks can generally be categorized into three categories: stored ,reflected And DOM-based XSS. 

#### Stored XSS Attacks
Stored attacks are those where the injected script is permanently stored on the target servers, such as in a database, in a message forum, visitor log, comment field, etc. The victim then retrieves the malicious script from the server when it requests the stored information.

#### Reflected XSS Attacks
Reflected attacks are those where the injected script is reflected off the web server, such as in an error message, search result, or any other response that includes some or all of the input sent to the server as part of the request.

#### DOM-based XSS: 
where the vulnerability exists in client-side code rather than server-side code.


### Is Your Website or Web Application Vulnerable to Cross-site Scripting

Cross-site Scripting vulnerabilities are one of the most common web application vulnerabilities. The OWASP organization (Open Web Application Security Project) lists XSS vulnerabilities in their OWASP Top 10 2020 document as the seventh most prevalent issue.
Fortunately, it’s easy to test if your website or web application is vulnerable to XSS and other vulnerabilities by running an automated web scan using the Acunetix vulnerability scanner, which includes a specialized XSS scanner module.


### How to Prevent XSS

To keep yourself safe from XSS, you must sanitize your input. Your application code should never output data received as input directly to the browser without checking it for malicious code.
The best way to find flaws is to perform a security review of the code and search for all places where input from an HTTP request could possibly make its way into the HTML output. Note that a variety of different HTML tags can be used to transmit a malicious JavaScript. Nessus, Nikto, and some other available tools can help scan a website for these flaws, but can only scratch the surface. If one part of a website is vulnerable, there is a high likelihood that there are other problems as well.



## Cross-Site Request Forgery


is an attack that forces an end user to execute unwanted actions on a web application in which they’re currently authenticated. 
    

### How does the attack work:

the attacker uses his or her website to send malicious code to a vulnerable web application in which a user is already authenticated.
When the user visits the attacker’s website, the malicious code inadvertently forces the user’s browser to generate an unwanted request to the intended web application, thereby also making it send an authentication cookie. That allows the attacker to gain access to the functionality of the target web application just as the user would.

![](https://media.discordapp.net/attachments/682186920586903553/684027235719577630/CSRF.png
)




### How to prevent CSRF attaks: 

An attacker can launch a CSRF attack when he knows which parameters and value combination are being used in a form. Therefore by adding an additional parameter with a value that is unknown to the attacker and can be validated by the server, you can prevent CSRF attacks. we can use the following method to avoid this issue
* Implement an Anti-CSRF Token
An anti-CSRF token is a type of CSRF protection. It is a random string that is only known by the user’s browser and the web application. The anti-CSRF token is usually stored inside a session variable. It is typically on a page inside a hidden form field which is sent together with the request.

If the value of the session variable and the hidden form field match, the web application accepts the request. If they do not match the request is dropped.