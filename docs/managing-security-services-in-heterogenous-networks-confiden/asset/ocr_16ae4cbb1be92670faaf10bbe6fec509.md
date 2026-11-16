neighbors’ trust values based on control and data packets it exchanged with them.

In [16], the direct trust is evaluated using Equation (1).

\(T = R_p \times W(R_p) + R_q \times W(R_q) + R_e \times W(R_e) + D \times W(D)\)

(1)

Here D, \(R_q\), \(R_p\), and \(R_e\) are misbehavior factors of data packets, route request, route reply, and route error packets, respectively, and are defined in Equation (2) as normalized values [0, 1].

\(R_q = \frac{R_{qs} - R_{qf}}{R_{qs} + R_{qf}} \quad R_{es} = \frac{R_{es} - R_{ef}}{R_{es} + R_{ef}} \quad R_p = \frac{R_{ps} - R_{pf}}{R_{ps} + R_{pf}} \quad D = \frac{D_s - D_f}{D_s + D_f}\)

(2)

Here \(R_{qs}\), \(R_{es}\), \(R_{ps}\), and \(D_s\) are defined as the number of route requests, route error, route reply, and data packets that are successfully forwarded by node B. \(R_{qf}\), \(R_{ef}\), \(R_{pf}\), and \(D_f\) are the number of route requests, route error, route reply, and data packets that are not forwarded (failed) by node B. Here W(). represents the weights that are given to different packets in the trust calculation.

# 3.2.6.2 Recommendation-Based Trust

Here \(c_{ij}\). indicates the confidence level of node i of node j, and this value lies in the range of [-1,1]. The confidence parameter is not symmetric. Hence, the confidence level in between node i and j is calculated as an average value of their confidence values on each other using Equation (3).

\(\hat{c}_{ij} = \frac{c_{ij} + c_{ji}}{2}\)

(3)

\(T_i(k)\) is the trust value of node i at k instant of time. \(T_i(k + 1)\) is calculated as in Equation (4)

\(T_i(k + 1) = \left\{ \begin{cases} 1, & m_i(k) > \tau \\ -1, & m_i(k) < \tau \end{cases} \right.\)

(4)

Here \(m_i(k)\). is the trust value of node i based on the recommendations of other nodes. \(\tau\) is the trust threshold value as in Equation (5).