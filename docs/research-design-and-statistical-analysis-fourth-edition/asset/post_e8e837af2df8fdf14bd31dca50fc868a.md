
# Multi-Factor Between-Participants Designs 255

- b) Estimate the population effects (the $\alpha_y$ and $\beta_k$) and the interaction effects [the $(\alpha\beta)_{jk}$ for the data in part (a).

- c) Using the estimated effects, calculate the main and interaction sums of squares. How do the results from part (a) compare?

## 9.2 [EMS and power]

- a) State the EMS for the data in Exercise 9.1. Coefficients for variance components should be numbers, not letters.

- b) Based on EMS, estimate Cohen's $f$ for $B$.

- c) The number of observations in this study was quite small. Assuming the estimate in part (b), what total sample size ($N$) would be needed to have .8 power to test $B$?

## 9.3 [Understanding means squares and simple effects]
A researcher publishes the following means and variances; $n=10$. We wish to verify the results of the analysis and perform further tests.

| | $B_1$ | $B_2$ | $B_3$ | $B_1$ | $B_2$ | $B_3$ |
|---|---|---|---|---|---|---|
| $A_1$ | 2.6 | 4.3 | 6.5 | 2.75 | 5.00 | 5.50 |
| $A_3$ | 4.3 | 3.6 | 3.4 | 1.75 | 2.25 | 3.75 |

- a) Carry out the ANOVA and present the tabled results.
b) Test the simple effects of $A$ at $B_3$.
- c) Test the simple effects of $B$ at $A_2$.
- d) Justify your choice of error terms for parts (b) and (c).

## 9.4 [Understanding means squares and simple effects]
Suppose an article contains the following table of means from a between-participants design with two factors and six scores in each cell:

| | $B_1$ | $B_2$ | $B_3$ |
|---|---|---|---|
| $A_1$ | 12 | 16 | 14 |
| $A_2$ | 18 | 14 | 12 |

In addition, the article reports that only the $AB$ interaction is significant, $F = 8.0$, $p = .002$.

- a) Reconstruct the entry ANOVA table.
- b) Test the simple effect of $B$ at $A_2$. What assumption is needed to justify your test?

## 9.5 [Calculating eta-squared]

- a) For the data set in the file $EX9\_S$, calculate general $\omega^2$ for $A$, $B$, and $AB$, assuming that $A$ and $B$ are both manipulated variables.
b) Calculate general $\eta^2$ for $B$.
- c) Repeat part (b), now assuming that $A$ represents three different personality types.

## 9.6 [Calculating omega-squared]

- a) For the data set in the file $EX9\_S$, calculate general $\omega^2$ for $A$, $B$, and $AB$, assuming that $A$ and $B$ are both manipulated variables.
b) Repeat part (a), now assuming that $A$ represents three different personality types.

# Research Design and Statistical Analysis

## 9.7 [ANOVA on real data]
In the Wiley and Voss (1999) data set (in the Wiley file on the website), the variable causal represents the number of causal connections participants introduced into essays based on the information obtained. [Note: format = 1 and 2 corresponds to Text and Web, respectively; instruct through 4 correspond to Narrative (N), Summary (S), Explanation (E), and Argument (A).]

- a) Are the assumptions under the analysis of variance met by the causal scores? Justify your answer with any relevant statistics and plots.
b) Carry out an ANOVA with format and instruct as the independent variables.
- c) Transform the data by log(causal + 1). How has this affected the results in parts (a) and (b)?

## 9.8 [Implications of hypotheses for observed data patterns]
Consider each of the following sets of hypotheses. Which sources of variance be significant? Plot means consistent with the theory.

- a) In a bar experiment, we hypothesize that Y = K x D x P where Y = bearing rate (the dependent variable), K is a constant, D = hours of deprivation, and P = number of practice trials.
b) In impression formation studies, we give participants some information on the attractiveness (A) and the intelligence (I) of an individual and ask them to rate the individual. By letting the rating, R, equals (A + I)/2.
c) Patients in a mental hospital were divided into experimental groups based on their socioeconomic status (SES, three levels) and the kind of treatment they receive (T, two levels, psychotherapy and behavior therapy). The investigator predicts that (1) psychotherapy will be less effective than behavior therapy, and (2) psychotherapy will be more effective the higher the SE level of the patient, but that will not be true for behavior therapy. In fact, no SE level is predicted for the behavior therapy patients.

## 9.9 [The relationship of t and F tests for interactions]
Assume that 40 participants are divided into good and poor readers based on a pretest. They then read either intact or scrambled text and are tested for their recall. The means and variances (in parentheses) are as follows:

| | Text | Scrambled | Intact |
|---|---|---|---|
| Good | 63 (145) | 67 (130) | |
| Poor | 37 (155) | 54 (170) | |

- a) Construct the numerator of a t test of Ability x Text.
- b) What is the denominator of t test?
- c) Calculate the t and report the level of significance. What is the value of F statistic?

## 9.10 [Calculating effect sizes from published data]

- a) Calculate general $\eta^2$ for the Text effects in Exercise 9.
b) Estimate general $\omega^2$ for the Text effects.

## 9.11 [Consequences of ignoring a systematic variable]
The file EX9_11 at the website contains five scores in a two-factor experiment. There are three levels of A, amount of reward, and two participants at each level of A.

