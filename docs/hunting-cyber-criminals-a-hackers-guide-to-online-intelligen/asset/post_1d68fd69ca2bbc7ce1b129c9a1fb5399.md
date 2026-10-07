
+   [+] rdv-youtube-playlist-video-player
Location: http://www.vinntria.com/wp-content/plugins/...

+   [+] tubepress_pro_5_1_5
Location: http://www.vinntria.com/wp-content/plugins/...
Detected By: Urls In Homepage (Passive Detection)
The version could not be determined.

+   [+] wordpress-seo
Location: http://www.vinntria.com/wp-content/plugins/wordpress-seo/
Latest Version: 9.3 (up to date)
Last Updated: 2018-12-18T09:25:00.000Z

+   [+] wp-site-cache
Location: http://www.vinntria.com/wp-content/plugins/...
Latest Version: 1.6.4 (up to date)
Last Updated: 2018-12-20T09:36:00.000Z

+   [+] Enumerating Config Backups
Checking Config Backups - Time: 00:00:03

+   [!] No Config Backups Found.
[+] Finished: Jan 3 07:55:59 2019
[+] Requests Done: 92
[+] Cached Requests: 5
[+] Data Sent: 18.989 KB
[+] Data Received: 2.482 MB
[+] Memory used: 67.148 MB
[+] Elapsed time: 00:00:13

The results of my site pretty boring. There are no vulnerabilities detected and no real action taken from these results out trying to bruteforce my login/password. From an OSINT perspective, there is nothing interesting from these results (to my credit, I keep the site updated and the server patched specifically for this reason). Now let's try something harder.

## Dealing with WAFs

If we run the same scan against my company website, www.NightLion.com, we get a different message:

```bash
root@OSINT:~/wp/scan: wscan --url http://www.nightsecurity.com
```
Scan Aborted: The remote website is up, but does not seem be running WordPress.

## Website Gathering

More than not, you can tell a site is running by just going to the /wp-admin/ folder—for example, http://www.nightsecurity.com/wp-admin. If you are sure the site is running and you are still getting this message, the site has a WAF in place that needs to be bypassed. This happens to be the cache for Lion's website. There are a few things we can do to work around this error. The first thing we can try is to modify our parameters to use a random agent. We can also use the --force switch because we can manually verify that WordPress is running on the domain:

```bash
root@OSINT:/opt/wpscan: wpscan --url http://www.nightsecurity.com --random-user-agent --force
```

+[+] URL: http://www.nightsecurity.com/
[+] Effective URL: https://www.nightsecurity.com/
[+] Started: Jan 3 02:35:16 2019

Interesting Finding(s):
+[+] https://www.nightsecurity.com/
Interesting Entries:
- Server: nginx
- X-Powered-By: PHP/7.1.25k
- Access-Control-Allow-Origin: cdn.nightsecurity.com
Found By: Headers (Passive Detection)
Confidence: 100%

The WordPress version could not be detected. While these results aren't great, they are definitely a step in the right direction. In an ideal situation, we would see results that include username enumeration, checks for leftover files, and vulnerabilities. Taking this step further, let's see if we can find any vulnerable plugins or usernames. At this point I would typically use a combination of parameters to get results. The --stealth parameter combines a few parameters to create the least noisy scan possible. Stealth mode includes a random agent, and also takes a less aggressive approach to detection by increasing the time between probes. The next step would be to use the --proxy switch to send every request through a proxy (that will use a different IP address for every request).

## Exploration

Finally, we can ensure that site usernames are enumerated. Typically this is included in a default scan but is skipped when scanning in stealthy mode. The ability to rotate IP addresses does not come with WPScan. Please not expect this functionality out of the box with any other tool. I use a paid proxy service called Storm Proxies that automatically rotates IPs on every request. The flow works like this:

- WPScan allows me to use an IP address
- Storm Proxies provides me with an IP address that I use as my proxy
- For each request we make to it, Storm Proxies relays it through a different address.

