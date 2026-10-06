# 9 The Bayesian approach and Gaussian processes

$ln p(\mathbf{y})$

![](bbox=[0.268, 0.105, 0.715, 0.283])

$ln p(\mathbf{y}) = -8.06$

$ln p(\mathbf{y}) = -8.13$

![](bbox=[0.136, 0.327, 0.853, 0.455])

**Figure 9.13:** The landscape of $p(y)$ may have several local maxima. In this case there is one local maximum at the blue dot, with relatively large noise variance and length scale. There is another local maximum, which is also the global one, at the green dot, with much less noise variance and a shorter timescale. There is also a third local maximum in between (not shown). It is not uncommon that the different maxima provide different “interpretations” of the data. As a machine learning engineer it is important to be aware that this can happen; the green one does indeed optimize the marginal likelihood, but the blue one can also be practically useful.

We conclude this part about the Gaussian process by applying it to the car stopping distance problem in Example 9.3.

Draft (April 30, 2021) – A First Course for Engineers and Scientists. http://smlbook.org
© Andreas Lindholm, Niklas Wahlström, Fredrik Lindqvist, and Thomas B. Schön. 2021.