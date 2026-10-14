The website was one of several websites running on a single Sun Solaris (UNIX) server at the webhosting company. That server was configured incorrectly, and the vulnerability in the single website ended up opening access to password files on other websites hosted at the same machine.

This example underscores the importance of patching commercial e-commerce server software (and of configuring shared machines properly). E-commerce software is complex and has many subsystems. It would be foolish to assume that vulnerabilities will never be found in a firm’s commercial e-commerce software. Much of this software runs as root, giving attackers open access to the entire server if they compromise the software components of WWW or e-commerce software.

Even when a webserver or e-commerce server produces clean code, some subsystems often are left open to attack by their vendors. Many webserver programs, for instance, support the OpenSSL library. A vulnerability named Heartbleed was disclosed in 2014 that allowed attackers to extract information from a website using the OpenSSL library. A year after disclosure nearly 74 percent of the top 2,000 largest companies had still not completely patched their systems. As of 2019, there were still 90,000 unpatched servers connected to the Internet.^8^

# Other Website Protections

**WEBSITE VULNERABILITY ASSESSMENT TOOLS**  Several webserver-specific vulnerability assessment tools have been developed. Some of the more widely used website vulnerability assessment tools include Nikto, Paros Proxy, Acunetix, and IBM’s Rational AppScan. Running a vulnerability assessment tool against the website frequently should be viewed as normal maintenance.

**WEBSITE ERROR LOGS**  In addition, websites usually log responses that contain error messages. Log reviews should be done frequently to look for signs of attacks. For instance, an excessive number of 500 error messages may indicate that an attacker is trying to send invalid data to the server.

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