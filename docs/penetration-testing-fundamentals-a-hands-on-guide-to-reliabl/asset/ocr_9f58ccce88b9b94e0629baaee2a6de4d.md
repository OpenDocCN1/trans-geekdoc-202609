![](bbox=[0.07, 0.115, 0.73, 0.445])

FIGURE 13-20  File Format Exploit.

# Remote Desktop Exploit

This one is a bit of a scan, rather than directly exploiting. But it is checking if the target has a specific remote desktop flaw that would let you get into that machine with remote desktop:

```
use auxiliary/scanner/rdp/ms12_020_check
set RHOSTS YOURTARGETIP
set RPORT 3389
set THREADS 1
```

You can see the results in Figure 13-21.

![](bbox=[0.07, 0.68, 0.72, 0.94])

FIGURE 13-21  RDP Exploit.