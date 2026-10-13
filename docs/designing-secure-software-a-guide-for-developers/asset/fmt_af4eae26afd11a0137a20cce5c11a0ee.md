
# Web Servers Overtrusting Client Browsers

Web servers overtrusting potentially untrustworthy client browsers is at the root of many web security vulnerabilities. I stress this point, at the risk of repetition, because it is so easily and often forgotten (as I will explain throughout the chapter).

## The HTTP Protocol

> Anyone who considers protocol unimportant has never dealt with a cat.
>
> —Robert A. Heinlein

The HTTP protocol itself is at the heart of the web, so before we dig into web security, it’s worth briefly reviewing how it works. This hyper-simplified explanation serves as a conceptual framework for the rest of the security discussion, and we’ll focus on the parts where security enters the picture. For many, web browsing has become so commonplace in daily life that it’s worth stepping back ands.

Web browsing always begins with a uniform resource locator (URL). The following example shows its parts:

```
http://www.example.com/page.html?query=value#fragment
```

The `scheme` precedes the colon, and specifies the protocol (here, `http`) the browser must use to request the desired resource. IP-based protocols begin with `//` followed by the `hostname`, which for web pages is the domain name of the web server (in this case, `www.example.com`). The rest is all optional: the `/` followed by the `path`, the `?` followed by the `query`, and the `#` followed by the `fragment`. The path specifies which web page the browser is requesting. The query allows the web page content to be parameterized. For example, when searching for something on the web, the URL path for results might be `/search?q=something`. The fragment names a secondary resource within the page, often an anchor as the destination of a link. In summary, the URL specifies how and where to request the content, the specific page on the site, query parameters to customize the page, and a way to name a particular part of the page.

Your web browser has a lot of work to do in order to display the web page when you give it a URL. First, it queries the Domain Name System (DNS) for the IP address of the hostname in order to know where to send the request. The request contains the URL path and other parameters encoded as `request headers` (including any cookies, the user’s preferred language, and so on) sent to the web server host. The server sends back a response containing a status code and `response headers` (which may set cookies, and many other things), followed by the content body that consists of the HTML for the web page. For all embedded resources, such as scripts, images, and so forth, this same request/response process repeats until the content is fully loaded and displayed.

Now let’s look at what web servers must do correctly in order to remain secure. One important detail not yet mentioned is that the request specifies the `HTTP verb`. For our purposes here, we will focus on just the two most common verbs. `GET` requests content from the server. By contrast, clients use the `POST` verb to send form submissions or file uploads. GET requests are explicitly not state-changing, whereas POST requests intend to change the state of the server. Respecting this semantic distinction is important, as will be seen when we cover CSRF attacks. For now, keep in mind that even though the client specifies the request verb to use, the server is the one that decides what to do with it. Additionally, by offering hyperlinks and forms on its pages, the server in effect guides the client to make subsequent GET or POST requests.

Sticklers will point out that one certainly can run a server that changes state in response to GET verb requests and, perversely, refuses to change state for form POST submissions. But if you strictly follow the standard rules, it is vastly easier to make your server secure. Think of it this way: yes, it is possible to climb over fences marked “Keep Out!” at a cliff and walk along the edge of the precipice without falling, but doing so needlessly puts your security in jeopardy.

A related security no-no is embedding sensitive data in a URL; instead, use form POST requests to send the data to the server. Otherwise, the `REFERER` header may disclose the URL of the web page that led to the request, exposing the data. For example, clicking a link on a web page with the URL `https://example.com?param=SECRET` navigates to the link destination using a GET request with a `REFERER` header containing the URL which includes `SECRET`, thereby leaking the secret data. In addition, logs or diagnostic messages risk disclosing the data contained in URLs. While servers can use the `Referrer-Policy` header to block this, they must depend on the client honoring it—hardly a perfect solution. (The `REFERER` header is indeed misspelled in the spec, so we’re stuck with that, but the policy name is correctly spelled.)

One easy mistake to make is including usernames in URLs. Even an opaque identifier, such as the hash of a username, leaks information, in that it potentially allows an eavesdropper to match two separately observed URLs and infer that they refer to the same user.

## Digital Certificates and HTTPS

> If what is communicated is false, it can hardly be called communication.
>
> —Benjamin Mays

The first challenge for secure web browsing is reliably communicating with the correct server. To do this, you must know the correct URL and query a DNS service that provides the right IP address. If the network routes and transmits the request correctly, it should reach the intended server. That’s a lot of factors to get right, and a large attack surface: bad actors could interfere with the DNS lookup, the routing, or the data on the wire at any point along the route. Should the request be diverted to a malicious server, the user might never realize it; it isn’t hard to put up a look-alike website that would easily fool just about anyone.

The HTTPS protocol (also called `HTTP over TLS/SSL`) is tailor-made to mitigate these threats. HTTPS secures the web using many of the techniques covered in Chapter 5. It provides a secure end-to-end tamper-proof encrypted channel, as well as assurance to the client that the intended server is really at the other end of that channel. Think of the secure channel as a tamper-evident pipeline for data that confirms the server’s identity. An eavesdropping attacker could possibly see encrypted data, but without the secret key, it’s indistinguishable from random bits. An attacker may be able to tamper with the data on an unprotected network, but if HTTPS is used, any tampering will always be detected. Attackers may be able to prevent communication, for example by physically cutting a cable, but you are assured that bogus data will never get through.
