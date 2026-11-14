```
...
[185,-,-] Performing iteration
[*] Fuzzing: DataTRUN.DataElement_1
[*] Mutator: UnicodeBadUtf8Mutator
-- Caught fault at iteration 185, trying to reproduce --
[185,-,-] Performing iteration
[*] Fuzzing: DataTRUN.DataElement_1
[*] Mutator: UnicodeBadUtf8Mutator
-- Reproduced fault at iteration 185 --
[186,-,-] Performing iteration
[*] Fuzzing: DataTRUN.DataElement_1
[*] Mutator: UnicodeBadUtf8Mutator
...
```

As you can see, the fuzzer found an exception and was able to reproduce it.

# Crash Analysis

During a fuzzing session, if everything is going as planned, there should be some logs for
the target application crashes. Depending on the fuzzer used, different traces of a crash will
be available. Here are some of the usual traces of crashes available:

+   • Sample file or data records that can be used to reproduce the crash. In the case of a
+   file fuzzer, a sample file that was used for testing will be stored and marked for
+   review. In the case of a network application fuzzer, a PCAP file might be recorded
+   and stored when an application crash was detected. Sample files and data records are
+   the most rudimentary way to keep track of application crashes; they provide no
+   context about the crash.
+   • Application crash log files can be collected in many ways. Generally, a debugger is
+   used to monitor the target application state and detect any sign of a crash. When the
+   crash is detected, the debugger will collect information about the CPU context (for
+   example, the state of registers and stack memory), which will be stored along with the
+   crash sample file. The crash log is useful for getting a general idea about the type of
+   crash as well as for crash clustering. Sometimes an application can crash hundreds of
+   times because of the same bug. Without some context about the crash, it is very hard
+   to determine how much different the vulnerabilities are. Crash logs provide a great
+   first step in filtering and grouping crashes into unique vulnerabilities.
+   • When an application crash is detected, many custom scripts can be run that collect
+   specific types of information. The easiest way to implement such scripts is by
+   extending the debugger. !exploitable is one such useful debugger extension. It was
+   developed by Microsoft for WinDbg and can be used for checking whether or not a
+   crash is exploitable. It should be noted that even though !exploitable is useful and