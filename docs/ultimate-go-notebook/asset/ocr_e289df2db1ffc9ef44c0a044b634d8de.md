that is 4 meg of memory.

If I want more clarity on this number, I can use GDEBUG and run the program
again.

# Listing 12.8

```
$ time GDEBUG=gctrace=1 ./trace > .out

gc 1 @01.06s 0%: 0.020+0.024+0.025 ms clock, 0.32+0.18/0.12+0.39 ms cpu,
4->4o MB, 5 MB goal, 16 P
gc 2 @00.29s 0%: 0.030+0.023+0.002 ms clock, 0.49+0.15/0.17/0.001+0.037 ms
cpu, 4->4o MB, 5 MB goal, 16 P
gc 3 @08.04s 0%: 0.033+0.026+0.019 ms clock, 0.52+0.15/0.059+0.31 ms cpu,
cpu, 4->4o MB, 5 MB goal, 16 P
gc 73 @82.79s 0%: 0.043+0.046+0.040 ms clock, 0.70+0.24/0.18/0.25+0.65 ms
cpu, 4->4o MB, 5 MB goal, 16 P
gc 74 @82.80s 0%: 0.043+0.035+0.002 ms clock, 0.69+0.28/0.37+0.16+0.042 ms
cpu, 4->4o MB, 5 MB goal, 16 P
gc 75 @82.814s 0%: 0.032+0.028+0.017 ms clock, 0.52+0.20/0.26+0.026+0.28 ms
cpu, 4->4o MB, 5 MB goal, 16 P
```

2021/05/12 15:17:24 Searching 4000 files, found presiden 2800 times.

Sure enough, the heap was maintained at 4 meg and all the memory was transient
s each GC resulted in the number of live values to be zero. Exactly what I am
seeing in the trace.

What I really need is more information about the GCCs. It's not about 1 GC, it's
all about the GC's that needed to take place. I can get this information by using the
selection tool and double clicking on any blue line.

# Figure 12.6

| 275 items selected. | Slices (275) |
| Name | Wall Duration | Self time | Average Wall Duration | Occurrences |
| GC | 106,639,993 ns | 106,639,993 ns | 387,72 ns | 275 |

+   - Selection start
  - 15,245,706 ns
- Selection extent
  - 2,647,454,596 ns

+   - Start
- CPU Duration
- Duration
- CPU Self Time

These numbers are helpful in determining how much the GC is doing in the
execution of the program. With these numbers I have a baseline for the program's
performance.