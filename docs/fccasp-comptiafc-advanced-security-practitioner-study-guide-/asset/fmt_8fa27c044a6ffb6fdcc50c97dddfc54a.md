
# XSS

XSS can occur anywhere a web application uses input from a user in the output it generates, without validating or encoding it. Attackers can inject malicious JavaScript, VBScript, ActiveX, Flash, or HTML for execution on the user's computer. The CASP exam may feature one or more simulations where you will need to recognize scripts or commands; they will appear as `</script>` in the question.

## Cross-Site Request Forgery

Closely related to XSS is the `cross-site request forgery` (CSRF) attack. A CSRF attack tricks a user's browser to send a forged HTTP request, including the user's session cookie and authentication information, to a vulnerable web application. CSRF allows an attacker to force the user's browser to generate requests so that the vulnerable application thinks the legitimate request is from the victim. Both XSS and CSRF flaws are quite widespread. A good source for more information is the Open Web Application Security Project (OWASP), `www.owasp.org`.

## Improper Error Handling

A big part of security is building good controls to check all input data, processed data, and output data. Yet even when this is done correctly, you must still deal with potential errors. Sometimes that is where application developers get in trouble as they provide the user with too much information. As an example, if I go to a web page that handles authentication and enter the wrong password, does the application respond with “wrong password,” or simply “wrong username/password,” which makes it a little harder for an intruder. Here are a couple of examples of this type of problem. First, there is the `httpd.conf` file.

```
<location /server-status>
SetHandler server-status
</Location>
```

This configuration file allows anyone to view the server status page, which contains detailed information about the current use of the web server. Another example is the `php.ini` file found on many web servers. When used, this file provides verbose error messages:

```
display_error = on
log_errors = on
Error_log = syslog
ignore_repeated_errors = Off
```

The limits of an application must always be tested to see what responses are returned and what error messages are displayed.

## Geotagging

Geolocation and location-based services are another concern to the CASP. This technology includes the ability to geotag the location of photographs. Most smartphone and tablet users turn this feature on when they activate a device yet never realize this information is used in every photograph they take. Most people don't realize that geotagging is active on their smartphones, either because it is enabled by default and not exposed to the user as an option, or they were asked to enable it and then promptly forgot about it. As a result, individuals often share too much information, right down to their exact location.

The security concern is that hackers or others may potentially have the ability to track the location of specific individuals. If you think this sounds a little creepy, it is! There is an application known as creepy (`http://ilektrojohn.github.io/creepy/`) that allows users to track individuals using the photos they have posted online. Creepy gathers geolocation-related information from social networking sites and presents the results using Google Maps.

Many applications also make use of this technology to identify a user's exact location. The idea is that that you can identify a user by their location for service or revenue. Examples include coupons from nearby coffee shops and restaurants.

## Clickjacking

`Clickjacking`, or `UI redressing`, is described by Wikipedia as “a malicious technique of tricking Web users into revealing confidential information or taking control of their computer while clicking on seemingly innocuous web pages.” This attack works by controlling what the user sees when visiting a web page. Attackers construct a page in such a way that they control what links or buttons a user can see. Victims click on a visible link yet in reality are selecting another link that is not visible to them. This is made possible in the way the attacker designed the web page. In essence, the attacker constructed a page where what the user sees and clicks on does not reflect what action the click actually performs.

Clickjacking targets `state management`. State management refers to the management of the state of one or more user interface controls such as buttons, icons, or choice options in a graphical user interface. If an attacker can obscure the items chosen by the victim, the user has no way of seeing if a button is in the enabled state or if valid choices have been made. In many cases a security professional may have no control over development of an application and be left with finding ways to defend against the vulnerability. To defend against the Flash-based vulnerabilities, set the Always Deny option in the Global Privacy Settings of your Flash Player. Other defenses include disabling plug-ins and using tools such as NoScript (`http:/noscript.net/`).

## Session Management

`Session management` attacks occur when an attacker breaks into the web application's session management mechanism to bypass the authentication controls and spoof the valid user. Two techniques are typically used:

*   Session token prediction
*   Session token sniffing and tampering

Session token prediction attacks occur when the tokens follow a predictable pattern or increment numerically. If an attacker can make a large number of requests, it may be easier to determine the pattern used by the web application.

In some situations, the token may not be encrypted or might even be using weak encoding such as hex-encoding or Base64. The attacker might also attempt to simply sniff a valid token with tools such as Wireshark or Burp Proxy (see [Figure 5.1](#c05.xhtml#c05-fig-0001)). If HTTP cookies are being used and the security flag is not set, the attacker can attempt to replay the cookie to gain unauthorized access. Other session management issues include the following:

1.  **Session IDs Placed in the URL** Some sites encode the session ID and place it in the URL for the page.
2.  **Timeout Exploitation** If a victim uses a public computer and just closes the browser, the website may not log the user out, thus allowing an attacker to reopen the site and gain full access.

![FIGURE 5.1 Burp Proxy cookie capture](images/c05f001.jpg)

[**FIGURE 5.1**](#c05.xhtml#c05-fig-anc-0001) Burp Proxy cookie capture

## Input Validation

`Input validation` is the process of validating data received from the client. This flaw occurs when client input is not validated before being processed by the web application. Web application controls should be used to check that the input is valid. This becomes important because in many automated systems, the output of one system is the input of another. In such situations, data should be checked to validate the information from both the sending and receiving applications. For example, if you enter a negative quantity in a field that requires a positive value, will the web application actually accept it? It shouldn't! [Figure 5.2](#c05.xhtml#c05-fig-0002) shows an example of a poorly constructed application entry form. Notice the grand total of –$2,450.99.

![FIGURE 5.2 Input validation error](images/c05f002.jpg)

[**FIGURE 5.2**](#c05.xhtml#c05-fig-anc-0002) Input validation error

## SQL Injection
