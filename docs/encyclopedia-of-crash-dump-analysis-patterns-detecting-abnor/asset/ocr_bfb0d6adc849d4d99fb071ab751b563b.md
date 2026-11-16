# Step Dumps

It is common to get dozens of process memory dumps saved sequentially, for example, after each second. Then we can first analyze memory dumps corresponding to changes in their file sizes ignoring plateaus to save analysis time. This pattern is called by analogy with step functions²⁰⁴. For example, we have this dump set with comments from WinDbg analysis sessions (it was reported that an application was freezing for some time until its disappearance from a user screen):

```
C:\MemoryDumps>dir
[...]
12/30/2012 8:33 PM 218,252,862 AppA-1.dmp // normal
12/30/2012 8:34 PM 218,541,762 AppA-2.dmp // slightly increased CPU consumption for thread #11
12/30/2012 8:37 PM 218,735,848 AppA-3.dmp // spiking thread #11
12/30/2012 8:38 PM 218,735,848 AppA-4.dmp
12/30/2012 8:38 PM 218,735,848 AppA-5.dmp
12/30/2012 8:39 PM 218,735,848 AppA-6.dmp
12/30/2012 8:39 PM 218,735,848 AppA-7.dmp
12/30/2012 8:39 PM 218,735,848 AppA-8.dmp
12/30/2012 8:40 PM 218,735,848 AppA-9.dmp
12/30/2012 8:40 PM 218,735,848 AppA-10.dmp
12/30/2012 8:41 PM 218,735,848 AppA-11.dmp
12/30/2012 8:41 PM 218,735,848 AppA-12.dmp // spiking thread #11
12/30/2012 8:42 PM 219,749,040 AppA-13.dmp // spiking thread #11, another thread blocked in ALPC
12/30/2012 8:42 PM 219,048,842 AppA-14.dmp // only one thread left
[...]
```