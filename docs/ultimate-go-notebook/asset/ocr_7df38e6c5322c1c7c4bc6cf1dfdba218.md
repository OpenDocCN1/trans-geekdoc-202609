# Figure 12.17

User Task: type=newsfeed-0000.xml,latency >= 2.511886ms,latency <= 3.981071ms

Search log text: [Submit]

| When | Elapsed | Goroutine ID | Events |
| --- | --- | --- | --- |
| 0.000024599 | 3296533ms | 21 | Task 1 (goroutine run) (id 1, parent 0) created |
| 0.000926559 | 28160 | 21 | region OpenFile started (duration: 68.934µs) |
| 0.000954719 | 75014 | 21 | region ReadAll started (duration: 687.839µs) |
| 0.001029733 | 695371 | 21 | region Unmarshal started (duration: 2.489759ms) |
| 0.00103106 | 2493092 | 21 | region Contains started (duration: 7.92µs) |
| 0.004223192 | | 9894 | 21 | task end |
| 0.004223092 | | | | GC:0 |

This page breaks down each region from this task and how long it took. It also provides information GC time at the bottom.

That final gives me this same information but in graph.

# Figure 12.18

![](bbox=[0.119, 0.413, 0.884, 0.658])

Now I can see when the file was processed and more information from the tracing tool.