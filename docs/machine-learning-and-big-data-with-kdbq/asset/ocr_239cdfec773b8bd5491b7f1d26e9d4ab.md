# 556

# MACHINE LEARNING

![](bbox=[0.104, 0.093, 0.895, 0.439])

**Figure 28.6** The sequence of average pay-offs for choices taken as perceived during the lifetime of the algorithm for the overall strategy (black), and for each arm separately – arm 1 (gray), arm 2 (light gray), arm 3 (dark gray) – using the decreasing exploration greedy algorithm performed in the following table:

it with the optimal strategy defined as a cumulative sum of the mean of arm 3. This is performed in the following table:

```
(1)select counter, payoffFirst:sum each raze payoffs from outcomeMAB1
    - where i>0) uj
(1)select counter, payoffRandom:sum each raze payoffs from outcomeMAB2
    - where i>0) uj
(1)select counter, payoffDecreasing:sum each raze payoffs from
    outcomeMAB3 where i>0) uj 1!([ counter: 1+ til 1000; payoffOptimal:
    1.5+til 1000)
```

Further, we calculate the convergence rate of the cumulative pay-offs of the three algorithms towards the optimal pay-off in the previous display:

```
(1)select counter, convergenceFirst:(sum each raze payoffs)%(1.5*
    - counter) from outcomeMAB1 where i>0) uj
(1)select counter, convergenceRandom:(sum each raze payoffs)%(1.5*
    - counter) from outcomeMAB2 where i>0) uj
(1)select counter, convergenceDecreasing:(sum each raze payoffs)%(1.5*
    - counter) from outcomeMAB3 where i>0)
```

Figure 28.7 depicts the cumulative pay-off of the three algorithms and the pay-off of the optimal strategy. The most optimal strategy seems to be the most straightforward