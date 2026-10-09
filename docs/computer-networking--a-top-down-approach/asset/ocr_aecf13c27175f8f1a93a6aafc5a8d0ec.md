where packet loss occurred hasn’t changed much, then perhaps it’s better to more quickly ramp up the sending rate to get close to the pre-loss sending rate and only then probe cautiously for bandwidth. This insight lies at the heart of a flavor of TCP known as TCP CUBIC [Ha 2008, RFC 8312].

TCP CUBIC differs only slightly from TCP Reno. Once again, the congestion window is increased only on ACK receipt, and the slow start and fast recovery phases remain the same. CUBIC only changes the congestion avoidance phase, as follows:

+   * Let $W_{\max}$ be size of TCP’s congestion control window when loss was last detected, and let $K$ be the future point in time when TCP CUBIC’s window size will again reach $W_{\max}$, assuming no losses. Several tunable CUBIC parameters determine the value $K$, that is, how quickly the protocol’s congestion window size would reach $W_{\max}$.
* CUBIC increases the congestion window as a function of *cube* of the distance between the current time, $t$, and $K$. Thus, when $t$ is further away from $K$, the congestion window size increases are much larger than when $t$ is close to $K$. That is, CUBIC quickly ramps up TCP’s sending rate to get close to the pre-loss rate, $W_{\max}$, and only then probes cautiously for bandwidth as it approaches $W_{\max}$.
* When $t$ is greater than $K$, the cubic rule implies that CUBIC’s congestion window increases are small when $t$ is still close to $K$ (which is good if the congestion level of the link causing loss hasn’t changed much) but then increases rapidly as $t$ exceeds $K$ (which allows CUBIC to more quickly find a new operating point if the congestion level of the link that caused loss has changed significantly).

Under these rules, the idealized performance of TCP Reno and TCP CUBIC are compared in Figure 3.54, adapted from [Huston 2017]. We see the slow start phase

![](bbox=[0.3, 0.61, 0.82, 0.85])

**Figure 3.54**   TCP congestion avoidance sending rates: TCP Reno and TCP CUBIC