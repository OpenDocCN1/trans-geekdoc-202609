
Before relaxing the SOP this way, it’s important to make sure the developers understand all of the implications. If this was a production environment, and someone put [`wikidev.browservictim.com`](http://wikidev.browservictim.com) on the Internet, weaknesses in this new site may pose a risk to the [`store.browservictim.com`](http://store.browservictim.com) origin. If an attacker were able to upload malicious code due to unpatched weaknesses, then the wikidev site would have the same level of access as the login site. This could expose information, or lead to XSS, XSRF, or other types of attacks.

## Understanding the SOP with CORS

By default, if you use an XMLHttpRequest object (XHR) to send a request to a different origin, you can’t read the response. However, the request will still arrive at its destination. This is a very useful characteristic of cross-origin requests, and will be discussed in Chapters 9 and 10 as part of a number of attack techniques.

The SOP prevents you from reading the HTTP response headers or body. One of the ways to relax the SOP and allow cross-origin communication with XHR is using Cross-origin Resource Sharing (CORS). If the browserhacker.com origin returns the following response headers, then every subdomain of browservictim.com can open a bidirectional communication channel with browserhacker.com:

```
Access-Control-Allow-Origin: \*.browservictim.com
Access-Control-Allow-Methods: OPTIONS, GET, POST 
Access-Control-Allow-Headers: X-custom
Access-Control-Allow-Credentials: true
```

Other than the first self-explanatory HTTP response header, the other headers specify that requests can be made using any of the OPTIONS, GET or POST methods, and eventually including the X-custom header. Note also the Access-Control-Allow-Credentials header, which is responsible for allowing authenticated communication to a resource. This is demonstrated in the following code snippet:

```
var url = 'http://browserhacker.com/authenticated/user';
var xhr = new XMLHttpRequest()
xhr.open('GET', url, true);
xhr.withCredentials = true;
xhr.onreadystatechange = do_something();
xhr.send();
```

The preceding example retrieves the /authenticated/user resource. In this instance it required credentials for access. The JavaScript enabled authentication support by setting the withCredentials flag to true.

## Understanding the SOP with Plugins

In theory, if a plugin is served from http://browserhacker.com:80/, it should only have access to http://browserhacker.com:80/. In practice, things are not that simple. As you will learn throughout this chapter, there are many SOP implementations in Java, Adobe Reader, Adobe Flash and Silverlight, but most of them are inconsistent and have suffered from different bypasses in the past.

Every major browser plugin implements the SOP in its own way. For instance, some versions of Java consider two different domains to have the same-origin if the IP is the same. This might have devastating results in virtual hosting environments that often host multiple websites from the same IP address.

Adobe has a long history of critical security bugs in its PDF Reader and Flash plugins. Most of those bugs allowed execution of arbitrary code, so the security risk was much higher than a SOP bypass. However, SOP bypasses affected both the plugins too.

Adobe Flash offers a method to allow you to manage cross-origin communication. This is performed through a file named crossdomain.xml, which should exist in the root of the website. The file has content similar to the following:

```
<?xml version="1.0"?>
  <cross-domain-policy>
       <site-control permitted-cross-domain-policies="by-content-type"/>
       <allow-access-from domain="*.browserhacker.com" />
  </cross-domain-policy>
```

With such a policy, every subdomain of browserhacker.com can achieve two-way communication with the application.

Java and Silverlight SOPs can be relaxed in a similar way, because crossdomain.xml is supported by both of these plugins. Silverlight also supports clientaccess-policy.xml. When a cross-origin request is issued, Silverlight first checks for this file, and then if that’s not found, falls back to crossdomain.xml. Both plugins have their quirks, as you will learn in the following sections.

## Understanding the SOP with UI Redressing

UI redressing, in simple terms, is an attack methodology category that changes visual elements in a user interface in order to conceal malicious activities. Overlaying a visible button with an invisible submit button that performs a malicious action, or changing the cursor to move or click independently from where a user actually intends, are both UI redressing attacks. Multiple UI redressing attacks have been successfully exploited in the wild, targeting Facebook and other popular websites, as you will discover later in this chapter.

UI redressing attacks bypass the SOP in different ways. Some of these (now patched) attacks relied on the fact the SOP wasn’t enforced when performing drag&drop actions from the main window to IFrames, between IFrames and between windows. Other attacks rely on the SOP not being enforced under certain conditions while requesting view-source content.

## Understanding the SOP with Browser History

Retrieving the browser history can be potentially devastating for the privacy of an end user. While most of the attacks targeting the user’s privacy are covered in Chapter 5, some examples of browser history attacks are covered in this chapter too.

Some of these attacks rely on classic SOP implementation flaws, such as an http scheme having access to other schemes (for example, browser, about or mx). These attacks worked on Avant and Maxthon, two lesser-known browsers that happen to be very popular in China.

Other more sophisticated attacks involve catching SOP violation errors while loading cross-origin resources. These attacks are useful in unveiling sites the browser has visited previously.

# Exploring SOP Bypasses

The SOP has been interpreted differently by all kinds of developers. This complexity and varied interpretation will work to your advantage when attacking the browser.

One way to expand your attacking opportunities is by finding a way around the SOP. It will allow you to use the victim browser as a liberal pivot point to launch further attacks, not only to the Internet, but also to intranets and even potentially to the local file system.

The following sections will demonstrate methods in which the SOP can be bypassed through browser plugins, browser quirks, or even through third-party applications. This is in no way an extensive list of every single SOP bypass, but acts as a primer for some of the more common bypasses and methods that have been successful. Once the basics have been covered, additional ways to leverage SOP bypasses will be covered in Chapters 6, 7 and 8.

## Bypassing SOP in Java

Java versions 1.7u17 and 1.6u45 don’t enforce the SOP if two domains resolve to the same IP. That is, if browserhacker.com and browservictim.com resolve to the same IP, a Java applet can issue cross-origin requests and read the responses.

Reviewing the Java 6 and 7 documentation, specifically the equals method of the URL object,1 uncovers the following statement: “Two hosts are considered equivalent if both host names can be resolved into the same IP addresses \[…\].” Obviously, this is a vulnerability in Java’s SOP implementation (which was unpatched at the time of writing). The bug is critical when exploited in virtual hosting environments where potentially hundreds of domains are managed by the same server and resolve to the same IP.

Consider the following scenario where www.browserhacker.com and www.browservictim.com resolve to the same IP address 192.168.0.2:

```
$ cat /etc/hosts/
192.168.0.2     www.browservictim.com
192.168.0.2     www.browserhacker.com
```
