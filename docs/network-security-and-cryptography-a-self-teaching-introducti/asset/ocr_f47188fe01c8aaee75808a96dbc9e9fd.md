# MATHEMATICAL FOUNDATIONS FOR COMPUTER NETWORKS • 65

We say that $\{X_k\}$, $k=0, 1, 2, \dots, n$ is an independent process if and

$F_X(x_0, x_1, \dots, x_n; t_1, \dots, t_n) = F_{X_0}(x_0; t_0)F_{X_1}(x_1; t_1) \dots F_{X_n}(x_n; t_n)$

In addition, if random variables are drawn from the same distribution, the process is characterized by a single CDF, $F_X(x; t_k)$, $k=0, 1, 2, \dots, n$. In this case, we call $\{X_k\}$ a sequence of independent and identically distributed (IID) random variables.

Having defined the CDF and PDF for a random process $X(t)$, we are now prepared to define the statistical (or ensemble) averages—the mean, variance, autocorrelation, and autocovariance of $X(t)$. In general, the random variables, these statistics play an important role in practical applications.

The mean or expected value of the random process $X(t)$ is

$m_X(t) = E[X(t)] = \int_{-\infty}^{\infty} x f_X(x;t)dx \quad (2.88)

where $E[.]$ denotes ensemble average, $f_X(x;t)$ is the PDF of $X(t)$, and $X(t)$ is regarded as a random variable for a fixed value of $t$. In general, $m_X(t)$ is a function of time.

The variance of a random process $X(t)$ is given by

$Var(X) = \sigma_X^2 = E[(X(t)-m_X(t))^2] = E[X^2]-m_X^2 \quad (2.89)

The autocorrelation of a random process $X(t)$ is the joint moment of $X(t_1)$ and $X(t_2)$, that is,

$R_X(t_1,t_2) = E[X(t_1)X(t_2)] = \int_{-\infty}^{\infty}\int_{-\infty}^{\infty} x_1x_2 f_X(x_1,x_2;t_1,t_2)dx_1dx_2 \quad (2.90)

where $f_X(x_1,x_2;t_1,t_2)$ is the second-order PDF of $X(t)$. In general, $R_X(t_1,t_2)$ is a deterministic function of two variables $t_1$ and $t_2$. The autocorrelation function is important because it describes the power-spectral density of a random process.

The covariance or autocovariance of a random process $X(t)$ is the covariance of $X(t_1)$ and $X(t_2)$, that is,