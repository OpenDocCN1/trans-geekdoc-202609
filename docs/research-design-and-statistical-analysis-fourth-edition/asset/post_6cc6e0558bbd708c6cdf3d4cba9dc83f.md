
> AnovaCl(data = datM, BDI_transform ~ health + activity + education, type=3)
Anova Table (Type III tests)

Response: BDI_transform
| Sum Sq | Df | F value | Pr(>F) |
| :--- | :--- | :--- | :--- | :--- |
| (Intercept) | 13.819 | 1 | 27.3986 | 8.425e-07 *** |
| health | 15.676 | 1 | 31.0788 | 1.903e-07 *** |
| activity | 6.538 | 1 | 43.0016 | 0.0004628 *** |
| education | 1.102 | 1 | 2.1853 | 0.142302 |
| Residuals | 53.465 | 106 | | |

Signif. codes: 0 **** 0.001 *** 0.01 ** 0.05 * ' ' 1

> AnovaCl(data = datW, BDI_transform ~ health + activity + education, type=3)
Anova Table (Type III tests)

Response: BDI_transform
| Sum Sq | Df | F value | Pr(>F) |
| :--- | :--- | :--- | :--- | :--- |
| (Intercept) | 36.759 | 1 | 36.0197 | 2.79e-08 *** |
| health | 8.921 | 1 | 8.7420 | 0.003827 ** |
| activity | 4.897 | 1 | 4.7987 | 0.030652 * |
| education | 4.288 | 1 | 4.2016 | 0.042831 * |
| Residuals | 109.195 | 107 | | |

Signif. codes: 0 **** 0.001 *** 0.01 ** 0.05 * ' ' 1

> AnovaCl(data = datM, BDI_transform ~ activity), type=3)
Anova Table (Type III tests)

Response: BDI_transform
| Sum Sq | Df | F value | Pr(>F) |
| :--- | :--- | :--- | :--- | :--- |
| (Intercept) | 36.658 | 1 | 552.5609 < 2.2e-16 *** |
| activity | 8.54 | 1 | 12.9098 | 0.0004943 *** |
| Residuals | 71.47 | 108 | | |

Signif. codes: 0 **** 0.001 *** 0.01 ** 0.05 * ' ' 1

> AnovaCl(data = datW, BDI_transform ~ activity), type=3)
Anova Table (Type III tests)

Response: BDI_transform
| Sum Sq | Df | F value | Pr(>F) |
| :--- | :--- | :--- | :--- | :--- |
| (Intercept) | 478.050 | 1 | 417.1795 < 2e-16 *** |
| activity | 7.220 | 1 | 6.2863 | 0.01364 * |
| Residuals | 124.900 | 109 | | |

Signif. codes: 0 **** 0.001 *** 0.01 ** 0.05 * ' ' 1

Figure 25.1 ANCOVA results from R for the Activity experiment for participants identifying as men (Panel a) and as women (Panel b), and the ANOVA results for men (Panel c) and women (Panel d).

## 25.7 Summary and More Discussion

In the first, observational study, we used several regression analyses to point out the difficulty of assessing the influence of different kinds of physical activity. The main question was whether leisure-time physical activity reduced symptoms of depression. We were unable to reach a definitive answer to this question because we could not separate the effects of activity from the effects of other variables. Possible reasons why leisure-time physical activity may be a proxy for other measures include the following (as well as many): people with higher BMI values tended to be more depressed and also exercise less; people with less education tended to be more depressed and also tend to work in jobs that involve more physical activity, so they have less energy to engage in leisure-related exercise; and so on.

