We are basically saying to listen on network interface eth0 and only focus on the IP of the guest machine and only listen to TCP or UDP ports (to avoid ARP or other noisy traffic). Also, because we are dealing with Mirai-based malware, we want to avoid port 23, which is normally used for scanning the Internet and will quickly increase the size of our capture file with the same destination port. It is highly recommended that you avoid doing this on your local network because your IP might be banned by your ISP.

On another terminal, trace the execution of the malware by executing the following command. Probably the most important options are -f for following child processes (very important since Mirai-based malware uses fork to eventually hide from the parent process) and -o for storing the gathered information into a file.

```
#strace -f -q -s 100 -o satori.out ./470.arm
```

Once strace and tcpdump are running, you can always monitor the size of those files and transfer the current captured file at intervals. Depending on the malware, it can be left running for minutes, hours, or even days. For this lab, after 5 minutes you can stop the malware execution (normally by shutting down the machine).

By taking a look at the captured traffic, you can identify the attacker’s host (C2) where the malware is trying to connect, as shown in Figure 25-14.

| Source | Destination | Protocol | Length Info |
| :--- | :--- | :--- | :--- |
| 10.0.2.15 | 8.8.8.8 | DNS | 82 Standard query 0x3730 A network.bigbotpein.com |
| 8.8.8.8 | 10.0.2.15 | DNS | 98 Standard query response 0x3730 A network.bigbotpein.com A 177.67.82.48 |
| 10.0.2.15 | 8.8.8.8 | DNS | 82 Standard query 0x1c48 A network.bigbotpein.com |

Figure 25-14 C2 used by the malware

If you want more details about the actions performed on that site, you can take a look at the satori.out output file, where you can easily identify a telnet connection to the resolved IP 177.67.82.48, as shown in Figure 25-15.

![](bbox=[0.123, 0.632, 0.88, 0.69])

Figure 25-15 Telnet connection with the C2

The duration of this particular capture shows an infinite loop of the malware trying to get a response from the host, which is not available at the time of testing. That’s the normal behavior of Mirai-based malware, waiting to receive the command to be executed.

Feel free to play with the malware or execute other samples following the same approach. You will eventually need a strace output parser for a good-looking report.

# Platform for Architecture-Neutral Dynamic Analysis (PANDA)