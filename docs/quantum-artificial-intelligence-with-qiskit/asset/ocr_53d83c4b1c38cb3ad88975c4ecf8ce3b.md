![](bbox=[0.218, 0.113, 0.735, 0.462])

Figure 5.4 Quantum circuit representing the generation of two instantiations of rules in the 3-puzzle task of depth one search.

The second rule is represented accordingly.

```
#If rule (2) for empty at 2, 3 -> 6, 7 or 0, 1
#Search empty state with the descriptor
qc.ccx(10,13,8)
#Execute 1st then part
qc.cswap(8,2,6)
qc.cswap(6,3,7)
#Sec then part with changed descriptor
#Reset Flag
qc.ccx(10,13,8)
#Fetch second superposition
qc.x(13)
qc.ccx(10,13,8)
#Execute 2th then part
qc.cswap(8,0,2)
qc.cswap(8,1,3)
#Reset Flag
qc.ccx(10,13,8)
#Restore descriptor
qc.x(13)
qc.barrier()
```