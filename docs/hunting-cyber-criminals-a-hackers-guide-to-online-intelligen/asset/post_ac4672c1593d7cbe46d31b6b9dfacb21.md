
# Chapter 6 Website Information Gathering 131

as our input filename, specify an output file of output.txt, and use a custom user agent:

```
root@OSINT:/opt/CMSMap: python3 cmsmap -i targets.txt -o output.txt \
- "Mozilla/5.0 (Android 4.4; Mobile; rv:41.0) Gecko/41.0 Firefox/41.0"
```

An annoying part about scanning sites in batch is that if a CMS is detected with one of the sites, the script won't automatically move to the next site. So you have to force the CMS to a known type or just scan the sites at a time. The following output shows what happens if site detection:

```
[-] Date & Time: 01/01/2019 20:45:12
[L] Robots.txt http://www.nightlightsecurity.com/robots.txt
[ERROR] CMS detection failed :
[ERROR] Use -f to force CMSMap to scan (WordPress, (J) oomma or (D) rupal
```

## Detecting Vulnerabilities

An amazing feature of CMSMap is its ability to detect vulnerabilities within target sites. The following output was taken from a scan run with the exact parameters shown in the preceding code. We have to leave out the names of websites of the discovered vulnerabilities, but you can quickly see how powerful this tool is:

+   [I] Threads: 5
[-] Target: http://www.fakebank.com (52.37.170.23)
[M] Website Not in HTTP5: http://www.fakebank.com
[I] Server: Apache/2.4.10 (Debian)
[I] X-Frame-Options: Not Enforced (Debian)
[I] Strict-Transport-Security: Not Enforced
[I] X-Content-Security-Policy: Not Enforced
[I] X-Content-Type-Options: Not Enforced
[I] Robots.txt http://www.fakebank.com/robots.txt
[I] CMS Detection: WordPress
[I] WordPress Version: 4.8.8

+   [M] EDB-ID: 44994 "WordPress Core < 4.9.6 - (Authenticated Arbitrary File Deletion"
[I] WordPress Theme: Avada
[M] EDB-ID: 34511 Multiple WordPress Themes 'admin-ajax.php?img" Arbitrary File Download"
[-] WordPress usernames identified:
[M] [omitted]
[M] [omitted]
[M] [omitted]

## Part II Web Exploration

[M] [omitted]
[M] [omitted]
[M] [omitted]
[M] [omitted]
[M] [omitted]
[M] [omitted]
[M] XML-RPC services are enabled
[M] Website vulnerable to XML-RPC Brute-Force Vulnerability
[I] Autocomplete Off Not Found: http://www.fakebank.com/wp-login.php

+   - Default Wordpress Files:
[I] http://www.fakebank.com/license.txt
[I] http://www.fakebank.com/readme.html
- Searching WordPress Plugins ...
[I] google-analytics-for-wordpress v6.2.6
[I] revslider
[I] akismet

+   [M] EDB-ID: 37826 "WordPress 3.4.2 - Multiple Path Disclosure Vulnerabilities"
[M] EDB-ID: 37902 "WordPress Plugin Akismet - Multiple Cross-Site Scripting Vulnerabilities"

+   [I] fusion-core
[I] fusion-builder
[I] feed

+   [M] EDB-ID: 38624 "WordPress Plugin WP Feed - 'nid' SQL Injection"
[I] Checking for Directory Listing Enabled ...
Checking for Directory Listing Enabled ...
- Date & Time: 01/01/2019 21:00:26
- Completed in: 0:04:58

In detecting vulnerabilities, CMSMap can enumerate what themes or plugins are on a site, and even brute CMS systems using a username and password file. It is an incredibly powerful middle-tier tool—it has enough features without feeling overly complex and advanced. Let's move on to our third and final tool, WPScan.

## WPScan

WPScan is a black box information gathering tool and vulnerability scanner for WordPress. In opinion, it is by far the best marker. NOTE WPScan is available at https://wpscan.org.

Right now you may be thinking: Why do I need another scanner? The answer is depends on how deep and thorough you want to get. CMSMap is focused on providing similar functionality to CMS systems, whereas WPScan provides advanced features on scanning WordPress sites which may be 80% of what you need in the end. Avoiding detection can be tricky, especially when facing modern WAFs. WPScan allows you to use proxies and has built-in stealth mode that will rotate user agents on every request. Here are some of the most important parameters that we will be discussing:

