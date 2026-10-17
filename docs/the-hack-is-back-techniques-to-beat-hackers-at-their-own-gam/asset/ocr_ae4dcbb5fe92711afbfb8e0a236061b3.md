We discussed the threat of vulnerable software, mergers and acquisitions, and third-party vendors that all can leave companies and organizations with security holes they were not anticipating. There is also the threat of supply-chain attacks, in which a company uses software from a trusted vendor that becomes compromised. This was the case with SolarWinds, which has a wide customer base using its network management and monitoring software. The nation-state attackers, attributed to Russia, compromised SolarWinds and then were able to add a backdoor program into the software updates and when their customers deployed these updates with malicious code, they also became compromised.

![](bbox=[0.41, 0.239, 0.59, 0.271])

**FIGURE 8.10**  Article Link: [https://www.businessinsider.com/solarwinds-hack-explained-government-agencies-cyber-security-2020-12](https://www.businessinsider.com/solarwinds-hack-explained-government-agencies-cyber-security-2020-12).

So why not just update all of your software all of the time? Well, in general, you should. And sometimes, you are even forced to, like with an iPhone or an XBOX. The XBOX brings up an interesting conundrum. Why does Microsoft force updates on their video game system for you to use it but not impose those same requirements on end users utilizing Microsoft Windows? Well, Microsoft Windows runs on countless computer vendor hardware platforms and pretty much is in the position of supporting an unlimited amount of different hardware configurations. This is what makes a MacBook Pro, iPhone, and XBOX so much easier to support as it is that the vendor is controlling the hardware and the Operating System (OS). Many times, updates might secure your systems but they can also break your applications as well. It is a constant game of cat and mouse for the IT staff to continually update systems that need to have their applications tested functionally almost every time these updates occur. This constant and unending battle is a great reason that a career in cyber seems fairly secure at the time of this writing.

# DATA EXFIL 101

Now we will move on to how data is stolen by the hacker and what techniques are used to perform these actions. First, let’s discuss what a hacker should go after and where the “best stuff” might be. If an attacker has the skills to break into a system, they also need to know where the “loot” might be located.

```
```text
meterpreter > ls
Listing C:\

Mode                 Size        Type  Last modified           Name
40777/rwxrwxrwx       4096        dir   2008-01-19 04:34:18 -0500  $Recycle.Bin
100444/r--r--r--     8192        fil   2012-09-10 22:01:39 -0400  BOOTSECT.BAK
40777/rwxrwxrwx       8192        dir   2012-09-10 22:01:37 -0400  Boot
0000/---------------     0        fil   1969-12-31 19:00:00 -0500  Documents and Settings
40777/rwxrwxrwx       4096        dir   2008-01-31 04:40:52 -0500  PerfLogs
40555/r-xr-xr-x       4096        dir   2008-01-19 04:40:52 -0500  Program Files
40777/rwxrwxrwx       4096        dir   2008-01-19 04:40:52 -0500  ProgramData
40777/rwxrwxrwx       4096        dir   2012-09-10 21:02:20 -0400  System Volume Information
40555/r-xr-xr-x       4096        dir   2008-01-19 04:45:53 -0500  Users
40777/rwxrwxrwx      16384        dir   2008-01-19 04:40:53 -0500  Windows
100444/r--r--r--    333203        fil   2012-01-19 04:31:37 -0400  bootmgr
40777/rwxrwxrwx          0        dir   2015-01-31 19:39:04 -0500  inetpub
100666/rw-rw-rw-  2460368896        fil   2012-09-10 20:02:20 -0400  pagefile.sys
40777/rwxrwxrwx       4096        dir   2012-09-12 18:40:53 -0400  share
40777/rwxrwxrwx      12288        dir   2015-01-31 19:25:55 -0500  xampp
```
```

**FIGURE 8.11**  Meterpreter directory listing.