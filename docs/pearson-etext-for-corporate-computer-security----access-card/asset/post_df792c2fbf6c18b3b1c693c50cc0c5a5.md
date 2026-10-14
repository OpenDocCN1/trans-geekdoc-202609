
![](img/073342643701cc54eb7875c41ab92ef2_411_0.png)

However, attackers learned that if they began with “../” in their path, some web-server programs would allow them to break out of the WWW root box and get to the directory above the WWW root. In operating systems, “..” means go up one level. To go down one level, the command gives the name of the directory. For instance, to go up one level and down to the etc directory, the path would be “../etc”.

Typing URLs with “..” in them can give access to sensitive directories, including the command prompt directory. This is the basic **directory traversal attack**. With directory traversal, the path ../etc/passwd would allow the attacker to download the passwd file in the etc directory (on a Unix computer).

## THE DIRECTORY TRAVERSAL WITH HEXADECIMAL CHARACTER ESCAPES

As usually happens, vendors responded with a patch that rejected HTTP request messages containing a series of two dots.

Attackers soon found a variant of the basic attack that would succeed against this countermeasure. For instance, IIS allows hexadecimal input, in which % is followed by two symbols between 0 and F. Each symbol represents four bits, so the two symbols together represent a byte.

Then attackers were sending HTTP directory traversal messages with two hexadecimal codes for dot. For a while, this **hexadecimal directory traversal attack** was successful. Then vendors issued a patch to stop it.

**Figure 8-14** Webserver Attacks (Study Figure)

**Figure 8-15** Directory Traversal

![](img/073342643701cc54eb7875c41ab92ef2_411_1.png)

## UNICODE DIRECTORY TRAVERSAL

This cat-and-mouse game continued. For instance, the UNICODE coding system can represent non-English languages. Each character in each language is assigned a code sequence. Some of these code strings in various languages represent dots. Soon, attackers used several UNICODE representations to get around the hex patches. In turn, vendors created a patch for UNICODE directory traversal attacks.

## Test Your Understanding

- 9. a. What is website defacement?
- b. Why is it damaging?
- c. In directory access commands and URLs, what does ".." represent?
- d. What are directory traversal attacks?
- e. Create a URL to retrieve the file aurigemma.htm under the rainbow directory on the host www.pukanui.com. The WWW root is three levels below the system’s true root directory and the rainbow directory, which is under the projects directory, which is directly under the root directory. (Hint: Draw a picture.)
- f. In what two ways have attackers circumvented filtering designed to stop directory traversal attacks?

## Patching the Webserver and E-commerce Software and Its Components

## E-COMMERCE SOFTWARE VULNERABILITIES

The webhosting company MindSpring suffered an embarrassment when it was found that its servers exposed the passwords of some of the websites they hosted. The problem was tracked to a single website that used a commercial e-commerce program and failed to register it. The website’s owners were not notified of an important patch because of the failure to register the product. Two years later, the vulnerable software was discovered by attackers.

- **Patching the WWW and E-commerce Software and Their Components**
- Patching the webserver software is not enough
- Also must patch e-commerce software
- E-commerce software might use third-party component software that must be patched

- **Other Website Protections**
- Website vulnerability assessment tools, such as Whisker
- Reading website error logs
- Placing a webserver-specific application proxy server in front of the web-server

- **Controlling Deployment (Figure 8-18)**
- Development server
- Testing server
  - Developers have no authorizations to use this server
- Production server
  - Developers have no authorizations to use this server
  - Testers have no authorizations to use this server

Figure 8-16 Webserver and E-commerce Protections (Study Figure)

The website was one of several websites running on a single Sun Solaris (UNIX) server at the webhosting company. That server was configured incorrectly, and the vulnerability in the single website ended up opening access to password files on other websites hosted at the same machine.

This example underscores the importance of patching commercial e-commerce server software (and of configuring shared machines properly). E-commerce software is complex and has many subsystems. It would be foolish to assume that vulnerabilities will never be found in a firm’s commercial e-commerce software. Much of this software runs as root, giving attackers open access to the entire server if they compromise the software components of WWW or e-commerce software.

