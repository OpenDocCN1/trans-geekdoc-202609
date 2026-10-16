
Here is an example of running `afl-fuzz` against a PDF viewer application. Normally, `afl-fuzz` requires applications to be built with instrumentation enabled so the application can be managed as it is executing. If you are unable to get access to the source code or unable to build a binary with instrumentation enabled, you can add the `-n` flag, which skips that part of the testing, which will lead to less reliable results.

```
kilroy@cutterjohn:~ $ afl-fuzz -t 100000 -n -i pdfs -o pdf-results /usr/local/bin/atril
afl-fuzz++4.04c based on afl by Michal Zalewski and a large online community
[+] afl++ is maintained by Marc "van Hauser" Heuse, Heiko "hexcoder" Eißfeldt, Andrea Fioraldi and Dominik Maier
[+] afl++ is open source, get it at https://github.com/AFLplusplus/AFLplusplus
[+] NOTE: This is v3.x which changes defaults and behaviours - see README.md
[*] Getting to work…
[+] Using exponential power schedule (FAST)
[+] Enabled testcache with 50 MB
[+] Generating fuzz data with a length of min=1 max=1048576
[*] Checking core_pattern…
[!] WARNING: Could not check CPU scaling governor
[+] You have 2 CPU cores and 2 runnable tasks (utilization: 100%).
[*] Setting up output directories…
[+] Output directory exists but deemed OK to reuse.
[*] Deleting old session data…
[+] Output dir cleanup successful.
[*] Checking CPU core loadout…
[+] Found a free CPU core, try binding to #0.
[*] Scanning 'pdfs'…
[*] Scanning 'pdfs/Downloads'…
[+] Loaded a total of 3 seeds.
[*] Creating hard links for all input files…
[*] Validating target binary…
[*] No auto-generated dictionary tokens to reuse.
[*] Attempting dry run with 'id:000000,time:0,execs:0,orig:keyboard-shortcuts-linux.pdf'…
[*] Spinning up the fork server…
[*] Using AFL++ faux forkserver…
[+] All right - fork server is up.
```

File‑based fuzzing does require local access to exploit any identified vulnerability. However, this can be useful for a number of post‑exploitation attack techniques, including privilege escalation.

## Post Exploitation

You now have a foothold on the system. What you can do with it depends on what you compromised. You may have limited permissions if the remote service you compromised has limited permissions. You can only perform tasks that you have permissions to perform. This means you may need to escalate your privileges to a user with more than you have. Gaining root or administrator permissions is a common objective for attackers since it helps them pivot to other systems to move laterally within the environment. You may also have a better chance to collect passwords and other critical system information that you may need for other tasks.

You not only have a foothold on the system, but that system also gives you a foothold on the network as well. You may find, especially if you have compromised a system offering services to the outside world, that the system is connected to more than one network. This means you can use the compromised system as a gateway to those other networks. This is a technique called *pivoting*, where you pivot off the compromised system to take a look at another set of systems. This will get you further into the network and potentially gain you even more sensitive information or access to more critical systems.

Attackers will also look to gain persistent access to the system. This may mean a number of activities, from creating users to installing backdoors. Alongside persistent access, the attacker will want to cover their tracks. This can mean hiding data in places on the system. It may mean manipulating logs. It can also mean manipulating system binaries to help hide your existence.

### Evasion

Once you have a foothold, which may include usernames and passwords or actual remote access to a system, you may run into problems. Both workstations and servers will probably have at least anti‑malware if not software that will look for anomalous behavior. Endpoint detection and response (EDR) software will know what attack techniques look like. Common tools, such as those discussed in this chapter, may be well‑known to these sorts of tools. This calls for evasive tactics.

One possible place where evasion needs to happen is detecting files, primarily on disk. You may be able to use techniques like alternate data streams mentioned later. You can also encrypt or otherwise obfuscate data. Encrypted zip files are one way to get around detection in anti‑malware software.

When it comes to execution, though, we have another problem. Anti‑malware software may have ways of detecting executables. You may be able to get around this by using PowerShell to perform the same task. There may not be a detection in place for a PowerShell script, especially if you write your own, and you may be able to accomplish the same task that a native executable is doing for you. One of the problems with PowerShell is it may be logged. This can make detection after the fact easier, but not if the PowerShell can't be read. As an example, the following is a sample of PowerShell that has been obfuscated:

```
$N7 =[char[ ] ] "noisserpxE-ekovnI| )93]rahC[,'pQm'ecalpeR-
43]rahC[,'bg0'ecalpeR- )')pQm'+'nepQ'+'m+pQme'+'rGpQm'+'
( '+'roloCdnu'+'orger'+'oF- )bg0nbg0'+'+ bg0oibg0'+' +
bg0tacbg0'+'+'+'bg0sufbO-b'+'g'+'0+'+'bg0ek'+'ovn'+'bg0+ bg0Ib'+'g'+'0 '+' (
)'+'bg'+'0tsO'+'bg0'+' + bg'+'0H'+'-'+'ebg0 '+' '+'+ b'+'g0'+'tIRwb'+'g0(.
'((";[Array]::Reverse($N7 ) ; IEX ($N7-Join '' )
```

This translates to `Invoke‑Obfuscation`, which is a cmdlet written by Daniel Bohannon that takes a PowerShell script and obfuscates it. There are different ways to accomplish the obfuscation, as demonstrated when you run the cmdlet without any parameters. The following are the techniques you can use for obfuscating PowerShell using this cmdlet:

```
Choose one of the below options:
 
[*] TOKEN Obfuscate PowerShell command Tokens
[*] AST Obfuscate PowerShell Ast nodes (PS3.0+)
[*] STRING Obfuscate entire command as a String
[*] ENCODING Obfuscate entire command via Encoding
[*] COMPRESS Convert entire command to one-liner and Compress
[*] LAUNCHER Obfuscate command args w/Launcher techniques (run once at end)
```

There are several other ways to obfuscate scripts and data. This may include techniques like encoding payloads that have been generated by a tool like Metasploit. Ultimately, your objective is to get access to a system, which may include getting files onto a system without detection or, probably more likely, executing programs on a target system.

### Privilege Escalation

Your mission, should you choose to accept it, is to gain root‑level access. There was a time when services ran as root on Unix/Linux systems or as LocalSystem on Windows systems, which is an account that has a high level of permissions. Once you have root‑level access, you should be able to gain access to all information on the system as well as make changes to services and manipulate users. What this means is that you need to get access to the system first, and then you'll need to run another exploit to get elevated privileges. We can continue to use Metasploit for this, so let's start with a compromised system with a Meterpreter shell. If we background the shell using `background`, we can make use of the open session as a way of interacting with the system.
