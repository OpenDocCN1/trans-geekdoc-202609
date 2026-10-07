
# Decision Making with Case-Based Learning

| Service | Technology | Location | Time | Throughput | Latency | Power | Dropped Calls | Blocked Calls |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | | | | | | | |

**Figure 6.11** Case representation of the cognitive radio case-based decision maker for service selection.

[text] Case representation of the cognitive radio case-based decision maker for service selection.

taught or learned from experience over time. Experience can show that a given service is highly time- and location-dependent. Peak traffic times and poor signal quality can lead to more dropped calls, more blocked calls, and increased latency in the network.

The similarity is determined by the environment. The environment consists of time of day, day of the week, location, and available service providers. This is another multidimensional problem, the problem is to figure out how to combine the information to produce an understanding of the similarity. Service at the same time of day on a weekday in any city might have similar problems due to heavy network use. At other times, usage patterns can be specific to certain locations, such as the difference between urban and rural roads.

In our academic exercise here, have to recognize that this kind of similarity analysis is very difficult without surveying and modeling the influences of location and time. To simplify the scenario, we will break the concepts down to simple measurements of location in the form of longitude and latitude and time in the form of the time of day and day of the week. Further investigation could help tie in concepts like location diversity, as the difference between rural, suburban, and urban areas. The similarity function of (6.10) compares the time and location by calculating an error between the current location, $d(p)$, and the location of the case, $q$, in the case base, $d(q)$. The time of day is calculated similarly as an error between the current time, $t(p)$, and time in $t(q)$. The day of the week is handled differently in that the similarity is 1 if the day of the week, $D(p)$, is the same as the day of the week in the case base, $D(q)$. Otherwise, it is 0. A more complicated model could have a partial similarity that equates to 0.5 if $D$ and $D(q)$ are both weekdays or both weekends.

```
$s(p,q) = 1 - \frac{\frac{|d(p)-d(q)|}{d(q)}+\frac{|t(p)-t(q)|}{t(q)}}{1 - D_{\Delta}}$
$D_{\Delta} = \begin{cases} 1 & D(p)=D(q) \\ 0 & D(p) \neq D(q) \end{cases} \quad (6.10)$
```

The utility is based on the observables of the network service and is maximized by higher throughput, lower BER, latency, dropped calls, and blocked calls. This is related to the multiobjective problem where these different values cannot be directly compared or combined by differences in scale and importance to the situation. On the other hand, this problem is constrained to known services, unlike the general cognitive radio system, we have a known set of parameters and values. While knowledge is being built up by the case base, the system selects services based on the required QoS, that has already primed the decision making with desired values. We will ignore the BER and the throughput as an indirect measure of value. We can use this fact to build the utility measure of future systems. For each service $q$ in the case base, the cognitive radio measures the performance, as average throughput comparable to the advertised service of the case, $R(q)$ and latency, $L(q)$ during the connection. These values are directly comparable to the advertised service of the case, $R_s(q)$ and $L_s(q)$ for the throughput and latency, respectively. The radio would also keep track of the number of dropped calls, $C_d(q)$, and blocked calls, $C_b(q)$, to calculate a percentage of each value over the total number of connections made or attempted, $C$. The utility function in it can be built from the knowledge and assumptions. This function sums the error between the actual service and the proposed service as well as the percentage of dropped and blocked calls. The closer to 1, the better the utility of the service.

```
$u(q) = 1 - \frac{1}{4}\left(\frac{|\hat{R}-R_s(q)|}{R_s(q)}+\frac{|\hat{L}-L_s(q)|}{L_s(q)}+\frac{C_B}{C(q)}+\frac{C_D}{C(q)}\right) \quad (6.11)$
```

An aspect of the case-based approach that should become obvious as we discussed this example is the ability to use knowledge developed from other users to augment our own. Our example has discussed the use of past information at different times and different locations. To individually build up enough information to make good, informed decisions could take a long time. If, however, other users who have also been developing similar information can share this, then the aggregate information built among all radios is more useful. There is of course security issues with this, such as poisoning the case base.

## 6.6 Conclusion

In this chapter, we introduced the concept of using feedback in the optimization process to aid future optimizations. We used the concept of case-based decision theory as the mechanism for producing the feedback. When one problem is optimized, the solution is fed back into a case base that stores the solution, results, and problem. When a new problem is received, the decision maker looks for similar problems in the case base that exhibit a high utility. The previous solutions stored in the case base are then fed to the optimization process. We examined how this technique is applied to the cognitive engine to build up and learn from experience.

To demonstrate this we employed the case-based learning system to the simple knapsack problem. The results showed an overall performance benefit from the implementation. They also showed that there are still significant gains to be made by further studying this technique as well as a number of parameters that can be adjusted. The case size, as well as the number of cases used to seed the optimization algorithm, can be changed for different results. More importantly, the results in this chapter showed that the definition of the utility function can have a great impact on the performance. We suggest that the similarity function would also produce a large performance difference. With the knapsack problem, we only present one similarity function that makes sense for this thing, but for more complicated problems, different similarity rankings may be possible and must be studied.

There are advances from this concept beyond these algorithm adjustments. As we discussed at the end of this chapter, this method introduces other aspects of learning, such as using performance trends to build up confidence or alter behavior. This concept offers a number of significant advantages to online optimization processes, especially when strict time limits must be imposed. Because of this, case-based learning provides significant potential for use with the cognitive engine where problems require solutions quickly as situations and environments.

We will show the results of using case-based learning in the cognitive engine in Chapter 8. First, however, we discuss a bit more theory and design

## References

- [1] T. W. Rondeau, B. Le, D. Maldonado, D. Scaperoth, A. B. Mackenzie, and C. W. Bostian, “Optimization, Learning, and Decision Making in a Cognitive Engine,” Software Defined Radio Forum, 2006.
- [2] D. E. Goldberg, Genetic Algorithms in Search, Optimization, and Machine Learning, Reading, MA: Addison-Wesley, 1989.
- [3] C. L. Ramsey and J. J. Grefenstette, “Case-Based Initialization of Genetic Algorithms,” Proc. Fifth Int. Conf. Genetic Algorithms, 1993, pp. 84–91.
- [4] T. R. Newman, R. Rajbanshi, A. M. Wyglinski, J. B. Evans, and G. J. Minden, “Population Adaptation for Genetic Algorithm-Based Cognitive Radios,” IEEE Proc. Cognitive Radio Oriented Wireless Networks and Communications, Aug. 2007.
- [5] J. Gilboa and D. Schneider, A Theory of Case-Based Decisions, Cambridge: Cambridge University Press, 2001.
- [6] J. Kolodner, Case-Based Reasoning, San Mateo, CA: Morgan Kaufmann Pub., 1993.
- [7] C. J. Rieser, “Biologically Inspired Cognitive Radio Engine Model Utilizing Distributed Genetic Algorithms for Secure and Robust Wireless Communications and Networking,” Ph. diss., Virginia Tech, 2004.
- [8] S. Ball, A. Ferguson, and T. W. Rondeau, “Consumer Applications of Cognitive Radio Defined Networks,” IEEE Sym. New Frontiers in Dynamic Spectrum Access Networks (DySPAN), 2005, pp. 518–525.
- [9] L. Doyle and T. Forde, “Towards a Fluid Spectrum Market for Exclusive Usage Rights,” IEEE Sym. New Frontiers in Dynamic Spectrum Access Networks (DySPAN), 2007, pp. 620–633.
