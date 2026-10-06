# /syncfromflags This is this manual because you want to sync with the servers in the
manual peer list.

You can specify multiple time servers by separating them with spaces and surrounding them with
double quotes, like so:
w32tm /config /computer:bf"time.windows.com AnotherTimeServer StillAnotherOne.com" /
syncfromflags:manual /reliable:yes

If you force the server that you want the clock to sync with, you can find out by typing this:
w32tm /query /computer:bf1 /source

By default, the root forest's PDC FSMO will try to synchronize with its time source once
every six minutes and again six minutes later. It keeps resynchronizing every six minutes until
it has successfully resynchronized three times in a row. Then it reduces its frequency to\every 100 minutes. You can change this with a registry entry, although we're not sure why
you'd need to do so (All Time server parameters are in HKLM\System\CurrentControl\nServices\W32Time). Alternatively, you can run the following command to view the
configurations:

```
C:\Users\Administrator >w32tm /query /computer:bf1 /configuration
[Configuration]
```

+   EventLogs: 2 (Local)
AnnounceFlags: 10 (Local)
TimeJumpAuditoffset: 28800 (Local)
MinPollInterval: 6 (Local)
MaxPollInterval: 10 (Local)
MaxNegPhaseCorrection: 172800 (Local)
MaxPosPhaseCorrection: 172800 (Local)
MaxAllowedPhaseOffset: 300 (Local)

+   FrequencyCorrectRate: 4 (Local)
PollAdjustOffset: 50000000 (Local)
SpikeWatchPeriod: 900 (Local)
LocalClockDispersion: 10 (Local)
HoldPeriod: 5 (Local)
PhaseCorrectRate: 7 (Local)
UpdateInterval: 100 (Local)

But where do you find an SNTP server? Oddly, there are many around. Most ISPs'
dig DNS servers seem to act as SNTP servers. You can find out which particular machine
is an SNTP server with a neat little tool called ntpquery.exe from www.bytefusion.com/
products/fs/fs.htm. You just point it at a DNS name or IP address, and if that machine is a
time server, you get a full screen of incomprehensible long numbers.