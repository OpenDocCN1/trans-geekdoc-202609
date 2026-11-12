Figure 8. Membership Function of (a) Temperature, (b) Soil Moisture, and (c) Humidity

![](bbox=[0.115, 0.165, 0.85, 0.415])

```
$$T_{OP} (X)=\left\{\begin{array}{ l l }
0, & X \le 12 \\
\frac{X-12}{0.5}, & 12 \le X \le 15 \\
1, & 15 \le X \le 28 \\
\frac{30-X}{0.5}, & 28 \le X \le 30
\end{array}\right.$$ (3)
```

```
$$T_{H} (X)=\left\{\begin{array}{ l l }
0, & X \le 28 \\
\frac{X-28}{0.5}, & 28 \le X \le 30 \\
1, & X \ge 30
\end{array}\right.$$ (4)
```

```
$$SH_{L} (X)=\left\{\begin{array}{ l l }
1, & X < 4 \\
\frac{(5-X)}{0.5}, & 4 \le X \le 5 \\
0, & X \ge 5
\end{array}\right.$$ (5)
```