The most direct way to access the effect of leisure-time physical activity on depression is to conduct an experiment in which participants are randomly assigned to different exercise conditions. That is what we did in the second, hypothetical study. In addition, we included health and education measures as covariates, both variables correlated significantly with depression in the observational study. Their inclusion in the design theoretically permitted a powerful test of the relationship between leisure activity and depression. In fact, it turned out that the covariates were significantly, not strongly, related to the dependent variable, so there was a negligible effect on power. A significant relationship between leisure activity and depression was found, suggesting that exercise tends to reduce depression. In the experiment, there is less ambiguity in interpreting the statistical relationship between the two measures because the random assignment of participants to conditions eliminated serious confounding of leisure activity with other influences on depression.

Although a major goal of Section 25.6 was to consider how data from a follow-up experiment might limit the generality of the conclusions from such an experiment, we should have no illusions that a single, simple experiment of the sort described previously would settle the once and for all. Some issues that might impair our ability to arrive at definitive conclusions from our simple experiment include the following.

### Issues Regarding the Selection of Participants

The choice of participants in the experiment is critical. If participants are selected from the HMO lists used in the Seasons study and are contacted by telephone and asked to participate in the experiment, on what basis will they decide whether to participate? Participants will self-select, and this will be influenced by what they are told about the experiment. If the study is presented to potential participants as a study on depression, rather than a study of blood lipids and exercise, it may influence whether participants with higher depression scores will decide to volunteer. Relatedly, when potential participants hear about the time commitment, many will decide against participation due to lack of motivation to devote that time or other commitments (e.g., their jobs) make it onerous to find the required time.

Another issue for these potential participants, given their range of health and age, is that they may not all be capable of participating in a vigorous exercise condition. In any event, the effects of vigorous exercise might be different for different kinds of participants.

### Integrated Analysis IV 675

If we did not have access to the HMO patient pool and instead selected volunteers from university classes, participants would be young adults with more similar age, educational level, and health backgrounds. The results of the experiment would be useful but would not readily generalize to the population at large.

### Issues Regarding the Choice of Experimental and Control Conditions

We must be careful about the control conditions that are used. In the experiment we described earlier, there were two conditions, a vigorous exercise condition and a minimal exercise condition in which participants participated in a group discussion. It could be argued that the second condition is not an appropriate control. We might wish to have several exercise conditions: low, moderate, and vigorous. Part of the motivation is that although the effect of exercise on depression is not a completely settled issue in the scientific literature, it is presented as a fact on the internet - insert "exercise and depression" into a search engine and read what comes up. Because of this, we assume many participants will have the expectation that an exercise program reduces depression. The consequence for us is that we must contend with placebo effects - the expectation would be that exercise should help and this expectation might have positive effects on depression. Therefore, we might be better off using several different activity conditions. Also, we want to separate the "social" effects of going out and to the gym from the effects of exercise itself. Therefore, we might want to add conditions in which participants engaged in some exercise program sure for participants who already engaged in different amounts of occupational or household activity. We also want to look at the potentially different beneficial of leisure to be successful in sorting all out. But it would not be simple.

We also note that it would have been possible to design a more powerful experiment than was presented earlier. In the Seasons study, the BDI was administered quarterly, and we can see that correlations for BDI scores obtained roughly months apart are approximately .7 to both men and women. We could have used a pretestposttest design in which we administered the BDI both at the beginning and at the end of the experiment and used the prest score as the covariate in the ANCOVA.

Finally, we should note that in many research contexts, it is not possible to conduct an experiment. We may be unable to manipulate the variables of interest, or it may be unethical to do so. In this case, the best we can do is to conduct an observational study and try to control for possible moderator variables statistically.

# Exercises

25.1 Using the data in the file Seasons physical activity, reproduce the analyses reported in Tables 25–25. Remember that these analyses were based only on participants who were employed full or part time (employed = 1 or employed = 2).

25.2 Given the type of observational study described in Chapter 25, estimate the number of cases required to yield power = .80 for a test of a medium-sized effect (f² = .15) of leisure-time exercise on depression in a regression which there are three additional predictors: age and measures of occupational and household exercise. This type of a priori power calculation is described in Chapter 21.
