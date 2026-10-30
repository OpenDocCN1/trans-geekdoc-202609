Before we continue on to other scans, let’s do something we have not done so far. Let me show you how you can find out the options for these modules yourself, rather than simply taking what I tell you. After loading the module with use auxiliary/scanner/mssql/mssql_ping, type show options. Metasploit will tell you what that module’s options are, as well as which ones are required and which are optional. You can see this in Figure 13-11.

![](bbox=[0.11, 0.24, 0.77, 0.56])

FIGURE 13-11 Viewing a Module’s Options with show options.

As you are learning Metasploit, I suggest you run show options after every time you use any module. Study the options for a moment. At the end of this chapter, the goal is that you be basically proficient in Metasploit, not that you have simply memorized a handful of commands.

# SSH Server Scan

This is a scan to detect Secure Shell (SSH) servers on the target. The commands are very similar to what you have already seen:

```
use scanner/ssh/ssh_version
set RHOSTS 192.168.1.177
Set THREADS 1
Set USE_WINDOWS_AUTHENT false
Run
```

Because all of these commands have already been explained, no further explanation is needed. You can see the results in Figure 13-12.