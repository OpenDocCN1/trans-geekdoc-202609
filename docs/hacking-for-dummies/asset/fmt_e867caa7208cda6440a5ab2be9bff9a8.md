
![tip](images/tip.png)To see the source code in Internet Explorer and Firefox, right-click the page and choose View Source or View Page Source from the contextual menu.

2. **Change the information stored in these fields.**

A malicious user might change a price from $100 to $10, for example.

3. **Repost the page to the server.**

This step allows the attacker to obtain ill-gotten gains, such as a lower price on a web purchase.

Such vulnerabilities are becoming rare, but like URL manipulation, the possibility for exploitation exists, so it pays to keep an eye out.

![warning](images/warning.png)Using hidden fields for authentication (login) mechanisms can be especially dangerous. I once came across a multifactor authentication intruder lockout process that relied on a hidden field to track the number of times the user attempted to log in. This variable could be reset to zero for each login attempt and thus facilitate a scripted dictionary or brute-force login attack. It was somewhat ironic that the security control designed to *prevent* intruder attacks was vulnerable to an intruder attack.

Several tools, such as the proxies that come with commercial web vulnerability scanners and Burp Proxy, can easily manipulate hidden fields. [Figure 15-3](#c15.xhtml#c15-fig-0003) shows the WebInspect SPI Proxy interface and a web page’s hidden field.

![ FIGURE 15-3:  Using WebInspect to find and manipulate hidden fields.](images/9781119485476-fg1503.png)

 [FIGURE 15-3:](#c15.xhtml#rc15-fig-0003)  Using WebInspect to find and manipulate hidden fields.

If you come across hidden fields, you can try to manipulate them to see what can be done. It’s as simple as that.

#### Code injection and SQL injection

Similar to URL manipulation attacks, code-injection attacks manipulate specific system variables. Here’s an example:

`http://www.your_web_app.com/script.php?info_variable=X`

Attackers who see this variable can start entering different data in the `info_variable` field, changing `X` to something like one of the following lines:

`http://www.your_web_app.com/script.php?info_variable=Yhttp://www.your_web_app.com/script.php?info_variable=123XYZ`

This example is rudimentary. Nonetheless, the web application may respond in a way that gives attackers more information than they want, such as detailed errors or access to data fields that they're not authorized to access. The invalid input may also cause the application or the server to hang. Attackers can use this information to find out more about the web application and its inner workings, which can lead to a serious system compromise.

![warning](images/warning.png)If HTTP variables are passed in the URL and are easily accessible, it’s only a matter of time before someone exploits your web application.

I once used a web application to manage some personal information that did just this. Because a `"name"` parameter was part of the URL, anyone could gain access to other people’s personal information by changing the `"name"` value. If the URL included `"name=kbeaver"`, a simple change to `"name=jsmith"` would bring up J. Smith's home address, Social Security number, and so on. Ouch! I alerted the system administrator to this vulnerability. After a few minutes of denial, he agreed that it was indeed a problem and proceeded to work with the developers to fix it.

Code injection can also be carried out against back-end SQL databases in an attack known as *SQL injection.* Malicious attackers insert SQL statements — such as `CONNECT`, `SELECT`, and `UNION` — into URL requests to attempt to connect and extract information from the SQL database that the web application interacts with. SQL injection is made possible by applications' failure to validate input properly combined with informative errors returned from database servers and web servers.

Two general types of SQL injection are standard (also called error-based) and blind. *Error-based* SQL injection is exploited based on error messages returned from the application when invalid information is input into the system. *Blind* SQL injection happens when error messages are disabled, requiring the hacker or automated tool to guess what the database is returning and how it’s responding to injection attacks.

![tip](images/tip.png)A quick (although not always reliable) way to determine whether your web application is vulnerable to SQL injection is to enter a single apostrophe (’) in your web form fields or at the end of the URL. If a SQL error is returned, odds are good that SQL injection is present.

You’re definitely going to get what you pay for when it comes to scanning for and uncovering SQL injection flaws with a web vulnerability scanner. As with URL manipulation, you’re much better off running a web vulnerability scanner to check for SQL injection, which allows an attacker to inject database queries and commands through the vulnerable page to the back-end database. [Figure 15-4](#c15.xhtml#c15-fig-0004) shows numerous SQL injection vulnerabilities discovered by the Netsparker vulnerability scanner.

![ FIGURE 15-4:  Netsparker discovered SQL injection vulnerabilities.](images/9781119485476-fg1504.png)

 [FIGURE 15-4:](#c15.xhtml#rc15-fig-0004)  Netsparker discovered SQL injection vulnerabilities.

The neat thing about Netsparker is that after it uncovers SQL injection, you can use the built-in tool Execute SQL Commands to further demonstrate the weakness. A screens hot of SQL injection in action is about as good as vulnerability and penetration testing gets!

When you discover SQL injection vulnerabilities, you may be inclined to stop there without trying to exploit the weakness. That’s fine. But I prefer to see how far I into the database system I can get. I recommend using any SQL injection capabilities built into your web vulnerability scanner if possible so that you can demonstrate the flaw to management.

![tip](images/tip.png)If your budget is limited, consider using a free SQL injection tool such as SQL Power Injector ([`www.sqlpowerinjector.com`](http://www.sqlpowerinjector.com)) or the Firefox add-on SQL Inject Me ([`https://addons.mozilla.org/en-us/firefox/addon/sql-inject-me`](https://addons.mozilla.org/en-us/firefox/addon/sql-inject-me)).

I cover database security in depth in [Chapter 16](#c16.xhtml).

#### Cross-site scripting

Cross-site scripting (XSS) is perhaps the best-known and most-widespread web vulnerability that occurs when a web page displays user input — typically via JavaScript — that isn’t validated properly. An attacker can take advantage of the absence of input filtering and cause a web page to execute malicious code on any computer that views the page.

An XSS attack can display the user ID and password login page from another rogue website, for example. If users unknowingly enter their user IDs and passwords in the login page, the user IDs and passwords are entered into the hacker’s web server log file. Other malicious code can be sent to a victim’s computer and run with the same security privileges as the web browser or email application that’s viewing it on the system. The malicious code could provide a hacker full read/write access to browser cookies or browser history files, or even permit him to download or install malware.

![tip](images/tip.png)A simple test shows whether your web application is vulnerable to XSS. Look for any fields in the application that accept user input (such as in a login or search form), and enter the following JavaScript statement:

`&lt;script&gt;alert('XSS')&lt;/script&gt;`

If a window pops up that reads `XSS`, as shown in [Figure 15-5](#c15.xhtml#c15-fig-0005), the application is vulnerable. The XSS-Me Firefox Add-on ([`https://addons.mozilla.org/en-US/firefox/addon/xss-me`](https://addons.mozilla.org/en-US/firefox/addon/xss-me)) is a novel way to test for this vulnerability as well.

![ FIGURE 15-5:  Script code reflected to the browser.](images/9781119485476-fg1505.png)
