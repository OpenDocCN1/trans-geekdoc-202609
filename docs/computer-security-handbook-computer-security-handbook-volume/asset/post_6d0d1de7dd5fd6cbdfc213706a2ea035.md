
industrial spies to extract information which stymied the acquisition of China’s largest soft-drinks company.36

In April 2013, the U.S. Department of Homeland Security (DHS) warned “organizations that post a lot of business and personal information on public web pages and social media sites” not to do so. In October 2012, phishers harvested detailed information about employees from a public posting by an energy company listing attendees at a conference. In addition to spear-phishing attacks on named individuals, “Malicious emails that appeared to be from one of the attendees were sent to others on the list informing them of a change in the sender’s email address. Recipients were politely asked to click on an attached link that promptly took them to a site containing malware.”37

The APWG is a valuable repository of statistical information about phishing.38 Their report on phishing during the fourth quarter of 2013 includes the following findings (these are direct quotations formatted as bullet points with page references removed):

- Phishing attacks against online game players saw a massive increase, from 2.7 percent of all phishing attacks in Q3 to 14.7 percent in Q4.
- Financial services continued to be the most targeted industry sector in the fourth quarter of 2012, with payment services close behind.
- Online gaming credentials are valuable to certain criminals, who sell them on the black market. In-game items held in those accounts can also be sold by phishers for real-world cash. Victims can even have their real-life identities stolen.
- Attacks against social media doubled to 6 percent, up from 3 percent in the third quarter.
- During Q4, about 30 percent of personal computers worldwide were infected with malware.
- More than 57 percent of PCs in China may have been infected, while PCs in European nations were infected least often.
- Except for October 2012, the number of phishing sites declined every month from April 2012 through December 2012.
- April 2012 saw 63,253 unique phishing sites detected, falling to 45,628 in December 2012.
- The APWG received reports of 28,195 unique phishing sites in December. December’s total was 31 percent lower than the high of 40,621 reports in August 2009.
- Use of crimeware dipped slightly in this quarter from the previous, as did the use of data-stealing malware.
- The use of other malware has increased by a statistically significant amount from the previous quarter.39

## 20.5.3 Where Is the Threat?

Phishing appears at first to be a personal problem, a matter of consumer computer security rather than enterprise information security. Indeed, the federal agency charged with consumer protection, the FTC, has been active in educating consumers about the problem and the ways to avoid getting scammed by these messages.40 However, phishing is also a computer-based threat to the information and welfare of companies as well as a threat to e-commerce in general.

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_637_0.png)

in Virgil’s *Aeneid*, but the goal of Trojan code is the same as that of the original Trojan horse: Fool the defender of a protected place into granting access to outsiders. (See Section 15.3.2.17 for more on the origins of the name.)

Almost as soon as the Internet provided a way to distribute executable code, either as download links or email attachments, some people decided to exploit this ability to distribute their code without explicit permission. In other words, an innocent party might be tempted to download an apparently innocuous executable, which was actually something else. The person doing the downloading does so intentionally but is ignorant of the intentions of the person who crafted the Trojan code within the executable.

## 20.6.1 Classic and Recent Trojans

Despite the fact that the screens of today’s computers do not need saving, screensavers continue to be a source of Trojan code. Some users apparently find the promise of animated waterfalls and fish tanks hard to resist. This leads users to download screensavers that they encounter on Websites or open screensaver files that they receive in email. In Exhibit 20.4 you can see an example of one screensaver.

The creator of this Trojan screensaver, discovered in February 2007, was apparently unhappy with a file-sharing network popular in Japan and named Winny. When this screensaver is opened, the Trojan displays an image warning the computer operator not to use Winny. This tactic is reminiscent of some of the very earliest viruses, which sought to spread relatively innocuous messages rather than cause damage. In fact, code does not have to have a malicious intent to be considered a Trojan—it merely needs the intent to get installed without permission. Unfortunately, in this particular case, the Trojan does go on to destroy data by overwriting certain files (e.g., those with .txt and .jpg extensions).

Another example of a screensaver Trojan is the one reported to be circulating as an email attachment called bsaver.zip in July 2007. When the file within the ZIP attachment is opened, the system is infected with the Agent-FZB Trojan horse, which then drops two rootkits to evade detection by security software and to make the system accessible to unauthorized users. (See Chapter 15 in this *Handbook* for more on rootkits.) This screensaver was distributed by a spam campaign with message subject lines such as *Life is beautiful*, *Life will be better*, *Good summer*, and *help you*. The message text included phrases like “Good morning/evening, man! Really [sic] cool screensaver in your attachment!”

More recent reports about Trojans include the following cases and studies:

- The BackDoor.Wirenet.1 Trojan was identified in August 2012; the malware “is the first Trojan Horse program that works on the Mac OS X and Linux platforms that is ‘designed to steal passwords stored by a number of popular Internet applications.’”⁴¹
- The “PandaLabs Q1 Report” for 2013 found that “Trojans set a new record, causing nearly 80 percent of all computer infections worldwide. Despite their inability to replicate, Trojans are capable of triggering massive infections through compromised Web sites that exploit vulnerabilities in browser plug-ins like Java, Adobe Reader, etc. This attack method allows hackers to infect thousands of computers in just a few minutes with the same Trojan or different ones, as attackers have the ability to change the Trojan they use based on multiple parameters such as the victim’s location, the operating system used, etc.”⁴²
- In March 2013, Kaspersky Labs reported that a new spyware attack on Tibetan freedom activists used a Trojan designed for the Android mobile-phone operating system.⁴³
- The Flashback Trojan had infected more than 600,000 Macintosh computers by early April 2013 by exploiting a flaw in Java.⁴⁴
- In April 2013, criminals sent out invitations to watch video footage of the Boston Marathon bombings. A remote-access Trojan was installed as a “WinPcap Packet Driver (NPF)” to evade notice.⁴⁵
- In May 2013, Graham Cluley of Sophos reported on a Trojan (Mal/BredoZp-B) circulated in an email supposedly from Tiffany & Co. that claimed to include details of an export license and a payment invoice.⁴⁶

A Trojan tries to look useful or interesting so that users will install it, but buried within is unauthorized, undocumented code for unauthorized functions, just some of which are listed here:

- Deleting files or folders or entire drives
- Changing data, in subtle or dramatic ways
- Encrypting data (possibly for purposes of extortion)
- Copying data to other computers (possibly for purposes of industrial espionage)
- Downloading files without user consent (possibly for purposes of illicit e-commerce, illegal file sharing, pornography site hosting, cheap storage)
- Corrupting browser software and network files to redirect user from legitimate Websites to fake, bogus, malicious sites
- Enabling remote access to the compromised system (sometimes referred to as a RAT, for Remote Access Trojan), often used to turn computers into zombies that can be aggregated into botnets (for the purposes of spamming, phishing, and executing denial-of-service attacks)
- Aiding the spread of viruses using dropper code to cause infections
