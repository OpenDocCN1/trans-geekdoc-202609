acceptance probability of \( q_2 \) should be carefully designed and computed. One feasible way is to utilize detailed balance property at each stage separately and obtain the acceptance rate that can preserve stationary status [15], i.e., Eq. (9.20).

```
\(\begin{aligned} A_2 &= \min \left( 1, \frac{\pi(q_2)\mathbb{Q}(q_2|q_1)\mathbb{Q}(q_2,q_1|q^*)[1 - A_1(q_2, q_1)]}{\pi(q^*)\mathbb{Q}(q^*|q_1)\mathbb{Q}(q^*|q_1, q_2)[1 - A_1(q^*, q_1)]} \right) \\ &= \min \left( 1, \frac{\lambda_2}{\phi_2} \right) \end{aligned}\)
(9.20)
```

Here \(\pi(q_2)\mathbb{Q}(q_2|q_1)\mathbb{Q}(q_2,q_1|q^*)[1 - A_1(q_2,q_1)]\) is denoted as \(\lambda_2 \cdot \pi(q^*)\mathbb{Q}(q^*|q_1)\mathbb{Q}(q^*|q_1, q_2)[1 - A_1(q^*, q_1)]\) which is denoted as \(\epsilon_2\) for the convenience of illustration. Since the procedure comes to \( t=2 \) stage, which means at \( t=1 \) stage we have \(\lambda_1 < \epsilon_1\).

Therefore, in Eq. (9.20), \( A_1 \) can be replaced with \(\frac{\lambda_1}{\phi_1}\) in denominator, which is Eq. (9.21).

```
\(\begin{aligned} A_2 &= \min \left( 1, \frac{\lambda_{t+1}}{\mathbb{Q}(q^*|q_1, q_2)[\pi(q^*)\mathbb{Q}(q^*|q_1) - \pi(q_1)\mathbb{Q}(q_1|q^*)]} \right) \\ &= \min \left( 1, \frac{\lambda_2}{\mathbb{Q}(q^*|q_1, q_2)[\epsilon_1 - \lambda_1]} \right) \end{aligned}\)
(9.21)
```

```
\(\begin{aligned} A_t &= \min \left( 1, \frac{\pi(q_t)\mathbb{Q}[1 - A_1(q_t, q_{t-1})]\cdots[1 - A_{t-1}(q_t, ..., q_1)]}{\pi(q^*)\mathbb{Q}(q^*|q_i)...\mathbb{Q}(q^*|q_1,..., q_t)} \right) \\ &= \min \left( 1, \frac{\lambda_t}{\phi_t} \right) \end{aligned}\)
(9.22)
```

Iteratively, we can derive a general delayed rejection procedure as the following. At the \( t \)-th stage, if the sample of the previous stage is rejected, the acceptance rate can be written as Eq. (9.22), where \(\tilde{\mathbb{Q}} = \mathbb{Q}(q_t | q_{t-1}) ... \mathbb{Q}(q_t, q_{t-1}, ..., q^*)\). Similarly, at the \( t \)-th stage, we have \(\lambda_m < \epsilon_m\) for \(\forall m = 1, ..., t-1\) so that \( A_m \) can always be written in the form of \(\frac{\lambda_m}{\phi_m}\), for \(\forall m = 1, ..., t-1\). Intuitively, the recursive equation

```
\(\epsilon_t = \mathbb{Q}(q^* | q_1, ..., q_t)(\epsilon_{t-1} - \lambda_{t-1})\)
(9.23)
```