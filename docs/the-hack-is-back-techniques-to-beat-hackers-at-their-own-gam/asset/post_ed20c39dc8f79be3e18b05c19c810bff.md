
To find established connections in Linux (Note that ESTABLISHED should be capitalized in both cases):

```
netstat -tanp | grep ESTABLISHED
```

To find established connections in Windows:

```
netstat -anob | find "ESTABLISHED"
```

![](img/181571ad74cba0e6a2f38fcd2658651e_278_0.png)

FIGURE 9.7 Outbound Java and SSH connections to an IP Address in North Korea.

So, we can look at the built-in commands to examine the processes involved in the connections. While it is nice to have built-in commands in case you need to react fast, there are some far better free tools (for Windows) that will be covered in the next section. So, if an attacker is in your system, there will be:

- 1. An IP Address and Port (IP+Port=Socket) that they use to connect to your system.
- 2. A Process ID (or PID) that is associated with the remote attacker to your system.

If I was attacking your system, I would name my file, svchost.exe? Why? Take a look at my non-compromised system and notice how many different PIDs are associated with svchost.exe. They actually did not all fit in the screenshot. I also had a large amount of Chrome.exe and MSedge.exe processes.

![](img/181571ad74cba0e6a2f38fcd2658651e_278_1.png)

FIGURE 9.8 Holy SVCHOST Batman.

Anyway, besides looking in the task manager there are some built-in tools in Linux to examine the processes on the system. In the case of Linux, you get the name of the process associated with the remote connection by using netstat -p. However, there is additional information we can get about the process that is extremely useful if we type ps -elf and then filter for the PID using the grep (global regular expressions print). Here you see that I found out that there is a Metasploit Payload associated with the PID and you can also find the location of the malicious payload in the /tmp directory. If you were not aware, the temp directory is usually deleted when the machine is shut down, so this is a reason that the examination and collection of volatile data and imaging of RAM are advised. Notice that I used the tried and true kill -9 command to put an end to North Korea’s fun with my Linux system.

![](img/181571ad74cba0e6a2f38fcd2658651e_279_0.png)

**FIGURE 9.9** Thanks for the hack, North Korea.

Built into Windows, you can use netstat to view the connection, tasklist to get information about the process, and taskkill to kill the process. You can also use netstat with the -ob switch on a Windows system to determine the process ID (PID) and the name of the executable that corresponds to the network connection. With the /v switch, tasklist (/v) will provide you with more detailed information about the process, and the taskkill command can be utilized to stop it. I also choose to use pslist (similar to tasklist) and pskill (similar to taskkill) which are part of the free sysinternals suite of tools for Windows. These tools are really a must have for anyone examining their system and can be downloaded from here: https://learn.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite, and these tools should all be part of your Windows Incident Response (IR) toolkit. Notice that I killed the PowerShell process. The issue with PowerShell is it is a legitimate program that runs on networks and is frequently utilized by systems administrators. But PowerShell is also leveraged by attackers as its powerful capabilities can be used by hackers within the network. In the example below, the attack is coming from an internal private IP Address of 172.16.200.50. That system should also be examined as it could be an attacker moving laterally, an insider threat, or be a network administrator (except that is extremely unlikely if they are using port 4444).

![](img/181571ad74cba0e6a2f38fcd2658651e_279_1.png)

**FIGURE 9.10** PowerShell PID killed.

## GETTING NASTIER, THEY UPPED THEIR GAME AND SO WILL WE

Once the attacker gets in, they will want to maintain their access by installing backdoors or creating accounts that can be used to connect to the system. Typically, a hacker will want to have persistence on a box, meaning if you kill the process with kill -9, pskill, task manager, or taskkill, the attacker will be easily able to re-enter your system. If an attacker gets persistence on the victim machine, an event like logging on to or restarting the computer will likely reestablish the attacker's connection. Sometimes, malware does not need to rely on any event, and it just keeps trying to reconnect when it drops. Most of the Graphical User Interface (GUI) based malware that I use has options to allow the attacker to maintain their persistence. Metasploit also gives an attacker the ability to maintain their persistence. An attacker wants to establish this right away so they can still have another route to get back in if they are detected or the original point of entry is closed.

Now, we need to examine some additional user-friendly commands in meterpreter that will keep the attacker in the system. As a long-time Metasploit user, I can attest to the fact that many useful commands and plugins have been released over time to make persistence and post exploitation much easier for the attacker. There was actually a time when meterpreter traffic from the attacker to the victim was not even fully encrypted. I am mentioning this because it is important to understand the evolution over time of hacker tools, as they are much more sophisticated and easy to use.

![](img/181571ad74cba0e6a2f38fcd2658651e_280_0.png)

FIGURE 9.11 Establishing persistence in Metasploit.

Typically, a Windows registry key will be created that will allow that malware to connect back to your attacker. For our forensic investigators out there, it is important to note that there will be a path to the malicious executable within the Windows Registry that will allow us to locate it on the disk, perform malware analysis, and possibly determine some type of attribution. And, as I mentioned with Linux, if a file is dumped into the Windows\temp directory it may not be present when the system is turned off which again reiterates our reason to collect volatile data and image the systems’ RAM to preserve indicators of compromise.

Now, let’s forget about those command line utilities and switch to some GUI-based sysinternals tools. The first (free) tool that I am examining, process explorer, is a must have for those looking at connections and processes, whether dealing with a real intrusion or some type of blue team exercise or competition. The process explorer tool will provide you with the data you can get from the netstat and tasklist commands and it is much more intuitive for locating a possible bad actor residing in your system.

When I am exploring the processes, I cannot help but notice the extremely long string that is present as well as a hidden flag that is likely there to help this malicious process evade detection. Finally, I also noticed that there is a curiously named process prLNUjAgGaE.exe. You are not going to see typical executables with a naming convention of lowercase and uppercase letters, so this is also a red flag.

![](img/181571ad74cba0e6a2f38fcd2658651e_281_0.png)

FIGURE 9.12 Process Explorer.

The other nice thing about Process Explorer is it will give you information about TCP/IP connection, including the IP Address and port (socket). In this case, we have a PowerShell connection to North Korea over port 4444, the default port for Metasploit. Outbound connections using port 4444 or PowerShell connections to North Korea are both something that should be avoided on any of your systems.

![](img/181571ad74cba0e6a2f38fcd2658651e_281_1.png)

FIGURE 9.13 PowerShell connection to North Korea.

The final thing we can do is examine this subprocess of PowerShell and we will notice a path to an executable. Notice that this executable was placed in the same directory that Metasploit indicated was created when the attacker ran the run persistence command within meterpreter.
