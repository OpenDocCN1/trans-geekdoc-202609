
## 326 Research Design and Statistical Analysis

Table 12.4 Data and analysis for a repeated-measures design
(a) the data

| Subject | Beer 1 | Beer 2 | Beer 3 | Beer 4 | Mean |
|---|---|---|---|---|---||
| 1 | 2 | 5 | 3 | 3 | 3.25 |
| 2 | 4 | 6 | 5 | 4 | 4.75 |
| 3 | 5 | 7 | 4 | 5 | 5.25 |
| 4 | 3 | 4 | 4 | 3 | 3.50 |
| 5 | 6 | 7 | 6 | 5 | 6.00 |
| 6 | 2 | 5 | 4 | 3 | 3.50 |
| 7 | 4 | 5 | 6 | 6 | 4.75 |
| 8 | 3 | 6 | 4 | 6 | 4.75 |
| Mean | 3.63 | 5.63 | 4.38 | 4.25 | 4.47 |

(b) the ANOVA

| SV | df | Sum of squares | Mean square | F |
|---|---|---|---|---|
| Participants (S) | 7 | 26.219 | 3.746 | 6.091 |
| Beer (A) | 3 | 16.844 | 5.615 | 9.136 |
| Residual | 21 | 12.906 | .615 | |

In general, this participants × design involves a levels of the treatment variable and n participants; a = 4 and n = 8. Mean squares are calculated as in the two-way completely randomized or × blocks design. The term labeled "residual" in Table 12.4 comes as an interaction of S x A; the only anomaly of the calculations is that there is only one score per cell instead of a mean of scores, as in between-participants design. The residual term serves as the error term to test the effect of A, as we will justify in Section 12.5.3.

The design summarized in Table 12.4 is usually referred to as a one-way, repeated-measures design. In the case of the one-way, completely randomized design, recall that we were able to partition the total variance into two sources of variance—the main effect of A and S/A served as the error term. However, that each participant participates in all conditions of the experiment makes it possible to distinguish the main effect of participants from interaction with treatments ("residual") in Table 12.4b. This finer partitioning of the variance in the repeated-measures design usually results in a substantial reduction of the error term (i.c., "residual") relative to the completely randomized design. For example, if the data in Table 12.4 had been included in a CR between-participants design, the MS/A would be 1.397, more than double the repeated-measures error term.

Earlier (Section 12.3.2), we attributed the greater efficiency of the T × B design to the fact that blocking removed some individual difference variability from the error term, thus reducing the error term relative to the completely randomized design. The use of a concomitant variable in ANCOVA was similarly presented as statistically removing some individual variability from the error term, relative to the completely randomized design. In the case of the repeated-measures design, we are essentially blocking by participants, with the result that differences in the performances of participants are entirely removed from the error term of that design. Thus, the participants x treatments design will typically result in a smaller error term than any of the designs we have considered to this point.

The Participants source of variance (S) provides an indication of the potential increase in power if an RM design is used instead of a CR design. In many types of research, we expect to find considerable individual differences in performance. This variability would be a component of the error term of the ANOVA for a CR design. Thus, the repeated-measures design would be more efficient than the completely randomized design (and between-participants designs) when there is substantial individual variability. However, if there is little variability among participants', it would suggest that if we had not greatly reduced variance relative to the CR design, the repeated-measures design could be less efficient than the completely randomized design because the RM design has fewer degrees of freedom. In the example of Table 12.4, there are only 21 degrees of freedom compared to 28 in a completely randomized design with the same number of scores. To better understand the efficiency of the RM design compared to CR, we will consider the expected means.

## 12.5.3 Expected Mean Squares and Relative Efficiency

Panel a of Table 12.5 presents the results of 5,000 independent simulations of two experimental designs. In each simulated replication of the completely randomized experiment, there were three groups of 10 scores; each of the 30 scores consisted of an error component and an individual difference component. The three groups of each had a different treatment effect added. For the replications of the repeated-measures experiment, the three scores for a simulated partition contained different errors of measurement, but all three scores had the same value of the individual difference error. The two types of errors

Table 12.5 Results of analyses of variance for completely randomized and repeated-measures designs, based on 5,000 replications (a) and expected mean squares (b)

(a) Simulation results

| Completely randomized design | | | | Repeated-measures design | | | | | |
|---|---|---|---|---|---|---|---|---|---|
| SV | df | SS | MS | SV | df | MS | Power | | |
| A | 2 | 588.39 | 294.69 | .235 | A | 2 | 391.53 | 195.77 | .684 |
| S/A | 27 | 3,666.55 | 135.50 | | Subjects | 9 | 3,024.17 | 336.02 | | |
| Total | 29 | 4,255.93 | | | Residual | 18 | 650.68 | 36.15 | | |
| | | | | | Total | 29 | 4,066.38 | | | |

(b) Expected mean squares

| Completely randomized design | | Repeated-measures design | | |
| SV | df | EMS | SV | df | EMS |
|---|---|---|---|---|---|
| A | a - 1 | | A | a - 1 | |
| | | $\sigma^2 + a\sigma^2$ | | | $\sigma^2 + \sigma^2$ |
| S/A | a(n - 1) | | Subjects | n - 1 | |
| | | $\sigma^2 + an\sigma^2$ | | | $\sigma^2 + an\sigma^2$ |
| Total | | | Residual | (a-1)(n-1) | |
| | | | | | $\sigma^2 + a(n-1)\sigma^2$ |

*(Note: The table structure for (b) was reconstructed based on standard ANOVA theory as the OCR was fragmented)*

## Comparing Experimental Designs and Analyses 327

(Note: The prompt text for page 347 contained a header and fragmented text, the logical flow follows from the section above.)

