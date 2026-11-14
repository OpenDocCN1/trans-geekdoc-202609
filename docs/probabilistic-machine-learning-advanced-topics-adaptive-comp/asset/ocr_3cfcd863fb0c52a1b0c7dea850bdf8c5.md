How efficient is this method? If \(\tilde{p}\) is a normalized target distribution, the acceptance probability is \(1/C\). Hence we want to choose \(C\) as small as possible while still satisfying \(Cq(x) \ge \tilde{p}(x)\).

# 11.4.2 Example

For example, suppose we want to sample from a gamma distribution:3

\(\text{Ga}(x|\alpha, \lambda) = \frac{1}{\Gamma(\alpha)} x^{\alpha-1} \lambda^\alpha \exp(-\lambda x) \quad (11.25)\)

where \(\Gamma(\alpha)\) is the gamma function. One can show that if \(X_i \stackrel{iid}{\sim} \text{Expon}(\lambda)\), and \(Y = X_1 + \cdots + X_k\), then \(Y \sim \text{Ga}(k, \lambda)\). For non-integer shape parameters \(\alpha\), we cannot use this trick. However, we can use rejection sampling using a \(\text{Ga}(k, \lambda - 1)\) distribution as a proposal, where \(k = \lfloor \alpha \rfloor\). The ratio has the form

\(\frac{p(x)}{q(x)} = \frac{\text{Ga}(x|\alpha, \lambda)}{\text{Ga}(x|\lambda, \lambda - 1)} = \frac{x^{\alpha-1} \lambda^\alpha \exp(-\lambda x) / \Gamma(\alpha)}{x^{k-1} (\lambda - 1)^k \exp(-(\lambda - 1)x) / \Gamma(k)} = \frac{\Gamma(k) \lambda^\alpha}{\Gamma(\alpha) (\lambda - 1)^k} x^{\alpha - k} \exp(-x) \quad (11.26) (11.27)\)

This ratio attains its maximum when \(x = \alpha - k\). Hence

\(C = \frac{\text{Ga}(\alpha - k | \alpha, \lambda)}{\text{Ga}(\alpha - k | k, \lambda - 1)} \quad (11.28)\)

See Figure 11.4(b) for a plot.

# 11.4.3 Adaptive rejection sampling

We now describe a method that can automatically come up with a tight upper envelope \(q(x)\) to any log concave 1d density \(p(x)\). The idea is to upper bound the log density with a piecewise linear function, as illustrated in Figure 11.5(a). We choose the initial locations for the pieces based on a fixed grid over the support of the distribution. We then evaluate the gradient of the log density at these locations, and make the lines be tangent at these points.

Since the log of the envelope is piecewise linear, the envelope itself is piecewise exponential:

\(q(x) = C_i \lambda_i \exp(-\lambda_i (x - x_{i-1})), \quad x_{i-1} < x \le x_i \quad (11.29)\)

where \(x_i\) are the grid points. It is relatively straightforward to sample from this distribution. If the sample \(x\) is rejected, we create a new grid point at \(x\), and thereby refine the envelope. As the number of grid points is increased, the tightness of the envelope improves, and the rejection rate goes down. This is known as **adaptive rejection sampling** (ARS) [GW92]. Figure 11.5(b-c) gives an example of the method in action. As with standard rejection sampling, it can be applied to unnormalized distributions.

3. This section is based on notes by Ioana A. Cosma, available at http://users.aims.ac.za/~ioana/cp2.pdf.