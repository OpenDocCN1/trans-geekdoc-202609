# Five Pennies Nim Game ■ 165

| | 0 | 1 | 2 | 3 | 4 | 5 | |
|---|---|---|---|---|---|---||
| 0 | | 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | | RULES_1 | 2 | 2 | 3 | 3 | 3 |
| 2 | | | IF_2 | 4 | 4 | 4 | 4 |
| 3 | | | | RULES_2 | 5 | 5 | 5 |
| 4 | | | | | IF_21 | 6 | 6 |
| 5 | | | | | | | 7 | 7 |
| 6 | | | | | | | | 8 | 8 |
| 7 | | | | | | | | 9 | 9 |
| 8 | | | 10 | 10 | 10 | 10 | | |
| 9 | | | | | | | | 11 | 11 |
| 10 | | | | | | | | 12 | 12 |
| 11 | | | | 13 | | | | |

**Figure 12.3** The circuit for the five pennies nim game representing the quantum tree search for the depth two.

```
qc.append(rules_depth1(),range(8))
qc.append(if_depth2(),range(11))
qc.append(rules_depth2(),range(13))
qc.append(oracle(),range(14))
qc.append(rules_depth2_inv(),range(13))
qc.append(if_depth2_inv(),range(11))
qc.append(rules_depth1_inv(),range(8))
qc.barrier()
qc.h(13)
qc.barrier()
qc.append(Grover(),range(13))
```

```
qc.measure(6,0)
qc.measure(7,1)
qc.measure(11,2)
qc.measure(12,3)
```

```
qc.draw(fold=200)
```

```
simulator = Aer.get_backend('qasm_simulator')
result=execute.execute(qc,shots=1000).result()
counts = result.get_counts()
print("nTotal count are: ",counts)
plot_histogram(counts)
```

The resulting histogram represents the measured path descriptor of the depth two after one rotation of Grover's amplification of the marked states with one penny.
**Figure 12.4.**