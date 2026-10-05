# Basic Computer Coding: PHP

+   - ru_oublock: block output operations
- ru_inblock: block input operations
- ru_msgsnd: messages sent
- ru_msgrcv: messages received
- ru_maxrss: maximum resident set size
- ru_ixrss: integral shared memory size
- ru_idrss: integral unshared data size
- ru_minflt: page reclaims
- ru_majflt: page faults
- ru_nsigals: signals received
- ru_nvcsw: voluntary context switches
- ru_nivcsw: involuntary context switches
- ru_nswap: swaps
- ru_utime,tv_use: user time (microseconds)
- ru_utime.tv_sec: user time (seconds)
- ru_stime,tv_use: system time used (microseconds)
- ru_stime.tv_sec: system time used (seconds)

Microsecond is an SI unit of time equal to one million (0.000001) or 10^-6 of a second. To see how much CPU power the script has consumed, we need to look at the 'user time' and 'system time' values. The seconds and microseconds portions are provided separately by default. You can divide the microseconds by 1 million, and add it to the seconds value, to get the total seconds as a decimal number.

Let's see an example:

```
// sleep for 3 seconds (non-busy)
sleep(3);
```