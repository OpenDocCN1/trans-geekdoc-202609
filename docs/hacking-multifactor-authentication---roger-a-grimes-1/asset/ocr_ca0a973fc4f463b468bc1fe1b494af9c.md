# Chapter 7 Endpoint Attacks 171

+   2. It modifies the system that it can remain in memory or be re-executed by the computer is rebooted. This is known as persistence.

+   3. It checks running processes to see if any of the most popular Internet browsers (Google Chrome, Microsoft Internet Explorer, Microsoft Edge, Apple Safari, etc.) are installed and running.

+   4. It monitors the URL address to see if any one of the predefined URLs that indicate a bank or other targeted host system.

+   5. When the user connects to one of the predefined URLs, the bancos trojan monitors the session, waiting to confirm a successful login. Usually this involves simply detecting the web page (via its URL) that is displayed after a successful login.

+   6. The bancos trojan performs one of the malicious actions listed earlier.

Good examples of popular bank trojan can be found here: www.enigmasoftware.com/clientmaxx-removal and www.americanbank.com/news/the-dridex-threat-how-to-block-the-latest-malware-armed-at-banks.

Banking trojans mean their hacker gains millions of dollars. Figure 7.1 shows an example news report about a single banking trojan gang who stole over $100 million from more than 41,000 victims. That's from just one hacker. The king of all banking trojans is Zeus. It proved a generic bot trojan, which through sharing and code leaks, was used by many newer bancos trojans over the years, many of which bypass MFA. It even has its own Wikipedia page: en.wikipedia.org/wiki/Zeus_(malware).

![](bbox=[0.093, 0.555, 0.638, 0.695])

Figure 7.1: Example news report about a single banking trojan gang arrest

# Transaction Attacks

When trojans first came out, they were simply stealing the customer's login credentials or access control tokens and conducting their fraudulent transactions from another computer. The bank could not tell or not the transaction was from the legitimate user. So, the bank implemented SMS-based MFA, where the bank sent the user a one-time code via their phone that the user had to type in to confirm the transaction they wanted to complete.