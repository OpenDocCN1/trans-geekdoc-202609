# # 9
# Autoregressive Models

# ## 9.1 Introduction

An important model in the analysis of time-series data is the auto-regression (AR) model. In such a model, the output response is constructed as a linear function of up to \(p\) previous values of itself. The previous values are based on measurements made in uniform increments of time, for example, each day, month or year. Since the measurements are evenly spaced, the time series can be represented as occurring at different integer values of time. We use the notation AR(\(p\)) to refer to models that use \(p\) previous values in time to predict the next (i.e. most recent) value. Specifically, for a model of order \(p\), we consider the random process \(X_t, t = ..., -1, 0, 1, ...\) satisfying the relation

\(X_t = \rho_1 X_{t-1} + ... + \rho_p X_{t-p} + \varepsilon_t, \quad 1 \le t \le n, p \ge 1\) (9.1.1)

where \(\rho = (\rho_1, ..., \rho_p)^\top \in \mathbb{R}^p\) is a vector of unknown auto-regressive parameters and we assume that all roots of

\(x^p - \rho_1 x^{p-1} - ... - \rho_p = 0\) (9.1.2)

are in \((-1, 1)\). The process \(\{X_t\}\) satisfying Eqs. (9.1.1) and (9.1.2) is called the auto-regression process of dimension \(p (> 1)\).

Let \(\mathbf{Y}_o = (X_0, X_{-1}, ..., X_{1-p})^\top\) be an observable random vector independent of white noise given by \(\varepsilon_1, \varepsilon_2, ..., \varepsilon_n\). Now, let \(\rho = (\rho_1^\top, \rho_2^\top)^\top\), where \(\rho_1\) and \(\rho_2\) are \(p_1\) and \(p_2\) vectors. Then, Eq. (9.1.1) may be written as

\(X_t = \rho_1^\top \mathbf{Y}_{t1} + \rho_2^\top \mathbf{Y}_{t2} + \varepsilon_t, \quad 1 \le t \le n\) (9.1.3)

where \(\mathbf{Y}_{t1} = (X_{t-1}, ..., X_{t-p_1})^\top\), and \(\mathbf{Y}_{t2} = (X_{t-p_1-1}, ..., X_{t-p})^\top, 1 \le t \le n\).

We may refer to Eq. (9.1.3) as a sparse auto-regression model where \(\rho_2\) may contain elements which are small or negligible. If \(\rho_2 = \mathbf{0}\) exactly, then we define a restricted auto-regressive model of order \(p_1\), namely,