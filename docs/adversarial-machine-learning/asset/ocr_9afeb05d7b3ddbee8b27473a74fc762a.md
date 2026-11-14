for \( p = \infty \). Based on this upper bound on the \( MAC \) of \( g \) and the \( MAC \) of \( f \) (i.e., \( C_0^- \)), if there is a common \( \epsilon \)-\( IMAC \) between these classifiers, it must satisfy

\( (1 + \epsilon) \ge \begin{cases} \left( \frac{D-K}{D} \right)^{\frac{p-1}{p}}, & \text{if } 1 < p < \infty \\ \frac{D}{D-K}, & \text{if } p = \infty \end{cases} . \)

Solving for the value of \( K \) required to achieve a desired accuracy of \( 1 + \epsilon \) yields

\( K \le \begin{cases} \frac{(1+\epsilon)^{\frac{p}{p-1}} - 1}{(1+\epsilon)^{\frac{p}{p-1}}} D, & \text{if } 1 < p < \infty \\ \frac{\epsilon}{1+\epsilon} D, & \text{if } p = \infty \end{cases} , \)

which bounds the size of the \( K \)-covering of \( \mathbb{X} \) required to achieve the desired multiplicative accuracy \( \epsilon \).

For the case \( 1 < p < \infty \), Lemma A.2 shows there must be

\( M \ge \exp \left\{ \ln(2) \cdot D \left( 1 - H \left( 1 - (1 + \epsilon)^{\frac{p}{1-p}} \right) \right) \right\} \)

vertexes of the hypercube in the \( K \)-covering of \( \mathbb{X} \) to achieve any desired accuracy \( 0 < \epsilon < 2^{\frac{p-1}{p}} - 1 \), for which

\( \delta = \frac{(1 + \epsilon)^{\frac{p}{p-1}} - 1}{(1 + \epsilon)^{\frac{p}{p-1}}} < \frac{1}{2} \)

to satisfy the condition required by the lemma. Thus, this theorem is applicable for any \( \epsilon < 2^{\frac{p-1}{p}} - 1 \). For example, for \( p = 2 \), the theorem is applicable for any \( \epsilon < \sqrt{2} - 1 \). Moreover, since \( H(\delta) < 1 \) for any \( \delta < \frac{1}{2} \),

\( \alpha_{p, \epsilon} = \exp \left\{ \ln(2) \left( 1 - H \left( \frac{(1 + \epsilon)^{\frac{p}{p-1}} - 1}{(1 + \epsilon)^{\frac{p}{p-1}}} \right) \right) \right\} > 1 \)

and

\( M \ge \alpha_{p, \epsilon}^D . \)

Similarly for \( p = \infty \), applying Lemma A.2 requires \( M \ge 2^{D(1-H(\frac{\epsilon}{1+\epsilon}))} \) to achieve any desired accuracy \( 0 < \epsilon < 1 \) (for which \( \epsilon / (1 + \epsilon) < 1/2 \) as required by the lemma). Again, by the properties of entropy, the constant \( \alpha_{\infty, \epsilon} = 2^{(1-H(\frac{\epsilon}{1+\epsilon}))} > 1 \) for any \( 0 < \epsilon < 1 \) and \( M \ge \alpha_{\infty, \epsilon}^D \).

It is worth noting that the constants \( \alpha_{p, \epsilon} \) and \( \alpha_{\infty, \epsilon} \) required by Theorem 8.12 can be expressed in a more concise form by expanding the entropy function (\( H(\delta) = -\delta \log_2(\delta) - (1 - \delta) \log_2(1 - \delta) \)). For \( 1 < p < \infty \) the constant is given by

\( \alpha_{p, \epsilon} = 2 \cdot \left( 1 - (1 + \epsilon)^{\frac{p}{1-p}} \right) \cdot \exp \left( \ln \left( \frac{1}{1 - (1 + \epsilon)^{\frac{p}{1-p}}} \right) \cdot (1 + \epsilon)^{\frac{p}{1-p}} \right) . \quad (\text{D.7}) \)

In this form, it is difficult to directly see that \( \alpha_{p, \epsilon} > 1 \) for \( \epsilon < 2^{\frac{p-1}{p}} - 1 \), but using the entropy form in the proof above shows that this is indeed the case. Similarly, for \( p = \infty \)