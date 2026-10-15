
The term `fingerprinting` can actually be used to describe two different activities. The first is identifying the platform and version of a browser, but the secondary meaning is used when someone is trying to uniquely identify a specific browser from others. Identifying a unique browser is typically used to try to track an individual instead of just identifying the platform. Many other pieces of information are brought into this equation. However, for the purposes of this chapter, the term `fingerprinting` is defined as the act of determining the browser platform and version. For more information about tracking individual users, refer to the “Privacy Attacks” section in Chapter 5.

So, how do you narrow down the exact browser version a target is using? To answer this, this section looks at `HTTP request headers`, `DOM properties`, as well as browser quirks.

`HTTP request headers` are information that is sent with every web request, which detail the supported features of the browser, the URL that is requested, as well as the host and other information. You can look at the header sent to help pick out differences from one browser to the next, as you will explore in the next section.

By looking at the `DOM`, you can see what information the browser has stored about a page that’s being viewed. Because different browsers support different features, particularly those exposed within the DOM, this will help reveal what features a browser has. By comparing that to known features of browsers, you can narrow down the browser type and version further. By combining knowledge about how different aspects of the DOM fit together, you can identify multiple different aspects of the DOM that vary across platform and version, and then combine those to create a match.

You will also investigate how browser bugs can be used to identify a browser. As with most applications, browsers have inconsistencies and bugs from time to time. By looking at these features you can work out if a browser is above or below a certain patch level.

By combining multiple pieces of information, you can determine that a browser might be above version 23 and below version 25, effectively narrowing it down to just a single version. This is the type of fine-tuning that brings you closer to what the actual version of a browser is, and with that information you can more specifically tailor attacks to a particular target.

Combining information gathered from the browser’s `User-Agent` (`UA`) header and `DOM` properties is useful for validating your fingerprinting results. The `UA` header can be spoofed easily so it shouldn’t always be trusted by itself. If you hook a browser that includes “Firefox” in its `UA` header, but appears to have the `window.opera` property in the DOM, this browser may not in fact be Firefox. From this analysis you might deduce that it is in fact an Opera browser with a fake `UA` header. `DOM` properties can be spoofed too, but it’s not as simple, nor as common, as changing the `UA` header. If you add some checks for browser bugs, in addition to `DOM` properties and `UA` headers, you should be able to reliably ascertain what type of browser you’re attacking.

## Fingerprinting using HTTP Headers

Headers are included in every HTTP request and response, as touched on briefly in the “HTTP Headers” section of Chapter 1. These headers help the browser and the server agree on how information will be transferred, as well as share information about web pages and data that are beyond the scope of the contents of the page. The type of things that browsers and servers discuss is a topic that isn’t for those weak in constitution. They tend to dismiss the pleasantries and get down to the bare essentials pretty quickly. Let’s take a look at [Figure 6-2](#c06.html#figure6-2) to understand what makes up a web request.

 start figure 

[**Figure 6-2:**](#c06.html#figureanchor6-2) Browser headers observed at echo.opera.com

![c06f002.tif](image_fi/662090c06/c06f002.png)

 end figure 

By visiting [http://echo.opera.com](http://echo.opera.com), you can view the headers that your browser sends to the server within the request. The top line is frequently called the request line. It consists of a verb, a location, and a protocol version. The verb is what you want to do. These are typically either `GET`, `POST`, or `HEAD`. In the context of fingerprinting, the verb, location, and protocol don’t matter as much as the rest of the information. You can see in [Figure 6-2](#c06.html#figure6-2) that the `Host` header is first, and it is specifying that the host that you are connecting to is echo.opera.com. The fact that the `Host` header is first is important, as you’ll see further on.

For fingerprinting purposes, the `User-Agent` header is the most informative, but also the most easily spoofed header. You can see from the screenshot in [Figure 6-2](#c06.html#figure6-2) that the browser is clearly indicating that it is Firefox 21 running on an Intel Macintosh. This browser is using the Gecko layout engine, the layout engine for Mozilla Firefox. This knowledge is additional verification that the browser is likely to be Firefox.

The rest of the headers indicate communication parameters. The `Accept` header indicates the types of information that the browser will accept as a response, and the `Accept-Language` header indicates the desired language. The `Accept-Encoding` header indicates preferences for how to compress the data returned in order to save space, and the `Connection` header indicates that it will support multiple requests on a single connection. These headers are often sent in a specific order. It’s also common that the order of the headers is different depending on different browser versions.

Take a look at [Figure 6-3](#c06.html#figure6-3), which is the same page on a different platform, and try to spot the differences with [Figure 6-2](#c06.html#figure6-2).

 start figure 

[**Figure 6-3:**](#c06.html#figureanchor6-3) Results of echo.opera.com viewed through IE 6 on Windows XP

![c06f003.tif](image_fi/662090c06/c06f003.png)

 end figure 

You can tell from the icon that this was taken on a Windows box running Internet Explorer. As you dig in, you see a number of other things that help identify not just the browser, but the software that’s installed on the system. Looking at the `User-Agent` headers here, you see that this is IE 6 on Windows XP, but that’s not all: the `User-Agent` is also listing the web-based enhancements that have been installed into IE.

The .NET framework versions 2, 3, 3.5, and 4 have all been installed, and the Microsoft Real-Time Communications plugins are also installed. If this browser isn’t spoofing the `User-Agent` field, you now know exact versions of this software that you might be able to target. However, if the information is spoofed, you are still getting useful information simply from the order in which the headers are sent.

Take note of the order of each header item, and notice the position of the `Host` header. In the case of Firefox the `Host` header is first, and on IE 6 it’s closer to the end. The `Accept`, `Accept-Language`, and `Accept-Encoding` headers are in the same order, however, they are before the `User-Agent` instead of after. These aspects are more difficult to change than the contents of the `User-Agent` field, so when you see headers in this order, it’s a good indication that the browser you’re targeting really is Internet Explorer.

To make life a little more interesting, not all versions of IE send the headers in the same order. Take a look at IE 8 on Windows 7, as shown in [Figure 6-4](#c06.html#figure6-4).

 start figure 

[**Figure 6-4:**](#c06.html#figureanchor6-4) Results of echo.opera.com viewed through IE8 on Windows 7

![c06f004.tif](image_fi/662090c06/c06f004.png)

 end figure 
