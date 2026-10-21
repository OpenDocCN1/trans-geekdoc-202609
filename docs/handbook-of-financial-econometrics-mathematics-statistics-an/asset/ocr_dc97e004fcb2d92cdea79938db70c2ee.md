Equation (81.8b) implies that the portfolio can be viewed as an investment in n basic securities and a weighted adjusted return in the market, or

$$\sum_{i=1}^{n} (x_i b_i) E(R_{It})$$

The return on the market can be decomposed as a combination of the expected return plus some random effect. When this random effect is positive, the atmosphere is bullish and when it is negative, the atmosphere is bearish. Notationally,

$$\begin{aligned}
R_{It} &= E(R_{It}) + e_{n+1,t}\\
&= a_{n+1} + e_{n+1,t}.
\end{aligned}\tag{81.11}$$

This bit of algebraic maneuvering enables the weighted adjusted investment in the market to be viewed as an investment in an artificial security, the (n+1)th of an n-security portfolio. The weight for this (n+1)th security is the sum of the n weights multiplied by their respective related coefficients to the market index. Thus,

$$x_{n+1} = \sum_{i=1}^{n} x_i b_i.\tag{81.12}$$

The reason for this divergence in notation resulting in the definition of the (n+1)th security's return and weight is that equation (81.8) can be simplified to yield a working model for portfolio analysis. Substituting the last results for X_{n+1} and R_{It} into equation (81.8B) yields

$$\begin{aligned}
R_{pt} &= \sum_{i=1}^{n} x_i (a_i + e_{it}) + x_{n+1} (a_{n+1} + e_{n+1,t})\\
&= \sum_{i=1}^{n+1} x_i (a_i + e_{it}).
\end{aligned}\tag{81.13}$$

Because the expected value of the random-effect terms is zero, the summation that results after the application of the expectations operator can be expressed as

$$\begin{aligned}
E(R_{pt}) &= \sum_{i=1}^{n} x_i a_i + x_{n+1} E(R_{It})\\
&= \sum_{i=1}^{n+1} x_i a_i.
\end{aligned}\tag{81.14}$$