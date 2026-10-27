So, 40% of the first 10 integers are prime, but only 16.8% of the first 1,000 are prime. π(n) may be calculated for any value of n by simply testing the primality of each positive integer less than or equal to n. However, if n is large, this is a very time-consuming method. It would be nice if there were some equation for π(n) that is easier to evaluate such as p(n) = ⌊1.591 + 0.242n − 0.0000752n²⌋. Recall that ⌊n⌋ denotes the greatest integer less than or equal to n. By plugging in values, we see that p(n) works great for 10, 100, and 1,000, but it becomes inaccurate for higher values of n, as can be seen by expanding the table above. Also, it doesn’t do well for most values under 1,000, other than the ones in the table!⁴

| *n* | π(*n*) |
|---:|---:|
| 10 | 4 |
| 100 | 25 |
| 1,000 | 168 |
| 10,000 | 1,229 |
| 100,000 | 9,592 |
| 1,000,000 | 78,498 |
| 10,000,000 | 664,579 |
| 100,000,000 | 5,761,455 |
| 1,000,000,000 | 50,847,534 |
| 10,000,000,000 | 455,052,511 |

German mathematician Carl Friedrich Gauss (1777–1855) came up with the *prime number theorem*, but was unable to prove it. It says:

$$\pi(n) \sim \frac{n}{\ln(n)}$$

We saw the ~ notation previously in *Section 1.6*, where Stirling’s formula was presented. Recall that it is pronounced “asymptotically approaches” and means that the ratio of the two quantities, π(n) and \(\frac{n}{\ln(n)}\), in this case, approaches 1 as n approaches infinity.

Gauss came up with another estimate, the logarithmic integral of n, which is written *li(n)*. It also asymptotically approaches π(n) as n → ∞, and it gives more accurate estimates when n is small.

$$li(n) = \int_{2}^{n} \frac{1}{\ln(x)}\,dx$$

That these functions converge to π(n) was proven in 1896, independently, by Jacques Hadamard and C. J. de la Vallée-Poussin. Their proofs used the Riemann Zeta function.

⁴ The function *p(n)* was obtained by using Lagrangian interpolation on the values for which it was seen to work perfectly.