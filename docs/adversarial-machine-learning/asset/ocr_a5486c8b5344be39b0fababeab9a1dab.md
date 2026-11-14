derivative with respect to the \(\tau^\text{th}\) element, \(\mu_\tau\), yields the following condition:

\(\frac{\partial}{\partial \mu_\tau} \left[ T - \sum_{t=1}^T \frac{\mu_{t-1}}{\mu_t} \right] = 0 \Rightarrow \frac{\mu_{\tau-1}}{\mu_\tau^2} = \frac{1}{\mu_{\tau+1}}.\)

These conditions do not hold for \(\tau = 0\) or \(\tau = T\), but we already have \(\mu_0 = N\) and \(\mu_T = M + N\). Further, since \(\mu_t^* \in \Re_+\), we can instead consider the logarithm of these variables: \(\ell \mu_t \triangleq \log (\mu_t))\), for which any stationary point must satisfy the following system of equations:

\(\ell \mu_0 = \log (N)\)

\(2 \cdot \ell \mu_t = \ell \mu_{t-1} + \ell \mu_{t+1} \quad \forall t \in \{1 \dots T-1\}\)

\(\ell \mu_T = \log (M + N),\) (B.7)

The second condition is equivalently defined by the recurrence relation \(\ell \mu_t = 2\ell \mu_{t-1} - \ell \mu_{t-2}\), for \(t \ge 2\). This recurrence has a characteristic polynomial given by \(\chi(r) = r^2 - 2r + 1\). Solving \(\chi(r) = 0\) yields the single root \(r = 1\), for which there must exist \(\phi\) and \(\psi\) such that \(\ell \mu_t = \phi \cdot r^t + \psi \cdot t \cdot r^t = \phi + \psi \cdot t\). Using the boundary conditions \(\ell \mu_0 = \log (N)\) and \(\ell \mu_T = \log (M + N)\), we find that \(\phi = \log (N)\) and \(\psi = \frac{1}{T} \log \left( \frac{M+N}{N} \right)\). Thus, the *unique* solution to this linear recurrence relation is given by

\(\ell \mu_t = \log (N) + \frac{t}{T} \log \left( \frac{M+N}{N} \right).\)

Naturally, this corresponds to the sequence \(\mu_t^* = N \left( \frac{M+N}{N} \right)^{\left( \frac{t}{T} \right)}\), which satisfies \(\mu_0^* = N\) and \(\mu_T^* = N + M\) and is a non-decreasing sequence. Moreover, the logarithmic conditions given in Equation (B.7) must hold for any optimal positive sequence, but specify a system of \(T + 1\) equalities in terms of \(T + 1\) variables and thus have a unique solution. Thus, \(\mu^*\) is the unique positive sequence that maximizes the program given in Equation (4.16).

Having established optimality, the optimal distance achieved is

\(D_N^*(M, T) = T - \sum_{t=1}^T \frac{N}{N} \left( \frac{M+N}{N} \right)^{\left( \frac{t-1}{T} \right)} \left( \frac{M+N}{N} \right)^{\left( \frac{-t}{T} \right)} = T \left( 1 - \left( \frac{N}{M+N} \right)^{\frac{1}{T}} \right)\)

as was to be shown. Finally, using the definition of total mass in Equation (4.7), for \(t \ge 1\), \(\beta_t^* = \mu_t^* - \mu_{t-1}^* = N \left( \frac{M+N}{N} \right)^{\frac{t-1}{T}} \left( \left( \frac{M+N}{N} \right)^{\frac{1}{T}} - 1 \right)\). This completes the proof. \(\square\)