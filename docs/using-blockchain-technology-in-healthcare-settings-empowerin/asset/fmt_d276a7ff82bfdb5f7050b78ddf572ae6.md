
Proof: Suppose is an efficient solution to the FMOLPP with cut is zero. Assume that is not an optimal solution to the problem according to the order relation . Therefore, there is a feasible solution, , of the FMOLPP such that

(13.9)

which is in contradiction to the efficiency of     for the problem with .

### Theorem 4
According to the order relation any efficient solution to the problem with is an optimal solution to the FMOLPP.

Proof: Suppose is an efficient solution to the problem when cut is zero. Assume that is not an optimal solution to the problem according to the order relation . Therefore, there is a feasible solution, , of the FMOLPP such that

(13.10)

which is in contradiction to the efficiency of     for the FMOLPP with .

### Theorem 5
According to the order relation any efficient solution to the problem with is an optimal solution to the problem.

Proof: Suppose is an efficient solution to the problem when cut is one. Assume that is not an optimal solution to the problem according to the order relation . Therefore, there is some feasible solution, , of the problem such that

(13.11)

which is our contradiction to the efficiency of     for the FMOLPP with and the proof is completed.

### Theorem 6
According to the order relation any optimal solution to the problem with is an LM-efficient solution to the FMOLPP.

Proof: Assume that is an optimal solution to the weighting problem with a positive weight coefficient. According to the order relation , it is not a Pareto optimal solution to the existing problem. Therefore, by Theorem 1, there is a feasible solution, , of the MOLPP, such that

(13.12)

Since    , we have thus, it contradicts the assumption that must be the optimal solution.

### Theorem 7
According to the order relation the unique optimal solution to the problem with is an LM-efficient solution to the FMOLPP.

Proof: Assume that is a unique optimal solution to the weighting problem with a positive weight coefficient. Therefore, by Theorem 6, there is a feasible solution, , of the MOLPP such that from Theorem 6, we can write as the following.

(13.13)

and

(13.14)

Since , we have ; thus, this contradicts the assumption that must be the unique optimal solution.

Similarly, we can prove the order relation     is an optimal and unique optimal to the weighting problem as well as it is an efficient solution to the F MOLPP.

### Theorem 8
Similar to the order relation the solution to the weighting problem is properly optimal if all weighting coefficients are positive.

Proof: Assume that is an optimal solution to the weighting problem with a positive weight coefficient. By the Theorem 7, we have to express that the solution is optimal. We have to show that is properly optimized. Assume that .

Let us contradict the above. Assume is not properly optimized for weighting problems. Then, from Theorem 7, and , we have

(13.15)

where .

For all ,

(13.16)

Multiplying both sides with

(13.17)

where

(13.18)

that means

(13.19)

(13.20)

The contradiction principle of our assumption that must be the solution to the weighting problem and that must be properly optimized.

### Theorem 9
If is an optimal solution to the weighting problem, then it is an exact optimal solution to the FMOLPP.

Proof: By the contradiction, let be an optimal solution to a given FMOLPP, according to the order relation and it is not the exact solution to the problem. There exists a feasible solution to the given problem.

Let , such that the minimization objective function of . By Theorem 7, we know that the weighting problem optimal solution is properly optimized. Regarding this, one of the prove can be center of TFN is getting the optimal solution to the weighting problem. Accordingly, we can prove that left and right also get optimal solutions to the FMOLPP by using the fuzzy weighted sum method.

Let the minimization problem of . Also, assume we have , and the objective function of left, center, and right are always greater than the objective value in .

(13.21)

By the contradiction principle, our assumption is that must be the solution to the FMOLPP and that must be the optimal solution.

## 13.6 Numerical example

In this section, we have employed the fuzzy weighted sum method to solve the given numerical example.

### EXAMPLE 1

