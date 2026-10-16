
![tip](images/tip.png)When sifting through your site with Google, be sure to look for sensitive information about your servers, network, and organization in Google Groups ([`http://groups.google.com`](http://groups.google.com)), which is the Usenet archive, and newer sites such as Reddit and Quora. I've found online postings that reveal too much about the internal network and business systems; the sky is the limit. If you find something that doesn’t need to be there, you can work with Google to have it edited or removed. For more information, see Google’s Contact us page at [`https://www.google.com/intl/en/contact`](https://www.google.com/intl/en/contact).

Looking at the bigger picture of web security, Google hacking is limited, but if you’re really into it, check out Johnny Long’s book *Google Hacking for Penetration Testers* (Syngress).

### Countermeasures against directory traversals

You can employ three main countermeasures against having files compromised via malicious directory traversals:

*   **Don’t store old, sensitive, or otherwise nonpublic files on your web server.** The only files that should be in your `/htdocs` or `DocumentRoot` folder are those that are needed for the site to function properly. These files shouldn't contain confidential information that you don’t want the world to see.

*   **Configure your `robots.txt` file.**

    This will help prevent search engines, such as Google, from crawling the more sensitive areas of your site.

*   **Ensure that your web server is configured to allow public access to only those directories that are needed for the site to function.** Minimum privileges are key, so provide access to only the files and directories needed for the web application to perform properly.

    ![technicalstuff](images/technicalstuff.png)Check your web server’s documentation for instructions on controlling public access. Depending on your web-server version, these access controls are set in the `httpd.conf` file and the `.htaccess` files for Apache (see [`http://httpd.apache.org/docs/current/configuring.html`](http://httpd.apache.org/docs/current/configuring.html)) and Internet Information Services Manager for IIS. The latest versions of these web servers have good directory security by default, so make sure that you're running the latest versions.

*   **Consider using a search engine honeypot.** A *honeypot* draws in malicious users so that you can see how the bad guys are working against your site. Then you can use the knowledge you gain to keep them at bay. One example is the Google Hack Honeypot ([`http://ghh.sourceforge.net`](http://ghh.sourceforge.net)).

### Input-filtering attacks

Websites and applications are notorious for taking practically any type of input, mistakenly assuming that it’s valid, and processing it further. Not validating input is one of the greatest mistakes that web developers can make.

Several attacks that insert malformed data — often, too much at one time — can be run against a website or application, which can confuse the system and make it divulge too much information to the attacker. Input attacks can also make it easy for the bad guys to glean sensitive information from the web browsers of unsuspecting users.

#### Buffer overflows

One of the most serious input attacks is a buffer overflow that specifically targets input fields in web applications. A credit-reporting application, for example, might authenticate users before they’re allowed to submit data or pull reports. The login form uses the following code to grab user IDs with a maximum input of 12 characters, as denoted by the `maxsize` variable:

`&lt;form name="Webauthenticate" action="www.your_web_app.com/login.cgi" method="POST"&gt;&lt;input type="text" name="inputname" maxsize="12"&gt;`

A typical login session involves a valid login name of 12 characters or fewer, but the `maxsize` variable can be changed to something huge, such as 100 or even 1,000. Then an attacker can enter bogus data in the login field. What happens next is anyone's call. The application might hang, overwrite other data in memory, or crash the server.

A simple way to manipulate such a variable is to step through the page submission by using a web proxy, such as those built into the commercial web vulnerability scanners I mention in this chapter or the free Burp proxy.

![tip](images/tip.png)Web proxies sit between your web browser and the server you’re testing and allow you to manipulate information sent to the server. To begin, you must configure your web browser to use the local proxy of 127.0.0.1 on port 8080. To access this proxy in Mozilla Firefox, choose Tools ⇒   Options, scroll to the bottom of the Options dialog box, and select Settings in the Network Proxy section, Next, select the Manual Proxy Configuration radio button. In Internet Explorer, click the gear icon and choose Internet Options from the drop-down menu; in the resulting dialog box, click the LAN Settings button in the Connections section, select the Use a proxy server for your LAN radio button, and enter the appropriate host name/IP address and port number.

All you have to do is change the field length of the variable before your browser submits the page, and the page is submitted using whatever length you give. You can also use Firefox Web Developer add-on to remove maximum form-field lengths defined in web forms, as shown in [Figure 15-2](#c15.xhtml#c15-fig-0002).

![ FIGURE 15-2:  Using Firefox Web Developer to reset form-field lengths.](images/9781119485476-fg1502.png)

 [FIGURE 15-2:](#c15.xhtml#rc15-fig-0002)  Using Firefox Web Developer to reset form-field lengths.

#### URL manipulation

An automated input attack manipulates a URL and sends it back to the server, telling the web application to do various things, such as redirect to third-party sites or load sensitive files from the server. Local file inclusion is one such vulnerability. This vulnerability occurs when the web application accepts URL-based input and returns the specified file’s contents to the user, as in the following example of an attempted breach of a Linux server’s `passwd` file:

`https://www.your_web_app.com/onlineserv/Checkout.cgi?state=detail&amp;language=english&amp;imageSet=/../..//../..//../..//../..///etc/passwd`

It’s important to note that most recent application platforms, such as ASP.NET and Java, are pretty good about not allowing such manipulation of the URL variables, but I still see this vulnerability periodically.

The following links demonstrate another example of URL trickery called URL redirection:

`http://www.your_web_app.com/error.aspx?URL=http://www.bad~site.com&ERROR=Path+'OPTIONS'+is+forbidden.http://www.your_web_app.com/exit.asp?URL=http://www.bad~site.com`

In both situations, an attacker can exploit the vulnerability by sending the link to unsuspecting users via email or by posting it on a website. When users click the link, they can be redirected to a malicious third-party site containing malware or inappropriate material.

 ![tip](images/tip.png)If you have nothing but time on your hands, you might uncover these types of vulnerabilities manually. In the interest of accuracy (and sanity), however, these attacks are best carried out by running a web vulnerability scanner, which can detect the weakness by sending hundreds of URL iterations to the web system very quickly.

#### Hidden field manipulation

Some websites and applications embed hidden fields in web pages to pass state information between the web server and the browser. Hidden fields are represented in a web form as `<input type="hidden">`. Because of poor coding practices, hidden fields often contain confidential information (such as product prices on an e-commerce site) that should be stored only in a back-end database. Users shouldn't see hidden fields (hence, the name), but a curious attacker can discover and exploit them. To do so yourself, follow these steps:

1.  **View the HTML source code.**
