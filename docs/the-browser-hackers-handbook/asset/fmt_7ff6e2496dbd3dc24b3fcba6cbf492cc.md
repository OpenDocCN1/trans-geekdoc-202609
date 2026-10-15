
One of the more interesting enhancements found in Jikto was how it managed to bypass the SOP. It did this by loading both the Jikto code and the target origin content into the same-origin through a proxy (or cross-origin bridge). Initially Google Translate was used to proxy the separate requests, but Jikto could be modified to use other sites for proxying too. For a copy of the Jikto code, visit [`https://browserhacker.com`](https://browserhacker.com).

#### Diminutive XSS Worm Replication Contest

By 2008 the concepts behind XSS viruses and worms were well understood and discussed by the security community. From here on, it was just a matter of optimizing and finding the most efficient way in which to construct these self-propagating payloads.

Robert Hansen’s Diminutive XSS Worm Replication Contest of 20087 was one such effort. The idea was to construct, in as few bytes as possible, a self-replicating snippet of HTML or JavaScript that would execute a standard alert dialog box, replicating through a POST request.

Giorgio Maone and Eduardo Vela won with very similar solutions. They managed to construct a 161-byte payload that self-replicated to a PHP file via a POST request. It didn’t grow in size after propagation, didn’t require user interaction, and didn’t even use any data from the cookie:

```
<form>
 <input name="content">
  <img src=""
   onerror="with(parentNode)
  alert('XSS',submit(content.value='<form>'+
   innerHTML.slice(action=(method='post')+
   '.php',155)))">
```

and

```
<form>
 <INPUT name="content">
  <IMG src="" onerror="with(parentNode)
   submit(action=(method='post')+
   '.php',content.value='<form>'+
   innerHTML.slice(alert('XSS'),155))">
```

You can clearly see how abusing this common web application flaw can be leveraged to embed that initial malicious piece of logic. Although we’ve done our best to summarize XSS in all its different forms, it’s important to recall that, like most vulnerabilities in the web security industry, these are still evolving even to this day.

DOM and Universal XSS is a perfect example of these phenomena as a later addition to the XSS classes. Meanwhile, with the continued enhancement of the Internet, HTML, and browser features, we’re confident that XSS will continue to be a valid method in which to get content to execute in weird and wonderful ways.

### Bypassing XSS Controls

The following sections provide an introduction into bypassing XSS controls. Later, in the Evading Detection section of Chapter 3, you will explore further techniques to assist with obfuscating the malicious code.

Most of the previous XSS examples assumed that you as the attacker would not run into any constraints by simply submitting malicious JavaScript. In reality this is not often the case. A number of obstacles will usually prevent your attacking code from executing in the target browser.

These obstacles come in a number of different forms. They include limitations within the context of injection, language quirks between browsers, a browser’s built-in security controls, and even web application defenses. Don’t be surprised if you need to really work for your XSS exploit!

#### Bypassing Browser XSS Defenses

Apart from potential issues with executing JavaScript, the other serious client-side barrier for you is XSS controls within modern-day browsers. These protective methods attempt to reduce the likelihood of an XSS payload executing within the target’s browser. The defenses include Chrome and Safari’s XSS Auditor, Internet Explorer’s XSS filter and the NoScript extension available for Firefox.

An XSS filter bypass technique that relies on how inputs get mutated by browser optimizations has been called mutation-based Cross-site Scripting (mXSS).8 This method is only helpful to you if the browser optimizes your crafted input. That is, the developer parses your input by using innerHTML or something similar.

The key point is that your input is optimized one way or another. The following code demonstrates how mXSS works:

```
// attacker input to innerHTML
<img src="test.jpg" alt="``onload=xss()" />

// browser output
<IMG alt=``onload=xss() src="test.jpg"> 
```

This example highlights how the backtick (`) character can be used to bypass the Internet Explorer XSS filter. The result of the browser optimization in this example is the onload attribute value being executed.

#### Bypassing Server XSS Defenses

XSS filtering isn’t all about the client side of course. In fact, filtering from the web application side has been the standard response to these web vulnerabilities since their discovery. In best cases, XSS defenses in the web application are implemented as both input filtering and output encoding.

One bypass example was in Microsoft’s .NET Framework. It offered a number of methods for developers to reduce the likelihood of malicious payloads being parsed by the server, including the RequestValidator class. Earlier versions of these weren’t completely effective. For example, submitting either of the following payloads would bypass the filter:

```
<~/XSS/*-*/STYLE=xss:e/**/xpression(alert(6))>
<%tag style="xss:expression(alert(6))">
```

Both of these examples leveraged the expression() feature, part of Microsoft’s Dynamic Properties. This functionality was introduced to provide dynamic properties within CSS.

In addition to fixing these issues at their source, security vendors were quick to provide automated methods in which to fix these issues outside of the vulnerable applications themselves. These are primarily seen in devices such as Web Application Firewalls (WAF), or even software filters to perform the same task. In all instances and combinations of technology and process, the goal is similar to their client-side counterparts. That is, to reduce the likelihood of web security flaws being exploited by an attacker.

The technology was so effective that all the attackers went home, and WAF technology was seen as a panacea to all the web vulnerabilities. And, of course, Santa Claus is real! Well actually… when presented with a challenge, hackers rose to the occasion.9 Much like bypassing client-side controls, similar payloads and methods were developed for server-side controls.

A common technique used by WAF (and related) technology to filter malicious payloads included detection of out-of-context or suspicious parentheses. Gareth Heyes’ technique10 from 2012 is a great bypass example that attaches an error handler to the window DOM object (without parentheses) and immediately throws it:

```
onerror=alert;throw 1;
onerror=eval;throw'=alert\x281\x29';
```

Neither of these examples contains suspicious parentheses. However for them to work, their injection point has to exist within an attribute of an HTML element.

 start feature 

* * *

**XSS Cheat Sheets** Yes, we’ll admit, if you’re not much of a developer or JavaScript hacker, the previous examples may leave you with a confounded look on your face, and your hands filled with the hair that you’ve just ripped off your head! Not to worry. In many circumstances it would be unreasonable to expect an attacker, or tester, to remember all the possible methods in which to try and bypass XSS filters. One of the original and best-known XSS cheat sheets available is Robert Hansen’s (RSnake) XSS Cheat Sheet, which has been donated to OWASP and is available from [`https://www.owasp.org/index.php/XSS_Filter_Evasion_Cheat_Sheet`](https://www.owasp.org/index.php/XSS_Filter_Evasion_Cheat_Sheet). With all the new features being introduced into HTML5, it was only a matter of time before new methods and attributes to abuse browsers were discovered. Mario Heiderich has published the HTML5 security cheat sheet available at [`http://html5sec.org/`](http://html5sec.org/). In addition to these cheat sheets, innumerable combinations exist in which these payloads can be converted, encoded, combined, and mashed together. Methods to help you perform this include: 
