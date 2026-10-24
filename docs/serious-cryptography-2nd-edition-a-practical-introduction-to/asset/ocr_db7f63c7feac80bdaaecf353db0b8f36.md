![](bbox=[0.267, 0.068, 0.888, 0.432])

*Figure 12-5: The geometric rule for doubling a point—that is, P + P*

The formula to determine the coordinates \((x_R, y_R)\) of \(R = P + P\) is slightly different from the formula for a distinct \(P\) and \(Q\). The basic formula is \(x_R = m^2 - x_P - x_Q\) and \(y_R = m(x_P - x_R) - y_P\), but the value of \(m\) becomes \((3x_P^2 + a)/2y_P\), where \(a\) is the curve’s parameter, as in \(y^2 = x^3 + ax + b\).

# Multiplying Points

To multiply points on elliptic curves by a given integer number \(k\), you determine the point \(kP\) by adding \(P\) to itself \(k - 1\) times. In other words, \(2P = P + P\), \(3P = P + P + P\), and so on. To obtain the x- and y-coordinates of \(kP\), repeatedly add \(P\) to itself and apply the preceding addition law.

To compute \(kP\) efficiently, however, the naive technique of adding \(P\) by applying the addition law \(k - 1\) times is far from optimal. For example, if \(k\) is large (of the order of, say, \(2^{256}\)) as it occurs in elliptic curve–based crypto schemes, then computing \(k - 1\) additions is downright infeasible.

You can gain an exponential speedup by adapting the technique in Chapter 10’s “A Fast Exponentiation Algorithm” to compute \(x^e\) mod \(n\). The difference is that you’re multiplying points by an integer rather than computing exponents. But you can adapt the method to become *double-and-add*, where multiplication becomes addition and squaring becomes doubling.

For example, to compute \(8P\) in three additions instead of seven using the naive method, first compute \(P_2 = P + P\), then \(P_4 = P_2 + P_2\), and finally \(P_4 + P_4 = 8P\). This is the simplest case, when the multiplier is a power of two,