The problem \[[37](#index_split_020.html#filepos1133641)\] is formulated as a FMOLPP. Such as the objective function, coefficient constraint, decision variable, and right-hand side vector are taken as TFNs.

subject to

(13.22)

where and

According to the given FMOLPP on TFNs, when we apply the fuzzy weighted sum method to find an optimal solution, it needs to perform left, center, and right computations of the FMOLPP. Therefore, FMOLP requirements to another parametric computation are the same. The crisp representation of TFNs possess two parameters (i.e., and . To find the efficient solution of the FMOLPP by using left, center, right, and parametric calculations, the weight value are taken from 0 to 1. The obtained results are listed in [Tables 13.1](#index_split_020.html#filepos1082079) and [13.2](#index_split_020.html#filepos1091088), whereas the final function values are listed in [Table 13.3](#index_split_020.html#filepos1100197). The results are compared with \[[37](#index_split_020.html#filepos1133641)\]. Graphical representation of TFNs of \[[37](#index_split_020.html#filepos1133641)\] and a proposed method are shown in [Figures 13.4](#index_split_020.html#filepos1110424) and [13.5](#index_split_020.html#filepos1110912). The objective function of the same are shown as [Figures 13.4](#index_split_020.html#filepos1110424) and [13.5](#index_split_020.html#filepos1110912).

### TABLE 13.1 Solutions for component and its parametric computation

| w || || || || || || |

| 0 || 0 || 1 || 3 || 0.9964 || 9 || 3 || 6.0356 |

| 0.1 || 0 || 0 || 3 || 0 || 8.9996 || 3 || 6.0356 |

| 0.2 || 0 || 0 || 3 || 0 || 0 || 3 || 6.0356 |

| 0.3 || 0 || 0 || 3 || 0 || 0 || 3 || 6.0356 |

| 0.4 || 0 || 0 || 3 || 0 || 0 || 3 || 6.0356 |

| 0.5 || 0 || 0 || 3 || 0 || 0 || 3 || 6.0356 |

| 0.6 || 0 || 0 || 3 || 0 || 0 || 3 || 6.0356 |

| 0.7 || 0 || 0 || 3 || 0 || 0 || 3 || 6.0356 |

| 0.8 || 0 || 0 || 3 || 0 || 0 || 3 || 6.0356 |

| 0.9 || 0 || 0 || 3 || 0 || 0 || 3 || 6.0356 |

| \[Original (created by authors)\] |

### TABLE 13.2 Optimal solutions for component and its parametric computation

| w || || || || || || |

| 0 || 1 || 2 || 3.6 || 1.0018 || 0 || 2 || 0.0001 |

| 0.1 || 1.5 || 2 || 3.6 || 1.5 || 0.0002 || 2 || 0.0001 |

| 0.2 || 1.5 || 2 || 3.6 || 1.5 || 3.6 || 2 || 0.0001 |

| 0.3 || 1.5 || 2 || 3.6 || 1.5 || 3.6 || 2 || 0.0001 |

| 0.4 || 1.5 || 2 || 3.6 || 1.5 || 3.6 || 2 || 0.0001 |

| 0.5 || 1.5 || 2 || 3.6 || 1.5 || 3.6 || 2 || 0.0001 |

| 0.6 || 1.5 || 2 || 3.6 || 1.5 || 3.6 || 2 || 0.0001 |

| 0.7 || 1.5 || 2 || 3.6 || 1.5 || 3.6 || 2 || 0.0001 |

| 0.8 || 1.5 || 2 || 3.6 || 1.5 || 3.6 || 2 || 0.0001 |

| 0.9 || 1.5 || 2 || 3.6 || 1.5 || 3.6 || 2 || 0.0001 |

| \[Original (created by authors)\] |

### TABLE 13.3 Optimal solutions of objective function

| w || Value || Value || Value || || || || Min |

| 0 || 6 || 23 || 45 || 6 || 36 || 23 || 18.1074 || 6 |

| 0.1 || 6.6 || 25.7 || 45 || 5.7 || 42.3 || 25.3 || 22.3324 || 5.7 |

| 0.2 || 7.2 || 28.4 || 45 || 5.4 || 41.76 || 27.6 || 26.5573 || 5.4 |
