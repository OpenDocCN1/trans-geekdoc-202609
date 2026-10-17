![](bbox=[0.261, 0.088, 0.738, 0.259])

**FIGURE 8.15**  Terabytes of data exfiltrated from the network ([homelandsecuritynewswire.com](http://homelandsecuritynewswire.com)).

Due to the fact that the exfiltration could be (and likely is) fully encrypted, the forensic team might need to consider the possibility of looking at the digital artifacts on the compromised system. When I worked for an IR team, we would look for rar files as compressing the files and taking them out of the network is more efficient and less likely to activate various network sensors. And in my response and forensics gigs, I did not just look for a rar file on the disk. We would use WinHex (great tool) to search in slack space for rar files and most hackers are smart enough to delete their files prepared for exfil after they are stolen.

![](bbox=[0.213, 0.45, 0.786, 0.599])

**FIGURE 8.16**  RAR (or 7z) it up.

You can also examine the MAC (not that MAC) Modified, Accessed, and Created of the files on the systems. While you may not be able to prove what encrypted data left the network, if there is a 4 GB RAR file created that stores your proprietary data and you see 4 GB of network traffic leave your network, it is fairly safe to “infer” what likely happened. When encryption is used to exfiltrate the network data, you can never say for sure what happened, but you can certainly look at the disks, logs, user activity, and time stamps to take an educated guess of what happened to the important data.

Meterpreter is just one tool that can be used to take data out of the network. There are so many Remote Access Trojans (RAT) that use encrypted transmission. Many of them will have a File Manager where you can upload malware (send) or exfiltrate (receive) data from the network. You will notice that the interface used for file transfer on most of these RATs is similar to that of the WinSCP interface.