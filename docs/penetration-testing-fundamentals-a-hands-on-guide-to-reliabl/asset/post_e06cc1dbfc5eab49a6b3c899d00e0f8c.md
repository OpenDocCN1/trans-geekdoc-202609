
particular exploit, then you won’t get in. If a machine is thoroughly patched, you probably won’t get in. But from a penetration tester point of view, that is exactly the sort of thing you wish to test!

This brings us to the third thing. How will you practice Metasploit? You will need at least two things:

- An attack machine with Kali Linux
- At least one target

Fortunately, you can put both as virtual machines and have one VM attack the other. But what type of machine should you have for the target? There are two approaches to this. The first is to get a realistic modern target. A patched Windows 10 machine (or whatever version is current while you are reading this) is very realistic, but the truth is most of what you try will not work. If you want to guarantee that some if not all of the attacks described in this book work, then get a version of Windows 7 without service pack 1. There are a few places for you to look for a target machine:

- Microsoft provides virtual machines for testing, which you can find at https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/. However, all of their Windows 7 VMs do have service pack 1 and you cannot remove it. This may mean some exploits in this chapter won’t work.
- If you have an MSDN subscription (and that is free), you may be able to get a Windows 7 iso from there.
- There are many websites that sell old versions of Windows. But make sure you get one without service pack 1 if you want to guarantee the attacks will work.
- People often sell old versions of Windows on places like eBay. Again, just check to make certain it is without service pack 1, to guarantee you will succeed in these exploits.

Now, it may seem a bit artificial to have you try a Windows 7 machine with no service packs. But this chapter is meant for Metasploit beginners. It is meant for you to succeed. But do be aware, the ease with which you get into these machines will not be repeated when you move to real machines that probably are patched (or at least they should be!).

Setting up your virtual machine is a bit different depending on whether your target is on a different computer or on a different virtual machine on the same host:

- Installing as Live USB with persistence. This option will install very easily; however, the VM may not be on the same subnet as the host. The VM should still be able to ping the host. If you have trouble pinging host to VM and VM to host, then manually set the IP address to be on the same subnet as the host.
- Set the VM network to **bridge** and manually set a static IP address with **ifconfig eth0** 192.168.0.XXX (or any range you want to use, as long as all machines involved are in the same range).

**Note**

If you are going from Kali VM to victim VM on the same host, then set to **host only adapter** and **allow all.**

## Background on Metasploit

Metasploit was first created in 2003 and was written in Perl. It was developed by a man named H. D. Moore. Moore is a well-known security expert and hacker. In 2007, it was rewritten in Ruby. In 2009, Metasploit was acquired by the company Rapid7, who now handles all maintenance and distribution of Metasploit.

Really, much of Metasploit can be divided into four types of objects you will work with:

- **Exploits:** These are pieces of code that will attack a specific vulnerability. Put another way, exploits are vulnerability specific.
- **Payload:** This is the code you actually send to the target. It is what actually does the dirty work on that target machine, once the exploit gets you in.
- **Auxiliary:** These modules provide some extra functionality. For example, scanning.
- **Encoders:** These embed exploits into other files like PDF, AVI, etc. We will see those in the next chapter.

This may make more sense with an explanation from Rapid7 (the people who distribute Metasploit):

> A vulnerability is a security hole in a piece of software, hardware or operating system that provides a potential angle to attack the system. A vulnerability can be as simple as weak passwords or as complex as buffer overflows or SQL injection vulnerabilities.
> 
> To take advantage of a vulnerability, you often need an exploit, a small and highly specialized computer program whose only reason for being is to take advantage of a specific vulnerability and to provide access to a computer system. Exploits often deliver a payload to the target system to grant the attacker access to the system.
> 
> The Metasploit Project hosts the world’s largest public database of quality-assured exploits. Have a look at our exploit database—it’s right here on the site.
> 
> (https://kb.help.rapid7.com/v1.0/docs/penetration-testing)

## Getting Started with Metasploit

Okay, you have read enough background, you want to see Metasploit! Well, let us not delay any longer. You have two options in Kali Linux. The first is to just use the desktop GUI and click on the Metasploit icon. You can see how to find this in Figure 13-1.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_311_0.png)

FIGURE 13-1 Launching Metasploit.

The second option is manual. Open the shell and issue three commands:

- 1. `service postgresql start`
- 2. `msfdb init`
- 3. `msfconsole`

You can see this in Figure 13-2.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_312_0.png)

FIGURE 13-2 Manually Starting Metasploit.

Now once you type **msfconsole** and hit **Enter**, a lot begins to happen. You will see a great many messages scroll past the screen. Whether you start Metasploit manually or through the GUI, the end result will be similar to what you see in Figure 13-3.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_312_1.png)

FIGURE 13-3 Metasploit Started.

The message you see on the screen is telling you that your Metasploit payloads might be detected by some antivirus products. The suggestion is to upgrade to Metasploit Pro and use the Dynamic Payloads found in that product. Now you only need to do one more thing and you are ready to start. That is to check the database. Metasploit uses a database. The way to check and make sure it is running properly is to type:

```
db_status
```

If all is well, you will see the message shown in Figure 13-4.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_313_0.png)

FIGURE 13-4 Database Connected.

If there is any problem, you will see the message shown in Figure 13-5.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_313_1.png)

FIGURE 13-5 Database Not Connected.

If the database connection is not working, you can still use Metasploit but you won’t be able to save the results to the database. But now you are ready to use Metasploit!

## Basic Usage of msfconsole

We will begin with basic navigation and commands in this section. In the next sections you will learn to conduct scans with Metasploit and to perform exploits; however, you will need to refer back to these commands to navigate in Metasploit.

### Basic Commands

The basic commands that you will use most frequently in Metasploit are briefly described here:

- **back:** This command is used to back out of an exploit. For example, if you just attempted an exploit and it did not work, and you wish to try another, then use this command to back out to the main Metasploit console.
- **load:** You will use this command frequently. It allows you to load any module/plugin.
- **unload:** This will unload a plugin.
- **exit or quit:** These should be obvious. They quit Metasploit.
- **use:** By the time you finish this chapter, you will be very familiar with this command. It is the command that tells Metasploit what you are going to use. This will become very clear in the next section on scanning.
- **show exploits:** This shows exploits.
- **show payloads:** Once you have loaded an exploit, this will show you the payloads you can use with that exploit.
- **show options:** If you load a payload or an exploit, **show options** will tell you what options you can set and what you must set.
- **jobs:** This command shows you currently running jobs.
- **kill:** This command is used to kill any running job.
- **sessions:** This shows you active sessions. If your exploit is successful, then you will have one or more running sessions. Then you can use **sessions -i 3** (replace **3** with the session number you want) to take control of that session and interact with the target machine.
- **msfupdate:** Metasploit updates the framework from time to time. If you want the latest, you type **msfupdate** from the shell. Notice I said from the shell, not from inside Metasploit.

This is Linux, and remember that Linux is case sensitive.

Again, these are the most fundamental commands. As you work through the chapter, you may wish to refer to this list from time to time.

### Searching

Metasploit has quite a lot in it. And you will be forgiven if you cannot memorize it all. Fortunately, it also has a very good built-in search capability. You can easily search for exploits in a variety of ways. Let us begin by searching by platform.

You can try:

```
search platform:Windows
```

But that will quickly fill many screens with numerous results. And it is not that helpful. Is a given exploit for Windows 7, or Windows 8, or Windows Server 2016, or Windows 10? You can modify this to be more specific:

```
search platform:"Windows 8.1"
```

This will help you get exactly what you are looking for. You can see this in Figure 13-6.
