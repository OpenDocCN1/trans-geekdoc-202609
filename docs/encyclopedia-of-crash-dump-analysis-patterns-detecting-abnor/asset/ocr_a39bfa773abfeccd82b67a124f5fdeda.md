Let's look at one of such entries (the first and the last qword values are pointers):

```
0:000> dq 000000db`56a57da0 L3
000000db`56a57da0 ffffff901`440deaf0 400a6d0a`00002c30
000000db`56a57db0 000000db`56a4f3b00

0:000> dw 000000db`56a57da0 L3*4
000000db`56a57da0 eaf0 440d f901 ffff 2c30 0000 6d0a 400a
000000db`56a57db0 3b00 564f 00db 0000
```

Applying 7f to wType word 400a gives us 0xa or 10 which is a font handle:

```
0:000> ? 400a & 7f
Evaluate expression: 10 = 00000000`0000000a
```

Since there are entries from other processes from the same session in this table assessing the handle leak visually is difficult so we wrote a WinDbg script that goes from the first non-zero _pKernelAddress_ ($t0) to the first zero entry and for the given _wProcessId_ ($tpid) counts the number of entries ($t1) and the number of entries ($t3) for the given wType ($t2). The script also counts the total entries till the first zero one ($t4):

```
.while (qwo(@$t0)) { .if (wo(@$t0+8) == @$tpid) {r $t1 = @$t1+1; .if (((qwo(@$t0+8) >> 0n48) & 7f) == @$t2) {r $t3 = @$t3+1}; r $t0 = @$t0+3*8; r $t4 = @$t4+1}
```

To execute it we prepare the variables:

```
0:000> r t0=000000db`56a500f0

0:000> r t1=0

0:000> r t2=a

0:000> r t3=0

0:000> r t4=0
```

```
0:000> .while (qwo(@$t0)) { .if (wo(@$t0+8) == @$tpid) {r $t1 = @$t1+1; .if (((qwo(@$t0+8) >> 0n48) & 7f) == @$t2) {r $t3 = @$t3+1}; r $t0 = @$t0+3*8; r $t4 = @$t4+1}
```

After execution we get the modified variables that show us that the total consecutive non-zero handle table entries is 21464, the total number of entries for the current process is 9990, and the total number of fonts is 9982:

```
0:000> ? $t0
Evaluate expression: 942052007216 = 000000db`56acdd30

0:000> ? $t1
Evaluate expression: 9990 = 00000000`00002706
```