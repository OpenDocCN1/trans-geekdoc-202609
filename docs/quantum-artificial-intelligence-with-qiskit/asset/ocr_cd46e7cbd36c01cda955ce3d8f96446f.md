```
qc.x(23)
qc.append(gate4, [17 ,23 ,24 ,25 , 9])
qc.swap(9,2,8)
#Clear WM
qc.append(gate4, [17 ,23 ,24 ,25 , 9])
qc.x(25)
qc.x(24)
qc.x(23)
```

```
#In the same way
#BA tower and block C
#CA tower and block B
#CB tower and block A
#AC tower and block B
#AB tower and block C
...
qc.name="R_TB"
return qc
```

# 11.1.2 Oracle

The goal states AC and B is represented by the oracle

```
def oracle():
    qc = QuantumCircuit(27)
    #Specify goal state
    gate = MCGate(3)
    #AC B
    qc.append(gate,[3, 5, 8, 26])
    qc.name="0"
    return qc
```

# 11.1.3 Architecture

The quantum circuit for the ABC blocks of the depth search 1, (see Figure 11.3)

```
qc = QuantumCircuit(27)
#State Preparation 0-8
```

```
#Working Memory, Flag 9
#1St Trace (ten) 10-22 Rule Classes
```

```
#1St Descriptors in superposition, one, three, six possible actions
represented by three qubit
#Possible instantiations
```

```
qc.h(23)
qc.h(24)
qc.h(25)
```