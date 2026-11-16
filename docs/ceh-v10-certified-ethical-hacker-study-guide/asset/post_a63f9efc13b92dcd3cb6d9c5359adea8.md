
You'll notice that only one of the systems shows headers, and out of those headers, there isn't a server type. The same server suggests that there is a redirect to a login page. Running the same scan with nmap returns server types. masscan doesn't have the same capabilities as nmap, including a lack of support for additional scan types, such as the unexpected TCP scans like XMAS, FIN, and ACK. It also doesn't support UDP scans. However, if you want all that functionality, you can use nmap. It's free and more than capable for those sorts of scans. What masscan gets you is the ability to indicate what rate you want to scan at and the ability to perform very fast scans.

## MegaPing

We've looked at MegaPing before for its capability to perform ping sweeps. As noted earlier, MegaPing has a number of capabilities, including the ability to run port scans. These are not just run-of-the-mill scans, however. You'll remember that nmap scans about 1,000 ports by default. These are commonly used ports. You can certainly select other ports if you want. One thing MegaPing provides us with that we don't get with nmap is some preselected port collections. You can see the drop-down in Figure 5.5 that provides you with different selections for ports. One of these is Hostile Ports, which are ports that are commonly misused as well as ports that may commonly be used by Trojan horse programs and other malicious software (malware). At the bottom, you will see the list of ports that are included in the scan type.

FIGURE 5.5 MegaPing scan types

![](img/421171b17a0c0dfae0aacde15d9831c1_189_0.png)

In order to run a scan in MegaPing, you select Port Scanner on the left side of the interface. Then you need to add in your targets for your scan. One downside to MegaPing is that it doesn't accept a CIDR block as a target. It also doesn't accept a range of addresses. If you want to scan multiple IP addresses, you need to add them in. You'll see the box in the middle where you can add the addresses and then select the ones you want to scan. If you just want to scan a single address, you enter it into the box below Destination Address List. Then you just click Start. Figure 5.6 shows the results of a scan of hostile ports.

FIGURE 5.6 MegaPing scan reports

![](img/421171b17a0c0dfae0aacde15d9831c1_190_0.png)

One thing you may notice when you look at the results is that there are common ports listed as being open. You'll see in the note alongside ports like 80 (www) is that they are elevated ports. These are ports that have to be opened with administrative privileges. This means the ports will be targeted by attackers because compromising the application behind the port will immediately give the attacker administrative privileges. Another scan type is Authorized Ports, which will scan just the range of ports where applications are expected to reside. Other ports are considered to be ephemeral, meaning they are assigned to client applications as source ports when they start a conversation with a server.

> One thing to note about MegaPing is that, while it has a load of functionality, it is commercial software. There is a fully functional evaluation version, but it does require you to wait while the license message shows when you start up the application.

## Vulnerability Scanning

Knowing open ports and even applications that are listening on those ports is a good start. You can then start hunting and pecking at those ports after doing a lot of research about what vulnerabilities may exist within those applications. You could also just find a lot of exploits and start throwing them at the applications on the open ports. This may be a simple way of checking to see if there are vulnerabilities. You just check all of the exploits you can find against your target. There are a few issues with that approach, however. The first is that you may end up causing failures on your target systems where you may not mean to. Blind testing can lead to unexpected results, and one of your objectives, from an ethical standpoint, is to cause no harm.

Certainly security testing of any type can lead to unexpected results and failures. However, your job is to control it as best you can and to ensure that your client or employer is aware of the possible ramifications of your testing. It wouldn't be very professional to tell your client that you're just going to throw a lot of exploits at their system without any idea what the impact would be and that they may experience outages as a result. Your job is to control your testing—to be knowledgeable about what you are doing and what the possible outcomes are.

Another issue is that if you are engaged in a red team test where the target has no idea you are running attacks, you want to be sure they don't detect you, or at least you want to do everything you can to avoid detection. Blindly running a lot of exploits against a lot of systems, including systems that may not even have the application that's vulnerable, is going to be noisy, and if there is any detection capability, you will be caught. That means you will have failed.

A better approach is to use a vulnerability scanner, which takes an intelligent approach to identifying potential vulnerabilities. A vulnerability scanner will identify open ports and listening applications, then determine what vulnerabilities may be possible based on those applications. The scanner will then run tests that have been defined for those vulnerabilities. The objective of a scanner is not to compromise a system, it is just to identify potential vulnerabilities.

This does not guarantee that what the scanner has identified is an exploitable vulnerability. It means that the scanner has found something it believes is a vulnerability based on interactions with the target system as compared with data the vulnerability scanner has. This is called a false positive. Any issue found by a vulnerability scanner needs to be verified manually. This may include investigating the actual interaction as presented by the scanner—sometimes it's based on return codes without looking at the actual data, for instance. It may also involve actually redoing the test performed by the vulnerability scanner. The vulnerability scanner is a tool and shouldn't be considered to be the end of your testing. It's the starting point. In spite of how good vulnerability scanners are, they are not the terminus.

> **Note**
>
> These are the four categories of vulnerabilities:
>
> - **False Positive**: The scanner has identified something it believes to be a vulnerability. After investigation, it turns out it's not really a vulnerability.
> - **False Negative**: The scanner has not identified a vulnerability. It later turns out that there was a vulnerability that the scanner missed.
> - **True Positive**: The scanner has identified a vulnerability that, after manual investigation, turns out to be a legitimate vulnerability.
> - **True Negative**: The scanner has not identified a vulnerability and there is not a vulnerability to identify.

For a historical perspective, it’s worth noting that network vulnerability scanners have been around since the early 1990s. The first one, developed by Dan Farmer and Wietse Venema, was known as Security Analysis Tool for Auditing Networks (SATAN). SATAN then spawned additional tools like Security Auditors Research Assistant (SARA) and Security Administrator’s Integrated Network Tool (SAINT). SATAN was written primarily in Perl and used a web interface. While Perl has been replaced by other languages for modern vulnerability scanners, they do generally use web interfaces. One of the vulnerability scanners that became very popular is Nessus. We’ll take a look at Nessus shortly, but we’ll start with OpenVAS, which is related to Nessus.

> I had tried to grab a copy of SATAN just to run it again for fun, since I last ran it 30 or so years ago. While the SATAN web page is still available, none of the mirrors that once had it are available. However, you can still get a copy of SARA, which hasn’t been updated in years, and SAINT, which is now a commercial product.

## OpenVAS

SATAN was open-source, meaning you could look at everything SATAN was doing and, if you felt like it, extend its functionality by adding in modules yourself. If you could find a copy of SATAN somewhere, you would still be able to look at the source code. Another open-source vulnerability scanner in the early 2000s was Nessus. It was initially released in 1998 as a freely available vulnerability scanner and remained so until 2005 when the company, formed three years before, closed the source code, making all future development proprietary to the company. At that point, the existing Nessus source was version 2 and the first version from Tenable was version 3. The existing source code for version 2 was open, however, and two separate projects were created, where the Nessus code for version 2, abandoned by the Nessus developers, was forked to create a basis for the new projects.