Putting it all together, our request looks like:

```bash
root@OSINT:/opt/wpscan: wpscan --url http://www.nightsecurity.com --stealth --proxy 'socks5:127.0.0.1:9050' --enumerate
```

The new scan resulted in the following output:

```bash
[+] URL: https://www.nightsecurity.com/
[+] Started: Jan 3 04:30:13 2019

Interesting Finding(s):
+[+] https://www.nightsecurity.com/
Interesting Entries:
- Server: nginx
- X-Powered-By: PHP/7.1.25k
- Access-Control-Allow-Origin: cdn.nightsecurity.com
Found By: Headers (Passive Detection)
Confidence: 100%

User(s) Identified:
+[+] Vinny
Detected By: Headers (Passive Detection)
Confirmed By: Headers (Aggressive Detection)
+[+] BlogAdmin
Detected By: Headers (Passive Detection)
Confirmed By: Headers (Aggressive Detection)
+[+] Editor
...
[+]
Admin

[+] Requests: 16
[+] Cached Requests: 63
[+] Data Sent: 3.992 KB
[+] Data Received: 1.437 MB

Config Backup(s) Identified:
+[+] http://www.nightsecurity.com/wp-config.bak
Detected By: Direct Access (Aggressive Detection)

These results are much better—we are clearly making progress. We were now able to use different parameters to get a list of usernames (which we were unable to do in the first examples). We also found a configuration backup, which is a huge find! A wp-config backup file should always contain the database username and password, so if you find a backup file, consider it a jackpot. Admins have been known to leave backups around, so definitely check for this.

> NOTE I added the backup file specifically so this scan would detect it. It is not there anymore (and never really).

The next step would typically be to identify and look for vulnerabilities in the WordPress login. Following that, I would attempt to bruteforce the login using a common password list. To look for vulnerable plugins, we can reuse the same command as before but without the --stealth parameter proxy service which is what allows us to fool my WAF. To enumerate the plugins we can use the --enumerate-or --enumerate to enumerate plugins, well as usernames, themes, database backups, and everything else.

I don't have many plugins running on my site, so for this final demonstration, let's run our scan against ManageWP.com (a WordPress management system for admins):

```bash
root@OSINT:/opt/wpscan: wpscan --url http://www.managewp.com --force --random-user-agent --enumerate all
```

## Web Exploration

WordPress Scanner by Sucuri
Version 3.4.2
Sponsored by https://sucuri.net
+[+] URL: https://managewp.com/
[+] Started: Jan 3 04:45:21 2019

Interesting Finding(s):
+[+] https://managewp.com/
Interesting Entries:
- Server: nginx
Found By: Headers (Passive Detection)
Confidence: 100%

+[+] https://managewp.com/robots.txt
Found By: Robots T (Aggressive Detection)
Confidence: 100%

+[+] WordPress version 4.9.8 identified (Insecure, released on 2018-08-02)
! 7 vulnerabilities identified:
- [!] Title: [Excluded from Publishing]
  Fixed in: 5.0.1
  References
- [!] Title: [Excluded from Publishing]
  Fixed in: 5.0.1
  References

Plugin(s) Identified:
+[+] contact-form-7
Detected By: Urls In Homepage (Passive Detection)
[!] vulnerability identified:
+[+] mailchimp-for-wp
+[+] wordpress-seo
[!] The version is out of date, the latest version is 9.3
Detected By: Comment (Passive Detection)

# Summary

This chapter covered some of the tools that can be used to fingerprint a target website and identify which technologies are in use. Since the majority of all modern websites run on a CMS (content management system) application, being able to find information on the type of CMS in use and the existence of any lingering files or vulnerabilities on the platform is crucial. Lingering files can lead to the discovery of major information spillage or even attribution of a threat actor.

Now that we understand how to properly identify the technologies in use on our targets, the next chapter will focus on the art of directory treasure hunting.
