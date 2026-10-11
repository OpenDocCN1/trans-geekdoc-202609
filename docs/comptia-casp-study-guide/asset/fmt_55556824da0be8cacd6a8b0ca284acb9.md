
# JavaScript Object Notation (JSON)

**JavaScript Object Notation (JSON)** is a lightweight, human-readable programming format that is a natural fit with JavaScript applications. It's an alternative to XML, and it is primarily used to transmit data between a server and a web application. One potential security issue is that JSON can be used to execute JavaScript.

# Representational State Transfer (REST)

**Representational State Transfer (REST)** is used in mobile applications and mashup tools as a type of simple stateless architecture that generally runs over HTTP. It is considered easier to use than other technologies, such as SOAP. Its advantages include ease of use and modification and that it helps organize complex datasets.

## Browser Extensions

A **browser extension** is a computer program that is used to enhance the functionality of a web browser. Browser extensions started off by performing basic tasks and now are increasingly used to significantly extend the functionality of client-side components. Browser extensions run within the browser, across multiple client platforms, and they provide the capability of a stand-alone application. Extensions are generally downloaded for the specific browser that you are using because not all are universal. Also, extensions may slow down browsing or potentially introduce security flaws. Some examples of extensions are as follows:

*   TinyURL generator
*   Print pages to PDF
*   Heartbleed Notifier, which tells you if a site is vulnerable to the Heartbleed SSL security bug

## Ajax

**Asynchronous JavaScript and XML (Ajax)** is used for developing web applications and combines XHTML, CSS, standards-based presentation, and JavaScript. Ajax allows content on web pages to update immediately when a user performs an action. Ajax, like other programming languages, can have security issues, primarily susceptibility to injection attacks. One design approach is to develop the application in Ajax so that it responds only to requests that were sent as expected. All malformed requests should be silently ignored, thereby reducing the possibility for security problems.

## JavaScript/Applets

**JavaScript** is an object-oriented scripting language. It is an implementation of the `ECMAScript` language, and it is widely used in web pages and applications. It is useful for functions that interact with the `Document Object Model (DOM)` of the web page.

Somewhat related to JavaScript are Java applets. A **Java applet** is a snippet of code that is delivered to users in the form of bytecode, which acts similar to an assembler. These small amounts of code, which are typically one or two bytes, allow the programmer to deliver small specific instructions to be executed. Their advantage is speed and the fact that applets can be executed on many different platforms. When a Java-enabled browser encounters an applet, it fetches the bytecode and passes it to the browser, which then executes the code. [Figure 4.5](#c04.xhtml#c04-fig-0005) shows how bytecode works.

![FIGURE 4.5 How bytecode works](images/c04f005.png)

[**FIGURE 4.5**](#c04.xhtml#R_c04-fig-0005) How bytecode works

Bytecode is different from machine code. Bytecode is the code that gets created by compiling source code, and machine code is a set of instructions in machine language that can be understood and executed by a machine, namely, the CPU.

From a security standpoint, JavaScript is a concern because it can run locally in a user's browser. Although this means that it can respond to a user's actions quickly, it also means that JavaScript is vulnerable to XSS and CSRF. XSS can be dangerous. Consider the situation in which an attacker can launch an XSS attack while victims are connected to their bank's website. This could allow the attacker to access the banking application with the privileges of the victim. The result might be the disclosure of secret information or transferring of large amounts of money without the victim's authorization. CSRF is used in much the same way—the attacker uses JavaScript to trick the victim's browser into taking actions that the user didn't intend (such as transferring money at a bank website).

## Flash

**Flash** was designed to create interactive websites. One of its primary advantages is that it can be used with many different operating systems and devices. However, some vendors, such as Apple, do not fully support Flash. And according to CNN Tech, Flash has suffered from numerous problems over the years (`money.cnn.com/2013/10/08/technology/security/adobe-security`). These security problems include the following:

*   In 2009, a vulnerability in Adobe Reader let hackers open backdoors into people's computers.
*   In 2010, attackers created malicious PDF attachments to hack into several companies, including Adobe, Google, and Rackspace.
*   In 2011, another bug gave hackers remote access to people's computers using Adobe Flash Player.
*   In 2012, cyberhackers gained access to Adobe's security verification system by tapping into its internal servers.

Fortunately, today it's rare to find websites still relying on Flash. At the time of this writing, it's now used on less than 5 percent of total sites and declining. Adobe discontinued patches and support on December 31, 2020, and blocked Flash content from running in Flash Player. Beginning January 12, 2021, Adobe strongly recommends all users immediately uninstall Flash Player to help protect their systems.

ActiveX was also deprecated as of August 2020. ActiveX was a software framework created by Microsoft that allowed websites to embed multimedia files or software updates. As with anything IT related, what could be used for good was alternatively used by malicious websites. The functionality that ActiveX provided was reduced by HTML5 capabilities.

## HTML5

The **HTML5** markup language is designed to be backward compatible with previous versions of HTML. HTML5 has support for features and input types, as well as validation for forms, which didn't exist until HTML5. HTML5 was officially adopted in 2014, and since then it has seen a few improvements and revisions. For example, it has been extended to XHTML5 (SML-serialized HTML5). However, for the foreseeable future, HTML5 remains the latest content presentation language for the Web and the de facto cross-platform language for mobile applications because it includes features for lower-powered devices.

The Open Web Application Security Project (OWASP) has a great cheat sheet for implementing HTML5 securely. For example, this cheat sheet references ways that a DOM-based XSS vulnerability can be avoided if you configure pages to interpret exchange messages as data, never as the code itself. If you would like more information about configuring web messaging, web sockets, or geolocation, you can find the reference here: `cheatsheetseries.owasp.org/cheatsheets/HTML5_Security_Cheat_Sheet.html#introduction`.

## SOAP

**Simple Object Access Protocol (SOAP)** is designed to exchange XML-based information in computer networks. SOAP provides a basic messaging format. The message is a one-way transmission between SOAP nodes. Messages consist of three parts: an envelope, a set of processing rules, and a set of procedure calls and responses. The advantage of SOAP is that it is built on open technologies, and it will work on a wide variety of platforms. However, because SOAP can pass messages via HTML, there is the possibility that an attacker could intercept these messages and alter or sniff the contents.

## Web Services Security
