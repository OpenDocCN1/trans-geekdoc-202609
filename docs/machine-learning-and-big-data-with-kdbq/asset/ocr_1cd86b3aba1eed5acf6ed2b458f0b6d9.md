# 550

# MACHINE LEARNING

Let us extract from the table outMAB1 several invariants: the counter of steps, the steps chosen in a given step, the total pay-off after given number of steps, and the average pay-offs for every arm after given number of steps:

```
select counter,strategy,payoff, p0: payoffs[0], p1: payoffs[1], p2:
payoffs[2] from select counter, {{bucket,x] bucket[minBound]]x{
bucket}; {each avg x each payoffs, payoff:avg each rate}
pays, last step chosen from outcomeMAB1 i>0
```

| | strategy payoff | p0 | p1 | p2 |
|---|---|---|---|---||
| 1 | | 1.400526 | ∅ | ∅ | 1.400526 |
| 2 | ∅ | 0.798637 | 0.180226 | ∅ | 1.400526 |
| 3 | | 0.632832 | 0.182266 | 0.318853 | 1.400526 |
| 4 | | 0.579608 | 0.299602 | 0.318853 | 1.400526 |
| 5 | | 0.590738 | 0.411828 | 0.318853 | 1.400526 |
| 6 | | 0.595476 | 0.493406 | 0.318853 | 1.400526 |
| 7 | | 0.646329 | 0.493406 | 0.318853 | 1.164042 |
| 8 | | 0.834804 | 0.621436 | 0.318853 | 1.492412 |
| 9 | | 0.848627 | 0.567813 | 0.318853 | 1.494212 |
| 10 | | 0.916064 | 0.567813 | 0.318853 | 1.494732 |
| 11 | | 1.023471 | 0.567813 | 0.318853 | 1.620034 |
| 12 | | 1.117768 | 0.567813 | 0.318853 | 1.829212 |
| 13 | | 1.138738 | 0.567813 | 0.824727 | 1.829221 |
| 14 | | 1.163473 | 0.567813 | 0.824752 | 1.829221 |
| 15 | | 1.145258 | 0.621436 | 0.824752 | 1.829221 |
| 16 | | 1.139196 | 0.651938 | 1.117699 | 1.698867 |
| 17 | | 1.181966 | 0.621436 | 1.117699 | 1.698867 |
| 18 | | 1.162579 | 0.651938 | 1.117699 | 1.698867 |
| 19 | | 1.109787 | 0.590194 | 1.117699 | 1.698867 |
| 20 | | 1.075534 | ∅ | 0.970949 | 1.698867 |

In the last query, we have included condition where $i$ $	extgreater; 0$. We leave for readers to answer why we make this constraint.

Let us review the results visually. Figure 28.1 depicts a sequence of choices, bucket[strategy], as they have been chosen consecutively by running the algorithm. The picture confirms that the first 10% of the sample was an exploratory phase as demonstrated by switching the arms while the rest of the time has been running the best option – the third arm.

Further, Figure 28.2 depicts a sequence of average pay-offs for choices taken. The figure shows the pay-offs as they have been revealed during the lifetime of the algorithm. The algorithm at every step makes a decision based on the set of values available up to the given step. The figure shows the performance of the overall strategy – black line – and for each arm separately: arm 1 (grey), arm 2 (light grey), and arm 3 (dark grey), respectively. The pay-off during the exploratory phase at the beginning is quite volatile. The pay-offs then stabilises during the exploitation phase where the total pay-off averages towards the optimal arm, arm number 3.