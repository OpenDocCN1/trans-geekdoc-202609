# External

This section involves scanning activities that are done remotely from the organization. You don’t need to be onsite.

# Passive Scanning

Next, we begin with passive scanning. Use netcraft.com, shodan.io, builtwith.com, and archive.org to learn as much as you can about the technology the company uses. Pay particular attention to shodan.io. It can be very informative. Document all the details you find for the web server (builtwith.com and netcraft.com) as well as any vulnerabilities identified by shodan.io.

Now it is time to search the web for this company name. Check LinkedIn, Twitter, and Facebook. You may wish to use Maltego on company phone numbers, URLs, and email addresses. This can give you an indication of any connected entities (individuals or companies) as well as any information about the company that is out in the public. It is also a good time to use cyberthreat intelligence websites such as threatcrowd.org.

This is also the appropriate phase to research known vulnerabilities for the operating systems used in this network. We know they have Ubuntu Linux and Windows Server 2016. Search the web using Google, threatpost.com, https://cve.mitre.org/, and others.

# Active Scanning

We now begin actively scanning the public facing portions of the target network. That will begin with using tools like Nmap to scan the gateway router and the web server. Note any open services and ports. If the company uses Wi-Fi, attempt to connect to the WAP using default passwords.

This is also when we run external vulnerability scans. You should run two different scanners on the web server. I recommend Vega and OWASP ZAP, but you can use any two you like.

This is also an appropriate place to utilize the Metasploit scans you learned in Chapter 13, “Introduction to Metasploit.” There are SSL, anonymous FTP, SQL Server, and other scans. Run these on any public facing device to determine if any services are exposed to the outside world, and if said services are exploitable.

# Actual Breaching

Now it is time to try actually breaching each of the external facing interfaces. We will start with the web server. Take each vulnerability you have discovered and attempt to breach them with multiple techniques. Assume the server is vulnerable to SQL Injection. You would then:

+   1. Attempt to manually use SQL Injection
+   2. Use a tool such as Burp Suite to attempt SQL Injection

Do both manual and semi-automated attacks on all identified vulnerabilities.

Now we repeat that process for the gateway router. We first attempt logging into it, guessing passwords, etc. Try a variety of techniques to gain access to the router and document the results.