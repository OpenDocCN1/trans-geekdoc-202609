For the one-factor design, $\eta^2$ is the same as $R^2$, the squared correlation between the observed scores $(\hat{Y}_j)$ and their predicted values $(ar{Y}_j)$. The adjusted-$R^2 = \frac{SS_A-(a-1)MS_{S/A}}{SS_{total}}$ corrects for the positive bias of $\eta^2$.

The data may be found in the Table 8_5_Male_educ.xlsx; go to the Tables page of the book's website.

Kelmanman et al. (2004) Wilcox, Peterson, and McNitt-Gray (2018) argued for further refinement of the trimmed t test and associated confidence intervals using bootstrapping methods that go beyond the scope of this book. See Field and Wilcox (2017) for detailed R-based examples of approach for a variety of experimental designs.

$H$ is distributed as a $\chi^2$ with degrees of freedom equal to $a-1$. In R, the $\chi^2$ distributional calculator abbreviation for $\chi^2$ is `chisq`, and so, by analogy to the examples in Box 6.1, we calculate $1-pchisq(6.4687, df=2)$ to confirm that $p=.039$.

Be careful not to use the $bl.test$ function in the [onewaytests] package for this purpose. That function tests for the equality of means, not variances.