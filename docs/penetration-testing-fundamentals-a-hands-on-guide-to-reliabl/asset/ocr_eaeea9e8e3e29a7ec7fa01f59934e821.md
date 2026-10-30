# Scanning with Metasploit

As you have seen in the early part of this book, scanning the target is an important step. If you don’t know much about the target, you will not have much success in attempting to breach it. Fortunately, Metasploit supports a large number of searches, as described in the sections that follow.

# SMB Scanner

Server Message Block (SMB) is used by Windows Active Directory. When you are scanning for this, you are checking to see if the target is a Windows computer. The scan is easy:

```
use scanner/smb/smb_version
set RHOSTS 192.168.1.177
set THREADS 4
run
```

Of course, you should replace the IP address 192.168.1.177 with the IP address of the target you are scanning. You can see the results in Figure 13-9.

![](bbox=[0.12, 0.45, 0.77, 0.58])

FIGURE 13-9 SMB Scanner.

While this is simple, it has a lot of information in it. So let us go through it, one line at a time, so that you fully understand. The first line is

```
use scanner/smb/smb_version
```

You will see lines, much like this, throughout this chapter. This is saying that you intend to use a specific module. And it gives the path to that module. Notice the first part of the path is scanner. This particular directory has a number of scanners you can use. The next line is

```
set RHOSTS 192.168.1.177
```

First notice the RHOSTS. This is the IP address for the remote host(s) you are scanning. Some modules will have RHOST, indicating you can only scan one target, while others will have RHOSTS, indicating you can scan several targets if you wish. Anytime a module has RHOSTS rather than RHOST, you could scan a range of IP addresses. Just modify the command to say:

```
set RHOSTS 192.168.1.177 192.168.1.215
```