- a) Present the ANOVA table, including EMS.
- b) Estimate general $\omega^2$ for A, treating E as extrinsic variables.
- c) Possible effects due to using more than one experiment are often ignored. Write out the ANOVA table, assuming that E has no effect.
- d) Estimate $\omega^2$ for A for this analysis.
- e) Which is the appropriate model? Why?

## 9.12 [Interpreting data in three-factor design]
Assume that the following numbers represent means in a three-factor design. Which sources contribute to the variance among means? Explain your answer.

| | $C_1$ | | | $C_2$ | | |
|---|---|---|---|---|---|---|
| | $A_1$ | $A_2$ | $A_3$ | $A_1$ | $A_2$ | $A_3$ |
| $B_1$ | 21 | 27 | 30 | 21 | 9 | 10 |
| $B_2$ | 17 | 23 | 26 | 23 | 19 | 24 |
| $B_3$ | 14 | 20 | 23 | 23 | 18 | 23 |
| $B_4$ | 16 | 22 | 25 | 22 | 18 | 23 |

## 9.13 [Intrinsic and extrinsic variables; effect sizes]
Eighty participants listened to a lecture (L) on either the impact of global warming in Alaska or the impact on wildlife in Alaska. This was then followed by a movie (M) on the impact of global warming on wildlife. They rated their agreement on a series of questions about the environment and global warming. There were equal numbers of participants who identified as male and female. The results of the analysis of variance are as follows:

| Source | df | MS | F | P |
|---|---|---|---|---|
| Movie (M) | 1 | .445 | 7.18 | .009 |
| Lecture (L) | 1 | .273 | 4.40 | .039 |
| Gender (G) | 1 | .245 | 3.77 | .056 |
| ML | 1 | .341 | 5.50 | .022 |
| LG | 1 | .076 | 1.17 | .283 |
| MG | 1 | .089 | 1.37 | .246 |
| MLG | 1 | .142 | 2.29 | .135 |
| S/MLG | 72 | .065 | | |

- a) Calculate general $\eta^2$ for the lecture and gender terms.
b) Calculate general $\omega^2$ for the movie term.

## 9.14 [Relationships among effect sizes, p-values, and power]
The Wiley.xlsx file on the website contains several dependent variables. Here we analyze the svt (sentence-verification task).

- a) Plot the cell means as a function of instruct and format, including standard error bars.
b) Perform the ANOVA.
- c) Calculate the standardized effects (Cohen's $f$) for the main and interaction effects.
d) Compare the relative sizes of the $f$ values with the $p$-values for the ANOVA. If there is a difference in ordering, why think this has happened?
e) What N would need to have .8 power to reject $H_0$ if the Format $f$ was .25 (medium, Cohen's guidelines)? What N would you need for the Instruction effect? Is there a difference? If so, why?

## 9.15 [Calculating effects sizes and power]
Assume that in a multi-factor experiment, $a = 4$, $b = 3$, and $c = 96$. Given that $MS_A = 56.8$ and $f = 2.84$:

- a) What is $n_{MS_{ABC}^2}$?
- b) Estimate $\sigma^2$ and $f^2$ for the A effect
- c) Assuming the effect size is medium (i.e., $f = .25$), what is the power to test A effect at $\alpha = .01$?

## 9.16 [Integrating intuition about effects from data patterns]
The file EX9_16 on the website contains data collected in a study by Bless, Bohner, Schwarz, and Barack (1990). These investigators manipulated the mood (1 = happy, 2 = sad) of their participants and presented them with a message (1 = strong, 2 = weak) to influence their attitude towards service fees. The dependent measure in our set is the recommended fee (in dollars) after reading the message.

- a) Describe the pattern of the cell means. What main and interaction effects are suggested by these means?
- b) Perform an ANOVA on the data. Discuss the results with reference to the plot in (a).

## 9.17 [Consequences of unbalanced design]
Following is a data with unequal $ns$. The cell totals / $ns$ ($T_{jk}/n_{jk}$)

| | $B_1$ | $B_2$ |
|---|---|---|
| $A_1$ | 20/2 | 40/4 |
| $A_2$ | 16/8 | 4/2 |

a) Calculate $SS_{cells}$. The equation is $SS_{cells} = \sum \sum n_{jk}(\hat{Y}_{jk} - \bar{Y}_{.)^2$.

b) In the same way you did part (a), calculate $SS_A$ and $SS_p$. For example, $SS_A = \sum n_j(\hat{Y}_{.j} - \bar{Y}_{..})^2$. Subtract these from $SS_{cells}$ to get $SS_{AB}$. Do you see any problem with this procedure?

c) Calculate $\hat{\alpha}_1$ and $\hat{\alpha}_2$. This requires finding the marginal (row) means for $A_1$ and $A_2$ and subtracting the grand mean. If you have done this correctly, $\sum n_j\hat{\alpha}_j = 0$ ($n_j$, total $n$ for row $j$).

d) Subtract $\hat{\alpha}_j$ from each cell mean in row $j$. Using these adjusted means, what are $SS_B$ and $SS_{AB}$? How does this compare with your answer in part (b)?

## 9.18 [Consequences of disproportionate cell frequencies]
Consider the following table of cell means. We will adjust these means for the effects of $A$ under different assumptions about cell frequencies, and by observing what happens to the column means,
