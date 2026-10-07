# 23.3.1 Orthogonal Designs

A regression analysis of a factorial design can be performed if both the factors and their interactions are coded by sets of dummy variables. Although it is generally more practical to analyze orthogonal designs with software designed to perform ANOVAs, it is useful to understand how such designs might be analyzed by regression. This will provide a deeper understanding of ANOVA as a special case of regression. In addition, greater facility with coding of categorical variables will provide the researcher with greater facility in analysis of designs that consist of combinatorial and quantitative variables.

Panel a of Table 23.2 contains data from a 3 x 3 design with factors A and C (we use C rather than B to refer to the second factor because of the large number of bs in the chapter). Panel b contains sets of effect dummy variables that code the design, where effect coding is used to code the categorical variables. Each set of dummy variables has as many as the corresponding sets of variance dfs. A and C are coded as though each were the only factor in the design, and the set of four dummy variables that code the AC interaction is obtained by multiplying each dummy variable in the A set by each one in the C set. Together, the eight dummy variables code membership in the nine cells of the set. Panel c contains the results of ANOVA on the data.

With coding, the dummy variables within any one of the A, C, and AC sets are correlated. However, if the cell frequencies are all equal, the dummy variables in any set are uncorrelated with all the dummy variables in any of the other sets; therefore, the sums of squares associated with the different sets do not overlap. Let us use the notation R_{Y,A}, R_{Y,C}, R_{Y,AC} to represent the multiple correlation coefficients that result when Y is regressed on the sets of dummy variables that code A, AC, and both A and AC, respectively. Then, because the sets of dummy variables corresponding to A, C, and AC are uncorrelated, we have

```
$R_{Y,AC}^2 = R_{Y,A}^2 + R_{Y,C}^2 + R_{Y,AC}^2$
```

Multiplying each of the squared correlations by SS_y, we have

```
$SS_{Between cell} = SS_A + SS_C + SS_{AC}$
```

That is, the between-cells variability is partitioned into the main effects of A and C, and their interaction. Because we have enough coding variables to account for all the between-participants variability, $SS_{error} = SS_{residual} = (1 - R_{Y,AC,AC}^2)SS_y$ and tests of the A and C main effects and the AC interaction, respectively, are provided by

```
$F = \frac{R_{Y
```

```
$F = \frac{R_{Y
```

and

```
$F = \frac{R_{Y,AC}^2 / (a-1)(c-1)}{(1 - R_{Y,AC,AC}^2 / (N-ac))}$
```