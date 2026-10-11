
# Web Services Security (WS-Security, WSS)

**Web Services Security (WS-Security, WSS)** is a security technology developed by OASIS that was designed as an extension to SOAP. One major issue with SOAP, just as with other applications, is poor input validation and sanitization of data. WS-Security was designed to take input in the form of SOAP messages over protocols such as HTTPS. SOAP works with several formats, such as Security Assertion Markup Language (SAML), Kerberos, and X.509 certificates. SOAP can provide confidentiality, integrity, and nonrepudiation.

## Attacks

One of the most important things you can do as an enterprise defender is to understand your attack surface. To put the proper controls in place, organizations typically gather lists of external-facing assets, web applications, databases, storage in the cloud, and VPN services. Once you have a solid understanding of these, then you can begin the process of targeted attack testing and assessment. The reason for targeted attack testing is to measure the effectiveness of currently used controls. You can use penetration testing or tabletop testing to identify gaps in technical controls, create a response, and measure remediation, measuring the risk and possibilities of these attacks of being successful in your network.

### Cross-Site Scripting

**Cross-site scripting (XSS) attacks** are an application issue caused by an injection problem. XSS occurs when malicious scripts are injected into otherwise trusted websites. The malicious script is then passed to the end user's browser, which has no way to know that the script is malicious, since it has been passed from a trusted site. Once executed on the end user's computer, the malicious script can access any cookies, session tokens, or other sensitive information retained by their browser and used with that site. XSS attacks allow the attacker to gain a high level of control over the user's system and communicate directly with the site to which the user is connected.

XSS attacks occur when invalid input data is included in dynamic content that is sent to a user's web browser for rendering, as in the following examples:

```
index.php?name=guest<script>alert(‘attacked’)</script>
```

or

```
index.php?name=<script>window.onload = function() 
{var link=document.getElements⇒ByTagName("a");link[0].
href="http://not-real-xssattackexamples.com";}</script>
```

XSS can occur anywhere a web application uses input from a user in the output it generates, without validating or encoding it. Attackers can inject malicious JavaScript, VBScript, ActiveX, Flash, or HTML into headers for execution on the user's computer. The Common Weakness Enumeration list, specifically `CWE-644`, deals with an application that incorrectly interprets HTTP headers used in a web browser, resulting in an attacker using XSS against a user.

The CASP+ exam may feature one or more simulations where you will need to recognize scripts or commands; they will appear as `</script>` in the question.

### Cross-Site Request Forgery

Closely related to XSS is the **cross-site request forgery (CSRF) attack**. A CSRF attack tricks a user's browser into sending a forged HTTP request, including the user's session cookie and authentication information, to a vulnerable web application. CSRF allows an attacker to force the user's browser to generate requests so that the vulnerable application thinks that the legitimate request is from the victim.

One way to validate a user is using a Completely Automated Public Turing test to tell Computers and Humans Apart (CAPTCHA). CAPTCHA is a security measure where there is a challenge and response to authenticate the user. There are two parts to CAPTCHA, a random sequence of letters and numbers that are distorted but still human readable. The user has to type the letters into a text box to verify they are not a bot.

Both XSS and CSRF flaws are quite widespread. A good source for more information is the **Open Web Application Security Project (OWASP)** at `www.owasp.org`.

### Injections

Many database products such as Microsoft SQL Server, MySQL, and Oracle allow sophisticated access queries to be made. If the database and the underlying OS do not have the proper security controls in place, the attacker can create queries against the database that disclose unauthorized information. This type of attack is generally known as **SQL injection**. A SQL injection attack is carried out when the attacker uses a series of malicious SQL queries to manipulate the SQL database directly. SQL injection attacks can be launched from the address bar of a website, from within application fields, or through queries and searches. Once the SQL injection is launched, the malformed input may cause the database to become unstable or leak information. Attackers use logic such as a single quote (`'`) to test the database for vulnerabilities. Responses such as the one shown in the following code snippet give the attacker the feedback needed to know that the database is vulnerable to attack:

```
Microsoft OLE DB Provider for ODBC Drivers error ‘80040e14’
[Microsoft][ODBC SQL Server Driver][SQL Server]Syntax error converting
the nvarchar value ‘sa_login’ to a column of data type int.
/index.asp, line 5
```

Preventing these types of input problems requires true **defense in depth**. This starts by filtering traffic before it ever enters the network. One approach is to use a **web application firewall (WAF)**, the next advancement in firewall design. WAFs analyze web traffic and can be used to filter out SQL injection attacks, malware, XSS, and CSRF. WAFs require a high degree of application awareness as they have the ability to analyze web traffic and look for items such as malicious XML injection constructs and SQL injection commands.

Another item that can be used to help defend against SQL injection attacks is a **database activity monitor (DAM)**. DAM systems have emerged because companies face many more threats such as SQL injection than in the past. There is also a much greater need for compliance so that companies can track what activity occurs within databases. Laws and regulations such as HIPAA and PCI DSS have increased this demand. DAMs basically monitor the database and analyze the type of activity that is occurring. You can think of DAM as being similar to **Security Information and Event Management (SIEM)**, except that SIEM systems like Splunk correlate and analyze events from multiple sources, whereas DAMs focus specifically on database access and activity.

Not only do you have to protect against SQL and XML injection, **LDAP injection** is another vulnerability if proper controls are not in place. In LDAP injection, queries are constructed from untrusted input without prior validation or sanitization. LDAP uses queries constructed from metacharacters such as brackets or quote symbols. These control the meaning of the query, which affects the type and number of objects retrieved from the directory. If an attacker can create an input command that processes these control characters, they can alter the query and change the intended behavior.

In [Figure 4.6](#c04.xhtml#c04-fig-0006), watch how an attacker changing this LDAP search query finds a node with a given username and password by adding asterisks in strategic locations; it can change the query, and it always evaluates as true, in which case authentication has been bypassed.

![FIGURE 4.6 LDAP injection](images/c04f006.png)

**[FIGURE 4.6](#c04.xhtml#R_c04-fig-0006) LDAP injection**

### Sandbox Escape

**Application sandboxing** is the process of writing files to a sandbox or temporary storage area instead of their normal location. Sandboxing is used to limit the ability of code to execute malicious actions on a user's computer. If you launch an application in the sandbox, it won't be able to edit the Registry or even make changes to other files on the user's hard drive.
