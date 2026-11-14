![](bbox=[0.38, 0.11, 0.62, 0.3])

Figure 5.7: Illustration of multivariate mutual information between three random variables. From https://en.wikipedia.org/wiki/Mutual_information. Used with kind permission of Wikipedia author PAR.

For 3 variables, the MMI is given by

\(\mathbb{I}(X; Y; Z) = \mathbb{I}(X; Y) - \mathbb{I}(X; Y|Z)\) (5.124)
\(= \mathbb{I}(X; Z) - \mathbb{I}(X; Z|Y)\) (5.125)
\(= \mathbb{I}(Y; Z) - \mathbb{I}(Y; Z|X)\) (5.126)

This can be interpreted as the change in mutual information between two pairs of variables when conditioning on the third. Note that this quantity is symmetric in its arguments.

By the definition of conditional mutual information, we have

\(\mathbb{I}(X; Z|Y) = \mathbb{I}(Z; X, Y) - \mathbb{I}(Y; Z)\) (5.127)

Hence we can rewrite Equation (5.125) as follows:

\(\mathbb{I}(X; Y; Z) = \mathbb{I}(X; Z) + \mathbb{I}(Y; Z) - \mathbb{I}(X, Y; Z)\) (5.128)

This tells us that the MMI is the difference between how much we learn about Z given X and Y individually vs jointly (see also Section 5.3.5.3).

The 3-way MMI is illustrated in the information diagram in Figure 5.7. The way to interpret such diagrams when we have multiple variables is as follows: the area of a shaded area that includes circles A, B, C, ... and excludes circles F, G, H, ... represents \(\mathbb{I}(A; B; C; \dots | F, G, H, \dots)\); if \(B = C = \emptyset\), this is just \(\mathbb{I}(A|F, G, H, \dots)\); if \(F = G = H = \emptyset\), this is just \(\mathbb{I}(A; B; C, \dots)\).

# 5.3.5.3 Synergy and redundancy

The MMI is \(\mathbb{I}(X; Y; Z) = \mathbb{I}(X; Z) + \mathbb{I}(Y; Z) - \mathbb{I}(X, Y; Z)\). We see that this can be positive, zero, or negative. If some of the information about Z that is provided by X is also provided by Y, then there is some **redundancy** between X and Y (wrt Z). In this case, \(\mathbb{I}(X; Z) + \mathbb{I}(Y; Z) > \mathbb{I}(X; Y; Z)\), so (from Equation (5.128)) we see that the MMI will be positive. If, by contrast, we learn more about Z when we see X and Y together, we say there is some **synergy** between them. In this case, \(\mathbb{I}(X; Z) + \mathbb{I}(Y; Z) < \mathbb{I}(X; Y; Z)\), so the MMI will be negative.