-v, --verbose (Verbose mode)
-o, --output FILE
-f, --format FORMAT (Output results in specified format)
--detection-mode MODE (Default: mixed, passive, aggressive)
--user-agent, --value UA
--random-user-agent, --ua
--http-auth login:password
--max-threads VALUE (Max threads to use)
--request-timeout SECDS (Milliseconds to wait between each request)
--connect-timeout SECDS (The connection timeout in seconds)
--disable-tls-checks (Disabled SSL/TLS verification)
--proxy/protocol://port
--proxy-auth login:password
--cookie-string COOKIE (Cookie string to use in requests)
--cookie FILE (File to read and write cookies. Default: /tmp/wpscan/cookie_jar)
Assume WordPress is running
--force
--wp-content-dir
--wp-plugins-dir
-e, --enumerate OPTS (to enumerate vulnerable plugins, all plugins, themes, config backups, media ids, and all)
-P, --passwords FILE (Passwords to use during attack)
-U, --usernames LIST (Usernames to use during attack)
--multicall-max-passwords Maximum number of passwords to send by request with XMLRPC multicall
--password-attack ATTACK Force the supplied attack to be used rather than automatically determining one
--stealthy Force stealth/passive mode

Out of the box, WPSCAN will automatically enumerate plugins on the site, check for vulnerabilities of these plugins, and look for important files like config backups. After running the tool with no parameters other than a URL against my personal site, we can already see a considerable difference in the output generated between WPSCAN and other plugins. The following is a condensed version of the results:

```
root@OSINT:/opt/wpscan: wpscan --url http://www.vinnytroia.com
```

![](img/ceaab52f5a94b18995b8efe8975871_155_0.png)

WordPress Security Scanner by the WPSCAN Team
Version 3.4.2
Sponsored by Sucuri : https://sucuri.net
@WPSScan_, @ethicalhacklr, @serwan_lr, @FirePart_

+   [+] URL: http://www.vinnytroia.com/
[+] Started: Thu Jan 3 07:55:46 2019

Interesting Finding(s):

+   [+] http://www.vinnytroia.com/
| Interesting Entries:
| Server: nginx |
| X-Powered-By: PHP/7.1.25, Plesk |
| Access-Control-Allow: * |
| Access-Control-Credentials: true |
| Access-Control-Allow-Headers: Content-Type, Accept |
| Access-Control-Allow-Methods: GET, POST, OPTIONS, PUT, DELETE |
| Found By: Headers (Passive Detection) |
| Confidence: 100%

+   [+] http://www.vinnytroia.com/robots.txt
| Found By: Robots TX (Aggressive Detection)

[+] Confidence: 100% http://www.vinnytroia.com/xmlrpc.php
| Found By: Direct Access (Aggressive Detection)
| Confidence: 100%

[+] http://www.vinnytroia.com/readme.html
| Found By: Direct Access (Aggressive Detection)
| Confidence: 100%

[+] WordPress version 5.0.2 identified (Latest, released on 2018-12-19).
| Detected By: RSS Generator (Passive Detection) |
| - http://www.vinnytroia.com/feed/

[+] WordPress theme used in: jupyter-child
| Location: http://www.vinnytroia.com/wp-content/jupyter-child/
| Style URL: http://www.vinnytroia.com/wp-content/themes/jupiter-child/style.css?ver=5.0.2
| Style Name: Jupiter Child Theme
| Style URL: http://themeforest.net/user/artbees
| Description: Child theme for the Jupiter theme...
| Author: Your name here

[+] Enumerating All Plugins
+] Checking Plugin Versions

[i] Plugin(s) Identified:

[+] contact-form-7

[+] google-analytics-for-wordpress

[+] gravityforms
| Location: http://www.vinnytroia.com/wp-content/plugins/gravityforms/
| Detected By: Urls In Inpage (Passive Detection)
| Version: 2.4.4.1 (100% confidence)

[+] js_composer

[+] js_composer_theme
| Location: http://www.vinnytroia.com/wp-content/plugins/...

[+] kiwi-logo-carousel
| Location: http://www.vinnytroia.com/wp-content/plugins/...

[+] mastersl
| Location: http://www.vinnytroia.com/wp-content/plugins/mastersider/
