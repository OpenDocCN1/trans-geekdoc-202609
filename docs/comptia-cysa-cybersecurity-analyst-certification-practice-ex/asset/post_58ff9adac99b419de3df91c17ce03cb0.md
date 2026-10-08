
[content]

- A. Processor consumption
- B. Drive capacity consumption
- C. Memory consumption
- D. Network bandwidth consumption

C is correct. The scenario is evidence of disk paging, a sign of extreme memory consumption.

A, B, and D are incorrect. A is incorrect because the user mentioned the system is running somewhat slower, but not so much to point to processor consumption. B is incorrect because the drive sounds like it is “paging” due to a memory shortage, not drive capacity shortage. D is incorrect because there was no mention of network issues.

8. Figure 10-1 shows a portion of active connections on the author’s desktop. The output is presented in the following order: protocol, local address, foreign address, connection state, and process ID. At the same time, the author opens IDs Task Manager and takes note of a few running applications and their processes’ IDs, detailed in Figure 10-2. Which of these processes might the author want to investigate further?

- A. Dropbox.exe
- B. chrome.exe
- C. notepad.exe
- D. WINWORD.EXE

# Command Prompt

```
TCP 127.0.0.1:50151 127.0.0.1:50152 ESTABLISHED 9708
TCP 127.0.0.1:50151 127.0.0.1:50151 ESTABLISHED 9708
TCP 127.0.0.1:50264 127.0.0.1:50265 ESTABLISHED 1652
TCP 127.0.0.1:50264 127.0.0.1:50265 ESTABLISHED 1652
TCP 127.127.127:127399 0.0.0.0 LISTENING 4
TCP 169.254.128:67139 0.0.0.0 LISTENING 4
TCP 169.254.128:67540 0.0.0.0 LISTENING 7588
TCP 192.168.240:24039 0.0.0.0 LISTENING 7588
TCP 192.168.240:49158 63.59.138:80 ESTABLISHED 1652
TCP 192.168.240:49164 162.125.183:143 ESTABLISHED 962
TCP 192.168.240:49176 162.125.183:143 ESTABLISHED 962
TCP 192.168.240:49245 131.253.74:436 ESTABLISHED 2840
TCP 192.168.240:49302 50.116.51:249 ESTABLISHED 5864
TCP 192.168.240:49918 63.59.138:80 ESTABLISHED 7248
TCP 192.168.240:49991 162.125.183:443 CLOSE_WAIT 962
TCP 192.168.240:49993 52.121.21:443 CLOSE_WAIT 962
TCP 192.168.240:50028 162.125.143:347 CLOSE_WAIT 962
TCP 192.168.240:50034 52.129.19:443 TIME_WAIT 0
TCP 192.168.240:50035 81.161.59,94:80 ESTABLISHED 9708
TCP 192.168.240:50043 53.197:80 TIME_WAIT 0
TCP 192.168.240:50054 172.27.21.126:443 ESTABLISHED 16640
TCP 192.168.240:50055 52.129.19:443 ESTABLISHED 1652
```

Figure 10-1 Outbound connections

| Name | PID | Status | User name |
| --- | --- | --- | --- |
| Dropbox.exe | 9612 | Running | admin |
| chrome.exe | 2840 | Running | admin |
| notepad.exe | 16640 | Running | admin |
| WINWORD.EXE | 3461 | Running | admin |

Figure 10-2 Running processes

- C is correct. There's little doubt that notepad.exe maintaining an outbound connection, on port 443 no less, is suspicious. That outbound communication should be investigated further.

- A, B, and D are incorrect. Dropbox and Chrome are expected to have outbound connections. Microsoft Word is not in the display of Figure 10-1, but it also might have an outbound connection.

9. The cybersecurity analyst hears of recent news about a new worm traveling through the company network, installing a bot that makes digital currency. Because the mining software is installed under a random name, running as a random process, there are few known signatures to search for. What might be a likely symptom that could point to infected systems?

- A. Processor consumption
- B. Unexpected output
- C. Unusual traffic spikes
- D. Introduction of new accounts

A is correct. Because the executable and process names are random, the worm is difficult to locate by name. However, mining software tends to be processor intensive, so that's a good place for the analyst to start.

B, C, and D are incorrect. B is incorrect because there was no mention of unexpected output. C is incorrect because mining software isn't likely to produce much network traffic. D is incorrect because no new accounts were mentioned in this scenario.

10. In regard to stopping unauthorized software from being installed on a system, which approach is the most effective?

- A. Software blacklisting
- B. Standardized desktop images and privileges
- C. Software whitelisting
- D. Host-based intrusion detection and antivirus

C is correct. Whitelisting, or allowing only explicitly listed applications, is the most restrictive method.

A, B, and D are incorrect. A is incorrect because blacklisting particular software as "bad" or unauthorized is effective, but this method relies on knowing every potential piece of software. B is incorrect because having a standard image is good at the start, but if privileges are not restricted, then software could be installed. D is incorrect because using a host-based IDS and antivirus is very safe at stopping malware, but not necessarily restricting safe-but-unauthorized software.

11. An application is experiencing apparent memory issues. The symptoms are fairly straightforward, resulting in the application terminating. Occasionally an error pop-up appears with a vague message. From what you see, what is the next course of action?

- A. Perform a memory dump
- B. Back up the disk
- C. Ensure drivers are up to date
- D. Capture a packet

A is correct. In case an application is experiencing memory issues, possibly memory overflow, performing a memory dump is a prudent measure.

B, C, and D are incorrect. B is incorrect because backing up the disk will not capture anything. C is incorrect because it's unlikely drivers are the issue. D is incorrect because packet analysis is really only when you have a good idea of what you're looking for.

12. After recovering from an incident, a company decides to invest in data loss prevention (DLP) solution as subtly watermark documents. What do you think was the host-related issue the company experienced?

- A. Unauthorized privileges
- B. Service interruption
- C. Unusual traffic spikes
- D. Data exfiltration

D is correct. Given the mention of DLP and watermarks, you can assume there was an incident of sensitive information being removed or exfiltrated.

A, B, and C are incorrect. A is incorrect because an incident of unauthorized privileges would result in better account and authorization management. B is incorrect because service interruption, which can also be an application-related issue, would have been handled with added layers of redundancy, fault tolerance, or high availability. C is incorrect because unusual traffic spikes might have affected network design or application control.

13. A new file server is made available to employees. The server’s capacity is expected to be sufficient for three years. Within two weeks, users complain the file server isn't as responsive as it used to be. What’s a file called MB2TB.exe has been spotted in every folder. What might be a likely issue?

- A. Bandwidth consumption
- B. Processor consumption
- C. Drive capacity consumption
- D. Memory consumption

C is correct. The performance and mysterious file “MB2TB” suggests malware, which greatly consumes drive space.

A, B, and D are incorrect. There’s no suggestion that the network bandwidth, processor, or memory is experiencing a bottleneck. However, the drive capacity does seem tight.

14. A user has raised a support ticket because of an unexpected dialog box on his Windows 10 laptop. He wasn’t concerned at first, because the pop-up seems a legitimate Windows prompt, as seen in Figure 10-3. However, the user cannot understand why the pop-up appears, given there seems no connection to his actions. Treating this as an incident, where would you investigate further?

- A. User account “Randy.”
- B. Admin account.
- C. Application’s publisher.
- D. This is not an incident but rather a legitimate User Access Control prompt.
[/content]
