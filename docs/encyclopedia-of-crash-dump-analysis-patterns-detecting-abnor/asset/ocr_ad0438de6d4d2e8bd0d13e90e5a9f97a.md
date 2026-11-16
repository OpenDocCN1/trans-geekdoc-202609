# Spike Interval

Sometimes, when an application is sluggish, periodically consumes CPU, it is possible to create a set of consecutive memory dumps of the same process to see the temporal development of any thread CPU consumption and figure out potential spike interval(s). For example, the following diagram was plotted from !runaway WinDbg command output for thread #1:

![](bbox=[0.2, 0.23, 0.8, 0.44])

The 3rd and the 5th user process memory dumps in addition to increased CPU consumption also had corresponding non-waiting stack trace frames caught while executing some CPU instructions in ModuleA (not preempted with saved context). The first memory dump (the first left bar) with 437 ms user time spent out of 629 ms elapsed time also had a non-waiting stack trace, but we consider it a normal application startup CPU consumption spike.