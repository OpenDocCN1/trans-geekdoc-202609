```
```
.text:00407C90 sub_407C90:
.text:00407C90
.text:00407C90 var_10= -0x10
.text:00407C90 var_8= -8
.text:00407C90 var_4= -4
.text:00407C90
.text:00407C90 li $gp, 0x4B540
.text:00407C90 addiu $gp, $t9
.text:00407C9C addiu $sp, -0x20
.text:00407CA0 sw $ra, 0x20+var_4($sp)
.text:00407CA4 sw $s0, 0x20+var_8($sp)
.text:00407CA8 sw $gp, 0x20+var_10($sp)
.text:00407CAC li $v0, 0x104C
.text:00407CB0 syscall 0
```
```

Figure 25-24 Renaming syscalls on MIPS

You can find an excellent syscall reference for multiple architectures at https://w3challs.com/syscalls/. Kudos to whoever uploaded it.

When you’re dealing with syscalls in ARM, the syntax is different. In newer versions, the svc command is used, and the service ID is hardcoded for every call. Figure 25-25 shows an ARM version of the okiru malware (ad52832a507cde6521e11556f7cbb95) with the ID 0x900005, which in this case corresponds to the “open” function call.

```
```
:00010958 sub_10958 ; CODE XREF: sub 88
:00010958 ; sub 8DC0+1F0↑p ..
:00010958 var_18 = -0x18
:00010958 arg_0 = -0xC
:00010958 var_2 = -8
:00010958 var_3 = -4
:00010958
:00010958 STMFD SP!, {R1-R3}
:0001095C STMFD SP!, {R4,LR}
:00010960 SUB SP, SP, #4
:00010964 LDR R1, [SP,#0x18+var_r1]
:00010968 ANDS R3, R1, #0x40
:0001096C ADDNE R3, SP, #0x18+var_r3
:00010970 STRNE R3, [SP,#0x18+var_18]
:00010974 LDR R3, [SP,#0x18+var_r2]
:00010978 MOV R2, R3,LSL#16
:0001097C MOV R2, R2,LSR#16
:00010980 SVC 0x900005
:00010984 CMN R0, #0x1000
:00010988 MOV R4, R0
:0001098C BLS loc_109A0
:00010990 BL sub_10DAC
:00010994 RSB R3, R4, #0
:00010998 STR R3, [R0]
:0001099C MOV R4, #0xFFFFFFFF
:000109A0
```
```

Figure 25-25 Renaming syscalls on ARM