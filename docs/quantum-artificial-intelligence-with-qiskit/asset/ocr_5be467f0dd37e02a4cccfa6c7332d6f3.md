```
# Empty Space in edge, 3 movements
qc.append(gate, [20, 21, 22, 23, 42])
#Empty Space in corner, 2 movements
qc.append(gate, [24, 25, 26, 27, 43])
#Empty Space in edge, 3 movements
qc.append(gate, [28, 29, 30, 31, 44])
#Empty Space in corner, 2 movements
qc.append(gate, [32, 33, 34, 35, 45])
qc.name="IF" qc
return qc
```

For the empty space in the center, there are four instantiations corresponding to the four movements.

```
def result():
qc = QuantumCircuit(48)
#Flag 36
#Path Descriptor 46, 47
#Trace 37-45
flag_gate = MCXGate(3)
```

```
#If then rule move right, for empty at 16, 17, 18, 19 -> 12, 13, 14, 15
qc.append(flag_gate, [41, 46, 47, 36])
#Move
qc.cswap(36,16,12)
qc.cswap(36,17,13)
qc.cswap(36,18,14)
qc.cswap(36,19,15)
#Clear Flag
qc.append(flag_gate, [41, 46, 47, 36])
```

```
#If then rule move left, for empty at 16, 17, 18, 19 -> 20, 21, 22, 23
qc.x(46)
qc.append(flag_gate, [41, 46, 47, 36])
#Move
qc.cswap(36,16,20)
qc.cswap(36,17,21)
qc.cswap(36,18,22)
qc.cswap(36,19,23)
#Clear Flag
qc.append(flag_gate, [41, 46, 47, 36])
```

```
#If then rule move up, for empty at 16, 17, 18, 19 -> 28, 29, 30, 31
qc.x(47)
qc.append(flag_gate, [41, 46, 47, 36])
#Move
qc.cswap(36,16,28)
qc.cswap(36,17,29)
qc.cswap(36,18,30)
qc.cswap(36,19,31)
#Clear Flag
```