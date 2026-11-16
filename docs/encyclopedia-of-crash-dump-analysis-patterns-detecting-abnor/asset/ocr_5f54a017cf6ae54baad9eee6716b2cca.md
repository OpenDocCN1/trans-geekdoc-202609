# Session Pool

Although we briefly mentioned session pool in Insufficient Memory (kernel pool) pattern (page 535) we factored it into a separate (sub)pattern to provide WinDbg commands for analysis of possible leaks. The following output shows the sequence of commands that gives an idea although the example itself was taken from a healthy dump so no highlights in bold font (we had seen leaks in session pool happening mostly in 32-bit cases):

```
1: kd> !vm 4

Terminal Server Memory Usage By Session:

Session ID 0 @ ffffff8800324d000:
Paged Pool Usage:      4128K
Commit Usage:          7488K

Session ID 1 @ ffffff88002f65000:
Paged Pool Usage:      32852K
Commit Usage:         36488K
```

```
1: kd> !session
Sessions on machine: 2
Valid Sessions: 0 1
Error in reading current session
```

```
1: kd> !session -s 1
Sessions on machine: 2
Implicit process is now ffffffa80`07d79730
Using session 1
```

```
1: kd> !pooled 8
Sorting by Session Tag

Pool Used:
NonPaged       Paged
Tag  Allocs   Used   Allocs   Used
TOTAL          4      4208   9500   33475120
[...]
```