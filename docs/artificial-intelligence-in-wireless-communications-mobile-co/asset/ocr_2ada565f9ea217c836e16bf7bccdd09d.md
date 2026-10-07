# Artificial Intelligence in Wireless Communications

base, $d(q)$. The time of day is calculated similarly as an error between the current time, $t(p)$, and time in $t(q)$. The day of the week is handled differently in that the similarity is 1 if the day of the week, $D(p)$, is the same as the day of the week in the case base, $D(q)$. Otherwise, it is 0. A more complicated model could have a partial similarity that equates to 0.5 if $D$ and $D(q)$ are both weekdays or both weekends.

```
$s(p,q) = 1 - \frac{\frac{|d(p)-d(q)|}{d(q)}+rac{|t(p)-t(q)|}{t(q)}}{1 - D_{\Delta}}\nD_{\Delta} = \begin{cases} 1 & D(p)=D(q) \ 0 & D(p) \neq D(q) \end{cases} \quad (6.10)
```

The utility is based on the observables of the network service and is maximized by higher throughput, lower BER, latency, dropped calls, and blocked calls. This is related to the multiobjective problem where these different values cannot be directly compared or combined by differences in scale and importance to the situation. On the other hand, this problem is constrained to known services, unlike the general cognitive radio system, we have a known set of parameters and values. While knowledge is being built up by the case base, the system selects services based on the required QoS, that has already primed the decision making with desired values. We will ignore the BER and the throughput as an indirect measure of value. We can use this fact to build the utility measure of future systems. For each service $q$ in the case base, the cognitive radio measures the performance, as average throughput comparable to the advertised service of the case, $R(q)$ and latency, $L(q)$ during the connection. These values are directly comparable to the advertised service of the case, $R_s(q)$ and $L_s(q)$ for the throughput and latency, respectively. The radio would also keep track of the number of dropped calls, $C_d(q)$, and blocked calls, $C_b(q)$, to calculate a percentage of each value over the total number of connections made or attempted, $C$. The utility function in it can be built from the knowledge and assumptions. This function sums the error between the actual service and the proposed service as well as the percentage of dropped and blocked calls. The closer to 1, the better the utility of the service.

```
$u(q) = 1 - \frac{1}{4}\left(\frac{|\hat{R}-R_s(q)|}{R_s(q)}+rac{|\hat{L}-L_s(q)|}{L_s(q)}+\frac{C_B}{C(q)}+\frac{C_D}{C(q)}\right) \quad (6.11)
```

An aspect of the case-based approach that should become obvious as we discussed this example is the ability to use knowledge developed from other users to augment our own. Our example has discussed the use of past