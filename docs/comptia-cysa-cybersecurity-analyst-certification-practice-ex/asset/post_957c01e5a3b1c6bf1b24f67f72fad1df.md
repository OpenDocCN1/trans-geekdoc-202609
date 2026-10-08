
# D. Introduction of new accounts

10. In regard to stopping unauthorized software from being installed on a system, which approach is the most effective?

-   A. Software blacklisting
-   B. Standardized desktop images and privileges
-   C. Software whitelist
-   D. Host-based intrusion detection and antivirus

11. An application is experiencing apparent memory issues. The symptoms are fairly straightforward, resulting in the application terminating. Occasionally an error pop-up appears with a vague message about a buffer address. From what you see, what is the next course of action?

-   A. Perform a memory dump
-   B. Back up the disk
-   C. Ensure drivers are up to date
-   D. Capture a packet sample

12. After recovering from an incident, a company decides to invest in a data loss prevention (DLP) solution as well as printers to subtly watermark documents from workstations. What do you think was the host-related issue the company experienced during the incident?

-   A. Unauthorized privileges
-   B. Service interruption
-   C. Unusual traffic spikes
-   D. Data exfiltration

13. A new file server is available to employees. The server’s capacity is expected to be sufficient for three years. Within two weeks, users complain the file server isn’t as responsive as it used to be. What’s more, a file called MB2TB.exe has been spotted in every folder. What might be a likely issue?

-   A. Bandwidth consumption
-   B. Processor consumption
-   C. Drive capacity consumption
-   D. Memory consumption

14. A user has raised a support ticket because of an unexpected dialog box on his Windows 10 laptop. He wasn’t concerned at first, because the pop-up seems like a legitimate Windows prompt, as seen in Figure 10-3. However, the user cannot understand why the pop-up appears, given there seems no connection to his actions. Treating this as an incident, where would you investigate further?

-   A. User account “Randy.”
-   B. Admin account.
-   C. Application’s publisher.
-   D. This is not an incident but rather a legitimate User Access Control prompt.

![](img/912de63e2fcf2d66d271d898c9165f4e_241_0.png)

Figure 10-3 User Access Control dialog box

15. A contractor has borrowed an older company laptop and has been using it with no issues for months. Recently the contractor came in, asking for a new laptop because he is “acting weird.” When asked for specifics, the contractor mentioned his application sometimes freezes, the browser goes to different websites, and other strange things start happening. What might be the best course of action?

-   A. Ensure the OS and applications are patched.
-   B. Increase the size of the hard drive; add more memory.
-   C. Create the contractor a new account.
-   D. Back up his data and perform a fresh, updated system install.

16. A security team member alerts you that a new domain account has been created, but there is no documented account request. Further, there is no legitimate way the account could be created without you or the team member’s assistance. In fact, a quick look shows you the new user account has a session activity now on a local host. What is your first step?

-   A. Fire the team member.
-   B. Log off the user session.
-   C. Isolate the host.
-   D. Reset the account password.

17. An important file that lists numerous bank accounts is tightly controlled, including a process for making any changes to that file. Although the file has no documented changes made in months, an analyst has determined its hashed value was changed between yesterday and last week. What would cause a different hash?

-   A. New account added
-   B. Unauthorized changes made
-   C. Different hash generator used
-   D. Drive capacity increased

# QUICK ANSWER KEY

-   1. B
-   2. B
-   3. D
-   4. A, B
-   5. B
-   6. A
-   7. C
-   8. C
-   9. A
-   10. C
-   11. A
-   12. D
-   13. C
-   14. A
-   15. D
-   16. D
-   17. B

# IN-DEPTH ANSWERS

-   1. Which of the following bandwidth-consumption behaviors strongly indicates something suspicious?
   A. Higher-than-normal bandwidth, every day, at the same time
   B. Higher-than-normal bandwidth once, during off-peak hours
   C. Lower-than-normal bandwidth used during peak hours
   D. Higher-than-normal bandwidth used during peak hours

