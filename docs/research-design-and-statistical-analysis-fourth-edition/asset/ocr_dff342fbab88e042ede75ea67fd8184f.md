Substituting the estimates of these parameters from Table 9.1, we have the basis for the
ANOVA:

```
$$(Y_{ijk} - \tilde{Y}_{ij}) = (\tilde{Y}_j - \tilde{Y}_{...) + (\tilde{Y}_k - \tilde{Y}_{...) + (\tilde{Y}_{jk} - \tilde{Y}_j - \tilde{Y}_k + \tilde{Y}_{...}) + (Y_{ijk} - \tilde{Y}_{ijk}) \quad (9.8)$
```

In other words, an individual score may differ from the mean for four distinct
reasons: (1) the effect of the level A to which they are exposed; (2) the effect of
t level B to which they are exposed; (3) the effect of the combination of the
levels of factors A and Bj; and (4) measurement error and other random noise. Put more
simply,

```
score – grand mean = main effect of A+ main effect of B+ interaction effect
+ residual error
```

# 9.3.2 Sums of Squares

Equation 9.8 forms the basis for the sums of squares; these are important components in
tests of null hypotheses. Squaring both sides of Equation 9.8 and summing yields the sums
of squares (SS) formulas in panel a of Table 9.5. As a first step, we partition the total
sum of squares into two components: between-cells sum of squares and a within-cell (S/
ab of squares). The between-cell variability is itself of interest as it has
several sources. For example, in the Wiley-Voss data set, the eight cells may
differ differ because they represent different formats, different instructions, or different
combinations of formats. Although software packages do not include the
between-participants variability, $SS_{cell}$ we include because it is involved in our concep-
tual and calculation of the $SS_{AB}$ and the $SS_{cellAB}$. The components of between-cell
sum of squares in Table 9.5 correspond to the main and interaction sources of variance that
we wish to.

The formulas presented in Table 9.5 define the sums of squares. Although statistical
software usually will be available to perform the calculations, the formulas are presented
to remind us that the sums of squares are indices of variability. For example, the $SS_{total}$ is
abn – 1 times the variance of all the scores, the $SS_S$ is $bn(a-1)$ times the variance of the A
marg, and the $SS_{cell}$ is $n(ab-1)$ times the variance of the $ab$ cell means. The tests
of null hypotheses corresponding to the A, B, and AB sources of variance (SV) test whether
those variances are greater than.

# 9.3.3 Degrees of Freedom

A formula for degrees of freedom is associated with each sources of variance. The
df_{total}$ are $ab-1$ because this SV represents the variability of all $ab$ scores about
the grand mean. The $SS_{cell}$ is distributed on $ab-1$ because it introduces the variability of the
ab cell means about the grand mean. The $df$ for the main effects has the same form as in
Chapter 8; these SV reflect the variance of the $a$ (or $b$) means about the grand mean and
one one is df. The selection of degrees of freedom is

```
$df_{AB} = (ab-1)-(a-1)-(b-1)=(a-1)(b-1)$
```