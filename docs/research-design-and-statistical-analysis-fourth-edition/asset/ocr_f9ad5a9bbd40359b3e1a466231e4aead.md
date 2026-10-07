# 376 Research Design and Statistical Analysis

Table 14.9 Expected mean squares and errors for a design with one- and within-participants factors

| SV | df | EMS | Error term |
|---|---|---||}{
| A | a-1 | $\sigma^2 + bca^2_A$ | S/A |
| S/A | $n-1$ | $\sigma^2 + bca^2_{S/A}$ | |
| B | b-1 | $\sigma^2 + \sigma^2_{SB/A} + nca^2_B$ | SB/A |
| AB | $(a-1)(b-1)$ | $\sigma^2 + \sigma^2_{SB/A} + ncb^2_{AB}$ | SB/A |
| SC/A | $n(a-1)(b-1)$ | $\sigma^2 + \sigma^2_{SC/A}$ | |
| C | c-1 | $\sigma^2 + \sigma^2_{BC/A} + nab^2_C$ | SC/A |
| AC | $(a-1)(c-1)$ | $\sigma^2 + \sigma^2_{SC/A} + nbc^2_{AC}$ | SC/A |
| SB/A | $n(a-1)(c-1)$ | $\sigma^2 + \sigma^2_{SCA}$ | |
| BC | $(b-1)(c-1)$ | $\sigma^2 + \sigma^2_{BC/A} + nca^2_{BC}$ | SBC/A |
| ABC | $(a-1)(b-1)(c-1)$ | $\sigma^2 + \sigma^2_{SCA} + nab^2_{ABC}$ | SBC/A |
| SBC/A | $(a-1)(b-1)(c-1)$ | $\sigma^2 + \sigma^2_{SBC/A}$ | |

*Note: A, B, and C are all assumed to have fixed effects.*

treatment is applied, so that there are no systematic differences in the test scores across levels of A. The posttest scores reflect the effects of the treatment, if there are any.
Although posttest designs are common, they are often analyzed in a less optimal way. One common analysis is a mixed factors ANOVA with test (prev posttest as the within-participant factor. With this analysis, the F test for the main effect A will be very conservative because the test scores cannot be affected by the treatment. Another common strategy is to compute a gain score (posttest – pretest) for each participant and then conduct a one-factor-between-participants ANOVA; this analysis is equivalent to testing the interaction effect in the mixed design. which the covariate is the pretest score and the dependent variable is the posttest score. For this reason, we recommend using ANCOVA to analyze the results from a posttest design (see Chapter 24).

# 14.4 Designs With More Than One Random-Effects Factor: The Fixed- as Random-Effects Distinction Again

Recall from Section 13.3 that the distinction between random- and fixed-effects refers to how levels of a factor are sampled. In the case of a fixed-effects factor, the levels of the factor are either chosen in such a way that exhaust all possible levels or they are selectively from all possible levels. An example of the former is taking observations from all four seasons in the Seasons data. Examples of the latter are common, as in our hypothetical experiment where face orientation and distortion orientations are manipulated. For both, the experimenter intentionally chose the specific orientations and particular distortions to be included in the experiment. In both cases, the levels of the variables were presumably chosen to be a representative range of variation on each dimension.

In case of a random-effects factor, the levels of the factor do not exhaust all possible levels of the variable nor are they selected in a systematic way. Instead, levels are randomly chosen subset of a much larger potential set of observations. The sole example of a random-effects factor that we have encountered in this point is participants.