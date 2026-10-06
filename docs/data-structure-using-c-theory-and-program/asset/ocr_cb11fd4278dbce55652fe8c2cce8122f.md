# Chapter 7 Graphs

| V1 | V2 | V3 | V4 |
|---|---|---|---||
| V1 | V1V2V1 | V1V2 | V1V2V3 | V1V2V3V4 |
| V2 | V2V1 | V2V1V2 | V2V3 | V2V3V4 |
| V3 | V3V2V1 | V3V2 | V3V4V3 | V3V4 |
| V4 | V4V3V1 | V4V3V2 | V4V3 | V4V3V4 |

$Q_1(1, 3) = Minimum [Q_0(1, 3), Q_0(1, 1) + Q_0(1, 3)]
= Minimum(\infty, \infty)$
= \infty$

$Q_1(2, 2) = Minimum [Q_0(2, 2), Q_0(2, 1) + Q_0(1, 2)]
= Minimum(\infty, 3+2)
= 5$

$Q_2(3, 1) = Minimum [Q_1(3, 1), Q_1(3, 2) + Q_1(2, 1)]
= Minimum(\infty, 6+3)
= 9$

$Q_3(1, 4) = Minimum [Q_2(1, 4), Q_2(1, 3) + Q_2(3, 4)]
= Minimum(9, 6+2)
= 8$

# Program: Write a program to modified Warshall’s Algorithm to find shortest path matrix

```
#include<stdio.h>
#define infinity 9999
#define MAX 20

main()
{
    int i
```