```
qc.append(gate4, [10 ,23 ,24 ,25, 9])
#B on C
qc.cswap(9,3,8)
#Reset WM
qc.append(gate4, [10 ,23 ,24 ,25, 9])
#Restore descriptor
qc.x(24)
qc.x(23)
```

```
# Moving C
qc.x(25)
qc.append(gate4, [10 ,23 ,24 ,25, 9])
#C on A
qc.cswap(9,6,2)
#Sec then part with changed descriptor
#Reset WM
qc.append(gate4, [10 ,23 ,24 ,25, 9])
qc.x(25)
#Fetch second superposition
qc.x(25)
qc.x(23)
qc.append(gate4, [10 ,23 ,24 ,25, 9])
# C on B
qc.cswap(9,6,5)
#Reset WM
qc.append(gate4, [10 ,23 ,24 ,25, 9])
#Restore descriptor
qc.x(23)
qc.x(25)
```

#We have only six rules, but eight possible paths!!!
#To get rid of the initial state we will move C again!

```
# Moving C Again
qc.x(24)
qc.x(25)
qc.append(gate4, [10 ,23 ,24 ,25, 9])
# A clear goes to high of B
qc.cswap(9,6,2)
#Sec then part with changed descriptor
#Reset WM
qc.append(gate4, [10 ,23 ,24 ,25, 9])
qc.x(25)
qc.x(24)
#Fetch second superposition
qc.x(23)
qc.x(24)
qc.x(25)
qc.append(gate4, [10 ,23 ,24 ,25, 9])
# C clear goes to high of B
```