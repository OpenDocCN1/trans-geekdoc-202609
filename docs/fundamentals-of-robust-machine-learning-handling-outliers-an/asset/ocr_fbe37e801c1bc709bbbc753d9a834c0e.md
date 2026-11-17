**Exercise:** Compute the correction terms for momentum and rmsprop for the previous two problems.

**Ans.:** The corrected terms are

\( m_{dw}^{corr} = \frac{0.5}{1 - 0.9} = 5 \)

and

\( r_{dw}^{corr} = \frac{0.025}{1 - 0.999} = 25 \).

**Exercise:** Given that \( dw^{(0)} = 5 \), compute \( w^{(1)} \) using the corrected values of \( m_{dw} \) and \( r_{dw} \) of the previous two exercises.

**Ans.:** Using the corrected terms above, we obtain for momentum,

\( w^{(1)} = 0.1 - 0.05 \times 5 = -0.15 \)

and for rmsprop,

\( w^{(1)} = 0.1 - 0.05 \times 5 / \sqrt{25} = 0.05 \).

They are different even in the warm-up phase.

# 10.4.4 Adam Optimizer

Each of the three methods above was presented as separate approaches. However, the Adam (ADAptive Minimizer) optimizer combines all of them into one tool. It applies rmsprop to the momentum update equation along with the warm-up correction to produce a very powerful method that has proven to be extremely efficient at finding a regional minimum in deep neural networks. The combination of the methods produces the following update equation:

\( w^{(t+1)} = w^{(t)} - \ell \times \frac{m_{dw}^{corr}}{\sqrt{r_{dw}^{corr}} + \varepsilon} \). (10.4.9)

**Exercise:** Given that \( (\partial J(w) / \partial w)^{(0)} = 5 \), \( r_{dw}^{(0)} = 0 \), and \( w^{(0)} = 0.1 \), compute the value of \( w^{(1)} \) using Eq. (10.4.9) with \( \alpha_1 = 0.9 \), \( \alpha_2 = 0.999 \), \( \epsilon = 0 \), and \( \ell = 0.05 \).

**Ans.:** Using the results from prior exercises, we find that

\( m_{dw}^{corr} = 5 \) and \( r_{dw}^{corr} = 25 \).

Therefore, \( w^{(1)} = 0.1 - \frac{0.05}{\sqrt{25}} \times 5 = 0.05 \).

As shown in Algorithm 10.1, the Adam optimizer begins by initializing \( \alpha_1 \), \( \alpha_2 \), and \( w^{(0)} \) to the appropriate values. In addition, the starting values for \( m_{dw} \) and \( r_{dw} \) are set and the learning rate is specified. The algorithm then enters the convergence loop where the momentum, rmsprop, and warm-up terms are