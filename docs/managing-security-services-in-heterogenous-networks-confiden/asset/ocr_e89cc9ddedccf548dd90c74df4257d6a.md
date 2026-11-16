![](bbox=[0.146, 0.082, 0.853, 0.359])

Figure 3.3 Fuzzy inference QoS trust model.

In further sections, first QoS metrics are evaluated and then fuzzy logic (fuzzification, defuzzification, and fuzzy rule base) is discussed to compute the trust value.

# 3.4.1.1 Computation of QoS Parameters

In [5], the computation of LET, energy, bandwidth, and reliability is discussed.

Estimation of LET: The LET between two nodes is calculated based on their present locations, velocity, and moving direction. It is estimated using Equation (7).

```
LET = \frac{-(ab + cd) + \sqrt{(a^2 + c^2)r^2 - (ad - cb)^2}}{(a^2 + c^2)} (7)
```

| Item | Definition |
|---|---|
| Table 3.1 LET Notations | |
| a | v1 cos θ1 - v2 cos θ2 |
| b | x1 - x2 |
| c | v1 sin θ1 - v2 sin θ2 |
| d | y1 - y2 |
| (x1, y1) and (x1, y1) | are node locations |
| v1 and v2 | are their velocities |
| θ1 and θ2 | are their directions |