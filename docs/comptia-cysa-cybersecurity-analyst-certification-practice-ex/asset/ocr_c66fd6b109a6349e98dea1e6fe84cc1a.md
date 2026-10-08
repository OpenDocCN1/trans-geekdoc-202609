D. # show run all logging

+   A is correct. The command show running-config logging is the proper one to start with, in order to continue with a specific command for logging onto a Cisco ASA firewall.

+   B, C, and D are incorrect. None of these commands is the correct one.

18. After running tcpdump, an analyst reviews the output, which includes the following line:

```
16:35:39.834754 > badguy.org.12889 > target.net.8008: FP
2921:4105(1184) ack 1 win 32120 (DF)
```

What does the “FP” represent?

# A. Final Packet

# B. First Packet

# C. Fin Push

# D. Forward Packet

+   C is correct. The “F” stands for Fin, and the “P” for Push. The words Fin and Push delete what TCP flags were set (for example, Fin, Push, Urg, Syn, Reset, or Ack).

+   A, B, and D are incorrect. The “P” in FP does not stand for “Packet.”

19. The director of technology has decided that the company requires an IDS. As the senior security analyst, you recommend Snort. The director requests that you flag any SSH request coming from a known competitor’s network. Examine the following rules and select the one that alerts if traffic originates from the network at 12.34.56.x/24 and is destined for the company’s web server (IP address 210.67.79.89).

+   A. alert tcp 210.67.78.89 -> 12.34.56.0/24 80

+   B. alert tcp 12.34.56.0 24 -> 210.67.79.89 21

+   C. alert tcp 210.67.78.80 -> 12.34.56.0/24 any

+   D. alert tcp 12.34.56.0 24 -> 210.67.79.89 22

+   D is correct. The Snort rule correctly alerts if an SSH request (over 22/TCP) comes from the network 12.34.56.0/24 to the company web server at 210.67.79.89.

+   A, B, and C are incorrect. A is incorrect because the source and destination addresses reversed and is monitoring port 80 (HTTP), when the question stated SSH traffic. B is incorrect because the Snort rule is monitoring for port 21 (FTP). C is incorrect because the Snort rule has the