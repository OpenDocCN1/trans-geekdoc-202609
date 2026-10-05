# MATHEMATICAL FOUNDATIONS FOR COMPUTER NETWORKS • 69

+   4. $\sigma_X^2 = \overline{X^2}-[X]^2$ is the average normalized power in the ac or time-varying component of the signal.

+   5. $X_{	ext{rms}} = \sqrt{\sigma_X^2 + [X]^2}$ is the rms value of $x(t)$.

# 2.12 MULTIPLE RANDOM PROCESSES

The joint behavior of two or more random processes is dictated by their joint distributions. For example, two processes $X(t)$ and $Y(t)$ are said to be independent if for all $t_1$ and $t_2$, the random variables $X(t_1)$ and $Y(t_2)$ are independent. That means that their $n$th order joint PDF factors, i.e.

$F_{XY}(x_1, y_1, x_2, y_2, \dots, x_n, y_n; t_1, t_2, \dots, t_n) = F_X(x_1, x_2, \dots, x_n; t_1, t_2, \dots, t_n).$

$F_Y(y_1, y_2, \dots, y_n; t_1, t_2, \dots, t_n) \quad (2.105)

The crosscorrelation between two random processes $X(t)$ and $Y(t)$ is defined as

$R_{XY}(t_1, t_2) = E[X(t_1)Y(t_2)] \quad (2.106)

Note that

$R_{XY}(t_1, t_2) = R_{YX}(t_2, t_1) \quad (2.107)

The processes $X(t)$ and $Y(t)$ are said to be orthogonal if

$R_{XY}(t_1, t_2) = 0 \quad \text{for all } t_1 \text{ and } t_2 \quad (2.108)

If $X(t)$ and $Y(t)$ are jointly stationary, then their crosscorrelation function becomes

$R_{XY}(t_1, t_2) = R_{XY}(\tau)$

$\tau = t_2 - t_1$. Other properties of thecorrelation of jointly stationary processes are:

+   1. $R_{XY}(-	au) = R_{XY}(\tau)$, that is, it is symmetric.

+   2. $|R_{XY}(	au)| \le \sqrt{R_X(0)R_Y(0)}$, that is, it is bounded.