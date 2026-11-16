![](bbox=[0.14, 0.08, 0.46, 0.16])

Figure 3.13 Aggregation of QoS Trust Recommendations.

P(E), and A and B are two observer nodes about event X. Their observations are represented as m<sub>A</sub>(X), m<sub>B</sub>(X). The combination of these two observations can be calculated using Equation (13).

```
m_{A,B}(X) = \frac{\Sigma_{P \cap Q=X} m_A(P) m_B(Q)}{1 - K} (13)
```

where the constant K is defined as K = \Sigma_{P \cap Q = \emptyset} m_A(P) m_B(Q).

# 3.4.3.2 DST Example

In Figure 3.13, node S is taking a trust recommendation from nodes P and Q about node D. The trust recommendation is in the form (T, T̄, U), i.e. trust, distrust, and uncertainty, respectively. Here nodes P and Q trust recommendations on node D are {0.7, 0.2, 0.1} and {0.3, 0.5, 0.2}, respectively. These recommendations are multiplied with their trust values.

Node S has 0.9 trust on P, so P's trust is recalculated as

```
m<sub>P</sub>(T) = T<sub>P</sub> × 0.7 = 0.63
m<sub>P</sub>(T̄) = T<sub>P</sub> × 0.2 = 0.18
m<sub>P</sub>(U) = T<sub>P</sub> × 0.1 = 0.09
```

Node S has 0.8 trust on P, so Q's trust is recalculated as

```
m<sub>Q</sub>(T) = T<sub>Q</sub> × 0.3 = 0.24
m<sub>Q</sub>(T̄) = T<sub>Q</sub> × 0.5 = 0.40
m<sub>Q</sub>(U) = T<sub>Q</sub> × 0.2 = 0.16
```

The aggregation of P,Q node recommendations on node D is evaluated as in Equation (21).