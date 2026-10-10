
# False Positive vs. False Negative

When evaluating IDSs, be sure to verify the likelihood of false positives and false negatives with the product. Having an IDS that reports a high number of false statements is bad news because it means the IDS triggers alarms when it shouldn’t or doesn’t trigger alarms when it should. Know the following false results for the Security+ exam:

- **False positive** A false positive is when the IDS states there was suspicious activity (positive), but in reality, there was not (a false assumption). In simple terms, the IDS reports suspicious activity but none occurred.
- **False negative** A false negative is when the IDS does not see any suspicious activity, and again that was incorrect—there really was some! In simple terms, the IDS fails to detect suspicious activity that actually occurred and thus doesn’t report it.

# EXERCISE 8-2

![Images](video.jpg)

## Using Snort: A Network-Based IDS

In this exercise, you learn how to use Snort, a popular network-based intrusion detection system. Keep in mind that Snort is complicated software, and the goal here is to simply introduce you to an example of a network-based IDS.

1. Ensure that the Linux, Windows 10, and ServerA VMs are running.
2. Download and install Snort from the Internet onto the ServerA VM. After installing Snort, be sure to install WinPcap, which is the packet-sniffing driver used by Snort.
3. After installing WinPcap and Snort, launch a command prompt (be sure to run as administrator) and type the following:

![Image](p0351-01.jpg)

4. List three of the folders that you see there: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
5. To start Snort, go to the bin directory by typing `cd bin`.
6. To view the version of Snort you are using, type `snort -V`.
7. To view a list of network adapters that Snort can use, type `snort –W`. What interface number is your network card? \_\_\_\_\_\_

Notice in the following illustration that my network card has an index/interface number of 1 (in the index column):

![Image](f0352-01.jpg)

### Monitor Traffic with Snort

8. To use Snort to monitor traffic on the screen, type `snort –i# -v` (where # is your interface number) and press enter.
9. Go to one of the other virtual machines and create some traffic, such as FTP, HTTP, or Ping traffic.
10. Switch back to the ServerA VM and then press ctrl-c to stop Snort.
11. Review the output by scrolling to the top and navigating down.

![Image](f0352-02.jpg)

12. Can you see the traffic you created? \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Notice in the preceding illustration that I have a packet destined for port 80 on the 10.0.0.1 system that came from 10.0.0.5.

### Logging with Snort

13. Ensure you are on the ServerA VM.
14. At the command prompt, you will use Snort to capture the payload data (`-d`) and log traffic (`-l`) to the `snort\log` folder by typing

![Image](p0353-01.jpg)

where # is your network interface number.
15. Go to another VM and generate network traffic with Ping, FTP, or HTTP.
16. Switch back to ServerA and then press ctrl-c to stop Snort.
17. Through My Computer, navigate to `c:\snort\log`.
18. Do you see a subfolder for each IP address involved in network traffic? \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
19. Open each of the log files and view the details.

![Image](f0353-01.jpg)

### Rules with Snort

20. Ensure you are on the ServerA VM.
21. With Snort, you can program rules that are signatures of the types of traffic you wish to be notified of. Each rule starts with an action such as “alert,” indicating that you want Snort to store any traffic that matches the rule to an alert file. Then you have the protocol such as TCP, UDP, IP, or ICMP. Then you have the source IP and port address with an arrow pointing to the destination IP address and port number. Finally, in brackets you can specify options that are different fields in the headers you can look for. Start Notepad and type the following rules (watch for typos):

![Image](p0354-01.jpg)

22. The following outlines what each rule does:
- The first rule identifies any web traffic with the word “facebook” in it.
- The second rule watches for ICMP echo request messages.
- The third rule watches for the word “password” being transmitted to help identify any potential unencrypted passwords.
23. Save the file as `c:\snort\rules\lab.rules` and change the file type to “all files” while in the Save As dialog box.
24. To use the Snort rules, go to the snort folder at a command prompt and type

![Image](p0354-02.jpg)

25. Once Snort has started, go to another system and create some traffic such as Ping or FTP, and if you have Internet access in the VM, surf the Facebook site.
26. Go back to the ServerA VM and stop Snort with ctrl-c.
27. Open My Computer and navigate to the `c:\snort\log` folder.
28. Do you have an alert.ids file? \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
29. Open the alert.ids file and review the contents. You should see your Ping traffic and FTP traffic.

![Image](f0355-01.jpg)

![Images](job.jpg)

**Snort is a very powerful, open-source, network-based intrusion detection system well worth spending some time with. And it’s free! You can download it from [www.snort.org](http://www.snort.org).**

## Deception and Disruption

Another method of detecting intrusions is by using a bit of trickery to catch the attacker red-handed, collect information about them, and slow down their attack against production systems. You can use a combination of technologies such as honeypots, honeynets, and honeyfiles to capture the attention of the hacker to lure them into your trap!

### Honeypots and Honeynets

A `honeypot` is a system that is placed on the private network, or in a DMZ, and is designed to lure the hacker away from production systems and to the honeypot. The hacker spends time trying to hack into the honeypot, but all the while, you are logging the activity and having the host-based IDS installed on the honeypot send you notification of the hacker’s existence.

Most companies make the mistake of not securing the honeypot because they want the hacker to break into it, but if you make it too easy for the hacker to compromise the honeypot, the hacker may walk away, sensing a trap. It is critical that you challenge the hacker by hardening the honeypot and that you implement security controls to make the system appear as if it may have value.

Another common security term is `honeynet`, which is an entire network designed to appear as a production network but is solely there to lure the hacker away from the real production network.

### Honeyfiles

A `honeyfile` is a file you place on a system to get the hacker to open it. When the file is opened, you can have an alert sent out that informs you of this fact so that you are aware there is someone on the system. For example, you could place a file on the desktop called `passwords.txt` that tricks the attacker into thinking you have a file with all your passwords in it. When the hacker opens the file, an alert is sent out informing you that the file has been opened.

### DNS Sinkhole

A `DNS sinkhole` is when the DNS server responds with fake IP address information for known-malicious URLs or domain names. These fake IP addresses are sent to the clients so that the clients do not connect to known-malicious addresses.

### Fake Telemetry

`Telemetry` is data that is collected for monitoring purposes. Some applications allow you to generate fake telemetry data, which could be information about the infrastructure, servers, and clients. Fake telemetry data can be generated to test solutions that use telemetry data.

![Image](exam.jpg)

**For the Security+ certification exam, know deception and disruption techniques such as honeypots, honeyfiles, and DNS sinkholes. Remember that a text file on the desktop called `passwords.txt` is a classic example of a honeyfile.**
