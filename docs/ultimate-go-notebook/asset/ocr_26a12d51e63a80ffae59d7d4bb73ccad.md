# Listing 5

```
gc 1406 86.07s 11%: 0.051+1.8+0.076 ms clock, 0.61+2.0/2.5/0+0.91 ms cpu,
8->16 MB, 13 MB goal, 12 P
```

```
// Memory
8MB: Heap memory in-use before the Marking started
11MB: Heap memory in-use after the Marking finished
6MB: Heap memory marked as live after the Marking finished
13MB: Collection goal for heap memory in-use after Marking finished
```

Listing 5 shows how the collection started 2ms after the start of the previous collection (0.068s to 6.070s) even though the memory in-use had only reached 8MB of the 12MB that was allowed. It's important to note, if the collector decides it to start a collection earlier, it will. In this case, it probably started earlier because the application is allocating heavily and the collector wanted to reduce the amount of Mark Assist latency during this collection.

Two more things of note. The collector stayed within its goal time. The amount of memory in-use after Marking finished was 11MB not 13MB, 2 MB less. The amount of heap memory marked as live after Marking finished was the same as 6MB.

As side note, you can get more details from the GC trace by adding the gctrace=1 flag. This causes the collector to print information about the internal state of the concurrent p.

# Listing 6

```
$ export GODEBUG=gtrace=1,gcpracetrace=1 .app
```

```
Sample output:
gc 5 80.07is 0%: 0.018+0.46+0.071 ms clock, 0.14+0.38/0.14+0.56 ms cpu,
29->29 MB, 30 MB goal, 8 P
```

```
pacer: sweep done at heap size 29MB; allocated OMB of spans; sweep 3752
pages at +6.18355e-004 pages/byte
```

```
pacer: assist ratio=+1.232155e-000 (scan 1 MB in 70->71 MB) workers=2+0
pacer: H.m_prev=30488736 h_t=+2.334071e-001 H=37605024 h_a+=1.409842+000
h_a=73473040 g_h+=1.000000+000 H_g=69977472 u_a+=2.500000e-001
u_g=2.500000e-001 W_a=308200 goalΔ+=7.665929e-001 actualΔ+=1.176435e+000
u_a_u=1.100000e+000
```

Running a GC trace tells you a lot about the health of the application and the
pace of the collector. The pace at which the collector is running plays an important
role in the collection process.