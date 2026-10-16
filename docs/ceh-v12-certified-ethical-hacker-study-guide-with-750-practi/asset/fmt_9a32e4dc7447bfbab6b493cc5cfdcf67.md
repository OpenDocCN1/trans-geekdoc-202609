
# A08:2021 Software and Data Integrity Failures

A08:2021 Software and Data Integrity Failures—This may be more commonly thought of as software supply chain failures, since it includes failures in code verification, as well as issues related to build pipelines that could result in the build tools creating malicious output. Any code or infrastructure that doesn't protect against integrity failures would fall into this category.

# A09:2021 Security Logging and Monitoring Failures

A09:2021 Security Logging and Monitoring Failures—Security logging is not always considered when applications are developed. Worse, operations teams may not be monitoring any logs that exist. Logs can be used to detect exploitations of some of the previously identified vulnerabilities.

# A10:2021 Server‑Side Request Forgery

A10:2021 Server‑Side Request Forgery—This was added to the list as a result of a request by the community and is a problem that occurs when the web application does not validate a user‑provided URL. This may cause the application to send requests to unexpected destinations, which would allow the attacker to bypass other protections like firewalls or access control lists.

While there are a lot of remediations that cover all of these vulnerabilities, appropriate design and input validation result in a good start. The following are some examples of the different vulnerabilities identified by OWASP.

## XML External Entity Processing

The XML external entity attack now falls under the category of security misconfiguration, though it was previously its own vulnerability. This is an attack that allows an attacker to manipulate data being sent to the server to get results not expected or otherwise allowed by the application.

A data model may be a complex set of data where multiple pieces of data are related and need to be organized together. This is very different than just passing a string from a web page to a web server. It may be passing multiple strings, a few integers, and also some organizing information. One way of organizing the data is to use the Extensible Markup Language (XML). XML allows you to put all related data together into a single data structure, complete with the organizing information indicating what each piece is. A common way to pass data back and forth between a client and a server is to use XML to structure the data and transmit that XML.

As you will see with other web application attack types, an XML entity injection attack comes from code on the web server accepting data that comes from the client without doing any data validation. This means programmers have not written any sort of check on the data when it enters the application. Even if it’s script code in the page contents that is rendering the data, it’s still possible for a user to tamper with it or even generate a data transmission to send to the server. As a result, any data coming from the user should never be trusted. As a general rule, data passed into a function from the outside should not be trusted because there is no guarantee the normal control flow of the program hasn’t been tampered with. When programmers don’t do any checking of the data, bad data can slip into the program and alter the expected behavior.

An example of an XML package that could allow the attacker to gain access to system files is shown in the following code listing. The XML refers to an external entity from the system. In this case, it’s a file. The attacker is requesting that the contents of the file `/etc/passwd` be delivered back to the view.

### XML External Entity Processing Example

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<!DOCTYPE wubble [
<!ELEMENT wubble ANY>
<!ENTITY xxe SYSTEM "file:///etc/passwd"  >]><wubble>&xxe;</wubble>
```

This may not necessarily seem like a big deal. However, in some cases, you can get the application server to do some of your work for you. Let’s say you want to know whether an internal web server (e.g., one you, as the attacker, can’t access because of firewall rules) is running. One way of doing this is to have the application server initiate a request by passing a URL into the system tag. This would have the application server make a call to the system with a URL, which the system would interpret as a request to pull the page indicated. Here you can see an example of XML that would allow this to happen.

### XML Request for Internal Page

```
<?xml version="1.0"?>
<!DOCTYPE GVI [<!ENTITY xxe SYSTEM "https://172.30.42.25:8443">]>

```

Of course, doing this sort of resource checking, or port scanning if you will, is not the only thing you can do with this approach. The best way to prevent against this sort of attack is to do input validation. Input validation should be done on the server side. You can do input validation on the client side, but expect that it will be bypassed. It’s easy enough to use an intercepting proxy or even an in‑browser tool to capture requests and modify them before sending them off to the server.

In examples such as this, simply not allowing any XML to use the external entity SYSTEM is a start toward protecting against this attack being successful. Any action the application has to perform through the system should be done directly by the application after it has parsed the data. Going a step further, evaluating if there is a way around the use of any external entity would be useful. Again, any external need should probably be handled directly by the application code after it has properly evaluated any data. This means all the external entities could be ignored when parsing the XML.

An external entity XML attack targets the server. This could be the web server or the application server, depending on who handles parsing the XML.

## Cross‑Site Scripting

A cross‑site scripting (XSS) attack is one that uses the web server to attack the client side. This is an injection attack, according to the OWASP Top 10. This injects a code fragment from a scripting language into an input field to have that code executed within the browser of a user visiting a site. There are three ways to run a cross‑site scripting attack. They all target the user. The difference is whether the script is stored somewhere or not. The first type, stored on the server and displayed for any user visiting a page, is called *persistent cross‑site scripting*. The second is called *reflected cross‑site scripting*. The last makes use of the Document Object Model (DOM).

All three types make use of a scripting language in the same way. The attacker would use a short script inside a `<script></script>` block. For example, the attacker may inject `<script>alert(‘wubble’);</script>` into an input field. With persistent cross‑site scripting, this would be a field where the value is stored on the server. A classic example of this sort of attack is a web forum where a user may be asked for a name, an email address, and then a comment. All of the values from these fields in the web form would be stored. When someone came back to the forum, the information would be displayed, including the script, which would be run by the browser. In the case of the previous example, an alert dialog box would be displayed with the word *wubble* in it.

When it comes to a reflected attack, the script isn’t stored. Instead, it is included in a URL you would send to a victim. This sort of URL would look like this, and you can see the script passed in as a parameter:

```
http://www.badsite.com/foo.php?param=<script>alert(5000);</script>
```

You would send this URL to a victim and do something to get them to click it, such as something like saying Apple is giving away free iPhones to the first 1,000 people to click this link. Then you’d make the link refer to the preceding URL. You can do this in an HTML email using the following HTML tag:

```
<a href="http://www.badsite.com/foo.php?param=<script>alert(5000);</script"></a>
```
