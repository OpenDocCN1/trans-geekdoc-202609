where $F_1(\cdot)$ and $F_2(\cdot)$ are the two empirical cumulative distribution functions (CDFs) of alpha $t$-ratios; one from the data and one from the model. This measure looks at the maximum vertical distance between the CDFs. The second alternative measure is the Cramer–von Mises distance,

$$D_{\mathrm{CvM}}=E_x\{[F_1(x)-F_2(x)]^2\}, \tag{108.9}$$

which looks at the mean squared distance.

To implement the alternative measures we combine the observations of the alpha $t$-ratios from the original data and from a model, rank the values and calculate the two CDFs at each of the discrete points. The results, reported in the Appendix, are similar to those using the original measures.

# ### 108.6.3 *Are the alphas correlated with active management?*

Several studies suggest that more active funds have larger alphas (e.g., Cremers and Petajisto 2009, Titman and Tiu 2011, Amihud and Goyenko 2013, Ferson and Mo 2016). In particular, funds with lower factor model regression $R$-squares are found to have larger alphas. We examine the correlations between the factor model $R$-squares and the estimated alphas and find a correlation of −0.015 in the mutual fund sample and −0.111 in the hedge fund sample. The mixtures of distributions simulated above do not accommodate this relation.

We modify the simulations to allow a relation in the cross-section between alpha and active management, measured by the $R$-squares in the factor model regressions that deliver the alphas. We sort the funds by their factor model $R$-squares, and group them into three groups with the group sizes determined by the π-fractions at any point in the simulations, and assign the good alpha first to the low $R$-square group and the bad alpha first to the high $R$-square group. Thus, this approach builds in a relation between the alpha and active management, measured by the factor model $R$-squares.

The results are summarized in Table 108E.4, Panel D. We find that this modification improves the goodness-of-fit statistic. The best-fitting alpha parameters are further out in the tails. In the left tail, the bad alpha moves about ¼ of a percent to the left. The estimates of the good alpha and the fraction of good hedge funds are similar to those in the original design. Fewer fractions of the hedge funds are estimated to have the more pessimistic bad alpha, and the fraction of zero alpha hedge funds increases to 30–44%, which is a significant positive fraction when the test size is 10%. The BSW estimates are similar to those in the original design. The results suggest that incorporating the relatively poor performance of the high $R$-square hedge