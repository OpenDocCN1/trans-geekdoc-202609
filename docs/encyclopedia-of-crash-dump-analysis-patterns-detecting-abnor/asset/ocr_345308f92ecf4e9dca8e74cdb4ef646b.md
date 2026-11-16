# Predicate

Sometimes we need to narrow general stack trace collection to a few threads that satisfy some predicate^198, for example, all threads with kernel time spent greater than some value, or all suspended threads, or all threads that wait for a specific synchronization object type. This can be implemented using WinDbg scripts^199 and debugger extensions.

# Comments

An example here can be service tags in TEB.SubProcessTag to identify threads from specific service in svchost.exe.

To list 32-bit stack traces from the specific WOW64 process:

```
!for_each_thread ".thread @#Thread; r $t0 = @#Thread; .if (@@c++(((nt!_KTHREAD *)@$t0)->Process) == ProcessAddress) {.thread /w @#Thread; .reload; kv 256; .effmach AMD64 }"
```

198 http://en.wikipedia.org/wiki/Predicate_(mathematical_logic)

199 Two WinDbg Scripts That Changed the World, Memory Dump Analysis Anthology, Volume 7, page 32