
# Malware Sandboxing

**Malware sandboxing** is a technique used to isolate malicious code so that it can run in an isolated environment. You can think of a malware sandbox as a stand-alone environment that lets you view or execute the program safely while keeping it contained. Two good examples of sandbox services are Cuckoo and ThreatExpert. ThreatExpert executes files in a virtual environment much like VMware and Virtual PC. This great tool tracks changes made to the filesystem, registry, memory, and network. ThreatExpert even uses API hooks that intercept the malware's interactions in real time.

Even when using a sandbox, you should not expect the malware creators to make analysis an easy process. As an example, malware creators build in checks to try to prevent their malware from running in a sandbox environment. The malware may look at the MAC address to try to determine if the NIC is identified as a virtual one, or it may not run if it does not have an active network connection. In such cases you may need additional tools such as FakeNet, which simulates a network connection to fool the malware so the analyst can observe the malware's network activity from within a sandboxed environment.

# Memory Dumping

**Memory dumping** is another technique that can be used to analyze a program or malicious application. Memory dumping can be used to extract the contents of memory so that the malware's activity can be examined. This technique is used because static analysis is not always possible.

Some malware writers obscure the code to make it hard to examine. To defeat obfuscation, the security professional may perform runtime debugging by dumping the unpacked program from memory once the decompression or decryption routine has completed. This can allow for better analysis; however, some attackers use packers, which have antidumping capabilities to protect their malicious programs from being analyzed. Tools that can be used for memory dumping include these:

*   IDA Pro
*   LordPE
*   OllyDbg

# Process Handling at the Client and Server

Before coding can begin, developers must make a decision as to what programming language they will use and where processes will be performed. Processes can be handled at the client or the server. These are issues that will be reviewed in this section. There are a number of issues and technologies to consider. These include:

*   JSON/REST
*   Browser extensions
*   Asynchronous JavaScript and XML (Ajax)
*   JavaScript/applets
*   Flash
*   HTML5
*   SOAP
*   Web Services Security
*   Buffer overflow
*   Memory leaks
*   Integer overflow
*   Race conditions (TOC/TOU)
*   Resource exhaustion

## JSON/REST

JSON (JavaScript Object Notation) is a lightweight human-readable programming format that is a natural fit with JavaScript applications. It's an alternative to XML and is used primarily to transmit data between a server and a web application. One potential security issue is that JSON can be used to execute JavaScript. REST (Representational State Transfer) is used in mobile applications and mashup tools as a type of simple stateless architecture that generally runs over HTTP. It is considered easier to use than other technologies, such as SOAP. Its advantages include ease of use and modification, and that it helps organize complex datasets.

## Browser Extensions

A browser extension is a computer program that is used to enhance the functionality of a web browser. Browser extensions started off by performing basic tasks and are now increasingly used to greatly extend the functionality of client-side components. Browser extensions run within the browser, across multiple client platforms, and provide the capability of a stand-alone application. Extensions are generally downloaded for the specific browser you are using because not all are universal. Also, extensions may slow down browsing or potentially introduce security flaws. Some examples of extensions are:

*   TinyURL generator, which creates tiny URLs
*   Print Pages to PDF, which is a PDF printer
*   Heartbleed Notifier, which tells you if a site is vulnerable to the Heartbleed SSL vulnerability

## Ajax

Ajax is a programming language used for developing web applications that combines XHTML, CSS, standards-based presentation, and JavaScript. Ajax allows content on web pages to update immediately when a user performs an action. Ajax, like other programming languages, can have security issues, primarily susceptibility to injection attacks. One design approach is to develop the application in Ajax so that it responds only to requests that were sent as expected. All malformed requests should be silently ignored, thereby reducing the possibility for security problems.

## JavaScript/Applets

JavaScript is an object-oriented scripting language. JavaScript is an implementation of the ECMAScript language and is widely used in web pages and applications. It is useful for functions that interact with the Document Object Model (DOM) of the web page.

Somewhat related to JavaScript are Java applets. A Java applet is a snippet of code that is delivered to users in the form of bytecode. These small amounts of code, which are typically one or two bytes, allow the programmer to deliver small specific instructions to be executed. Their advantage is speed and the fact that applets can be executed on many different platforms. When a Java-enabled browser encounters an applet, it fetches the bytecode and passes it to the browser, which executes the code.

From a security standpoint, JavaScript is a concern because it can run locally in a user's browser. Although this means it can respond to a user's actions quickly, it also means JavaScript is vulnerable to XSS and CSRF. XSS can be potentially dangerous. Consider the situation in which an attacker can launch an XSS attack while the victim is connected to his bank's website. This could potentially allow the attacker to access the banking application with the privileges of the victim. The result might be the disclosure of secret information or transferring of large amounts of money without the victim's authorization. CSRF is used in much the same way—the attacker uses JavaScript to trick the victim's browser into taking actions the user didn't intend (such as transferring money at a bank website).

## Flash

Flash was designed to create interactive websites. One of its primary advantages is that it can be used with many different operating systems and devices. However, some vendors such as Apple do not fully support Flash. And according to `http:/money.cnn.com/2013/10/08/technology/security/adobe-security/`, Flash has suffered from numerous problems over the years, including:

*   In 2009, a vulnerability in Reader let hackers open backdoors into people's computers.
*   In 2010, attackers created malicious PDF attachments to hack into several companies, including Adobe, Google and Rackspace.
*   In 2011, another bug gave hackers remote access to people's computers using Flash Player.
*   In 2012, cyber hackers gained access to Adobe's security verification system by tapping into its internal servers.

## HTML5

HTML5 is the fifth revision to the HTML programming language. HTML5 is designed to be backward-compatible. It has support for new features, new input types, and validation for forms. The problem with anything new is that attackers will start to look for vulnerabilities that can be exploited. At the Black Hat conference in 2012, ten problems were identified with HTML5; among these issues were CSRF, clickjacking, XSS, and attacking DOM variables. You can read more at `www.securityweek.com/top-10-security-threats-html5-black-hat`.

## SOAP