Even when a webserver or e-commerce server produces clean code, some subsystems often are left open to attack by their vendors. Many webserver programs, for instance, support the OpenSSL library. A vulnerability named Heartbleed was disclosed in 2014 that allowed attackers to extract information from a website using the OpenSSL library. A year after disclosure nearly 74 percent of the top 2,000 largest companies had still not completely patched their systems. As of 2019, there were still 90,000 unpatched servers connected to the Internet.^8^

## Other Website Protections

**WEBSITE VULNERABILITY ASSESSMENT TOOLS** Several webserver-specific vulnerability assessment tools have been developed. Some of the more widely used website vulnerability assessment tools include Nikto, Paros Proxy, Acunetix, and IBM’s Rational AppScan. Running a vulnerability assessment tool against the website frequently should be viewed as normal maintenance.

**WEBSITE ERROR LOGS** In addition, websites usually log responses that contain error messages. Log reviews should be done frequently to look for signs of attacks. For instance, an excessive number of 500 error messages may indicate that an attacker is trying to send invalid data to the server.

In turn, an excessive number of 404 errors might indicate that an attacker is searching blindly for files on your website. The error log in Figure 8-17 shows an internal employee (10.10.10.10) blindly searching for directories (bolded) on an internal webserver (10.0.0.1). Responses are all **404 errors** indicating that the directory or file is not found. In this case, the employee is probably searching for plans about a new product that is going to be released.

| Date | Time | Client IP | Method | URI Stem (target) | Server Port | Server IP | HTTP Error |
|---|---|---|---|---|---|---|---|
| 3/25/2021 | 21:31:18 | 10.10.10.10 | GET | **/secret/index.htm** | 80 | 10.0.0.1 | 404 |
| 3/25/2021 | 21:31:24 | 10.10.10.10 | GET | **/secrets/index.htm** | 80 | 10.0.0.1 | 404 |
| 3/25/2021 | 21:31:29 | 10.10.10.10 | GET | **/hidden/index.htm** | 80 | 10.0.0.1 | 404 |
| 3/25/2021 | 21:31:32 | 10.10.10.10 | GET | **/topsecret/index.htm** | 80 | 10.0.0.1 | 404 |
| 3/25/2021 | 21:31:37 | 10.10.10.10 | GET | **/plans/index.htm** | 80 | 10.0.0.1 | 404 |
| 3/25/2021 | 21:31:40 | 10.10.10.10 | GET | **/newproducts/index.htm** | 80 | 10.0.0.1 | 404 |

**Figure 8-17** IIS Error Logs

^8^ Shodan keeps a running total of the number of sites vulnerable to Heartbleed at *www.shodan.io/report/0Weu7Zq47*.

Checking error logs allows systems administrators to see who is attacking their servers and what type of attack they might be using.

## WEBSERVER-SPECIFIC APPLICATION PROXY FIREWALLS

One protection is to use an application proxy firewall for a webserver. This firewall sits between the webserver and the rest of the network. It checks incoming request messages for signs of buffer overflow attacks and other problems. It also stops outgoing response messages that are inappropriate.

## Test Your Understanding

- 10.
- a. What software must be patched on an e-commerce server?
- b. What three other webserver protections are mentioned in the text?
- c. Where is an application proxy firewall placed relative to the webserver?

## Controlling Deployment

It is also critical to control the deployment of new server-side applications. As Figure 8-18 shows, firms with rigorous deployment policies use three types of servers: development servers, testing servers, and production servers.

## DEVELOPMENT SERVERS

Server-side programs should be created on development servers dedicated to that purpose. Developers need extensive permissions on these servers.

## TESTING SERVERS

After development, the program is moved to a testing server for testing. Developers should have no access permissions on this server. Only testers should have access permissions to make changes so that developers do not slip in backdoors and make last-minute changes. ("It's just a few lines of code.")

## PRODUCTION SERVERS

After a program has been fully tested on the staging server, it should be moved to the production server that will provide services to users.

## Figure 8-18 Development, Testing, and Production Servers

![](img/073342643701cc54eb7875c41ab92ef2_414_0.png)
