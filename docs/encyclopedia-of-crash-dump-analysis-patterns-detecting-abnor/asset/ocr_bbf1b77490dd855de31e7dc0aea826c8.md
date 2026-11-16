# Reserved Virtual Memory

Allocated dynamic memory such as process heap can remain reserved after deallocation, and its virtual memory region might become unavailable for usage. One example of this we encountered while debugging a .NET service. During peak usage, it reported various out-of-memory events, but its managed heap was healthy and didn’t consume much. However, its process heap statistics showed a large reserved heap segment missing in a similar memory dump from a development environment. Remaining allocated entries in that heap segment contained a specific **Module Hint** (page 696) that allowed us to suggest removing a 3rd-party product from a production environment.

In order to provide a proof of that possible scenario of reserved heap regions we created a special modeling application:

```
int _tmain(int argc, _TCHAR* argv[])
{
    static char *pAlloc[100000];
    for (int i = 0; i < 1000000; i++)
    {
        pAlloc[i] = (char *)malloc(1000);
    }
    getc(stdin);
    for (int i = 0; i < 1000000; i++)
    {
        free(pAlloc[i]);
    }
    getc(stdin);
    return 0;
}
```

Here is the debugging log:

```
0:001> .symfix c:\mss

0:001> .reload
Reloading current modules
......
```

After allocation:

```
0:001> !heap -s
LFH Key : 0x156356e0

Termination on corruption : ENABLED
  Heap     Flags   Reserv  Commit  Virt   Free  List   UCR  Virt  Lock  Fast
          (k)     (k)     (k)     (k)    length   blocks cont. heap
-------------------------------------------------------------------------------
00520000 00000002   1024    112     1024     8     1     1     0     0    LFH
007e0000 00001002  1019328 1012444 1019328 131    68    67     0     0    LFH
-------------------------------------------------------------------------------
```