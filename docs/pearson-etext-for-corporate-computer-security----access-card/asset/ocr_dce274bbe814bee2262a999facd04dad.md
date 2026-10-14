Onion routing can provide anonymity via an encrypted network of “relay” servers. Computers around the world pass your fully encrypted traffic. The intermediary relay servers do not know the entire path of the onion network. Requests that come from you appear to originate from around the world. You have complete anonymity. It’s still a good idea to use a secured end-to-end HTTPS connection because the connection between the last relay server and the site you are visiting is not encrypted.

+   1. Open a web browser.
+   2. Go to www.google.com.
+   3. Search for “my IP address.”
+   4. Press Enter.
+   5. Click on the first result.
+   6. Take a screenshot showing your IP address.
+   7. Go to www.TorProject.org.
+   8. Click Download Tor Browser.
+   9. Click on the link for Windows 10 under Tor Browser Bundle.
+   10. Save the file in your download folder.
+   11. Browse to your download folder.

+   12. Right-click the Tor executable and select “run as administrator.”
+   13. Complete the installation process and start the Tor Browser. (If the Tor browser doesn’t automatically start, you can search for “Tor Browser” in the Windows Search menu.)
+   14. Within the web browser, go to www.Google.com.
+   15. Search for “my IP address.”
+   16. Click on the first result. (If you get a warning about an “Untrusted” connection, just click I Understand the Risks, Add Exception, and Confirm Security Exception.)
+   17. Take a screenshot showing the new IP address. (This is someone else’s IP address.)
+   18. Start Microsoft Edge. (Arrange the windows so that the Tor browser and Microsoft Edge are both visible on your desktop.)
+   19. Search for “my IP address.”
+   20. Click on the first result.
+   21. Take a screenshot of your desktop (Ctrl-PrintScreen) showing the IP address results in both web browsers. (Use the results from the same website. Each browser should show a different IP address.)

# Project Thought Questions

+   1. What are channels? Would one be better than another?
+   2. Why is WEP considered cryptographically weak?
+   3. What is the difference between WPA and WPA2?
+   4. Why do some networks run at 11 Mbps and others at 54 Mbps?
+   5. Why would someone want to use a Tor network?
+   6. What do relay servers do in a Tor network?
+   7. How do Tor networks provide anonymity?
+   8. Why is it still important to use an HTTPS connection if you are using a Tor network?

# Case Study

# Apt1

Spamhaus is a nonprofit organization that tries to reduce spam by distributing blocking lists of IP addresses associated with known offenders. It has more than 70 servers in 18 countries that serve blocking lists to ISPs, corporations, universities, governments, and military networks.²² Spamhaus protects more than 1.7 billion mailboxes free of charge.

In early 2013, Spamhaus and their content delivery firm CloudFlare were hit by the largest DDoS attack known to

date.²³ At one point, Spamhaus’s site was receiving 300 Gbps as the result of a reflected DNS attack using more than 30,000 Open DNS resolvers. Attackers were able to use Open DNS servers to amplify their DDoS attack. CloudFlare explained it this way:

> “In the Spamhaus case, the attacker was sending requests for the DNS zone file for ripe.net to open DNS resolvers. The attacker spoofed the CloudFlare IPs we’d issued for Spamhaus”