B is correct. A single instance of higher-than-normal bandwidth consumption outside the "work day" is the most suspect. However, although it doesn't necessarily guarantee suspicious behavior, such bandwidth consumption is worth investigating further.
A, C, and D are incorrect. A is incorrect if such higher bandwidth consumption is happening every day, then that becomes the new normal. Investigating further is prudent but unlikely necessary. C is incorrect because lower-than-normal bandwidth could point to other issues, such as network disruption. D is incorrect because higher bandwidth consumption during the work day is not necessarily abnormal.

-   2. Your SIEM alerts you to to an unusual amount of ARP queries. This is indicative of what sort of behavior?

-   A. Rogue device on the network
-   B. Scan sweeps
-   C. Unauthorized privileges
-   D. Unauthorized software
-   ☑ B is correct. A spike in ARP queries would indicate someone or some process is conducting a scan. This would warrant additional action and investigation.
-   ☑ A, C, and D are incorrect. The ARP queries indicate a scan, which may or may not be originating from a rogue device, unauthorized software, or unauthorized privileges.

-   3. What is a property of network usage that suggests a rogue device on the network?

-   A. Repeated failed remote logins
-   B. Beaconing
-   C. Failed connection attempts on the legitimate wireless access points
-   D. Unrecognized MAC addresses logged on legitimate access points
-   ☑ D is correct. Unrecognized MAC addresses indicate unrecognized or unauthorized devices.
-   ☑ A, B, and C are incorrect. A is incorrect because repeated failed logins don't suggest a rogue device. B is incorrect because beaconing indicates a possibly compromised system keeping in contact with a malicious actor or system outside the network. C is incorrect because failed connection attempts don't indicate a rogue device, except perhaps in the case where connections are only allowed from whitelisted MAC addresses.

-   4. With regard to peer-to-peer network communication, which of the following observations should a cybersecurity analyst be concerned with as abnormal? (Choose all that apply):

-   A. Host-to-host connections using an unprivileged account
-   B. Host-to-host connections using a privileged account
-   C. Local user connecting to a print server on another subnet
-   D. Client/server connections with high number client ports
-   ☑ A and B are correct. Host-to-host connections are fairly uncommon. Such peer-to-peer communication can suggest an attacker moving laterally from one to another.
-   ☑ C and D are incorrect. C is incorrect because a local workstation connecting to any print server is hardly abnormal. D is incorrect because client/server connections typically originate with the client using a high port number.

-   5. A network engineer is responding to users complaining the network is slow. Looking at the blinking lights, the engineer notices considerable activity by the HR file server. What would be the network engineer's next step?

-   A. Unplug the network cable at the switch going to the file server.
-   B. Monitor usage and compare it against the baseline.
-   C. Alert the CIO to the traffic spike.
-   D. Sample the traffic using a packet analyzer.
B is correct. The network engineer's next step is to consider whether the activity is normal by monitoring usage and comparing it against the baseline.
A, C, and D are incorrect. A is incorrect because unplugging the network cable is clearly wrong. C is incorrect because it's far too early to escalate the issue to the CIO. D is incorrect because sampling the traffic is likely the course of action after comparing traffic against the baseline.

-   6. A cybersecurity analyst has a suspicion upon a system's behavior, reviewing logs and baseline performance of that has proven nothing. Finally, the analyst decides to investigate network traffic, based on a hunt. The analyst starts with an endpoint analysis. The analyst sorts the traffic log first by internal source address, by destination address, and finally by time. What evidence is the analyst clearly searching for?

-   A. Beaconing.
-   B. Anomalous activity.
-   C. Network memory consumption.
-   D. This is not a search; rather, the analyst is creating a new baseline.
A is correct. Judging by the analyst's traffic analysis, the intention is to identify any beaconing.
B, C, and D are incorrect. B is incorrect because the analyst is sorting traffic a particular way. C is incorrect because the analyst wouldn't be sorting traffic to identify network memory consumption. D is incorrect because the analyst is searching for a particular clue.

-   7. A user notices the workstation seems louder than normal—necessarily fan noise, but the hard drive is constantly “working” without the user installing or moving any files. When the analyst asks if any other system behavior is occurring, the user replies the system seems a bit slower as well. What might be an issue the system is experiencing?
