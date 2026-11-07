
The coefficient here on `T̂`, at 1.46, is very close to the theoretical value of 1.5 established in the simulation. The t-statistic on the coefficient of `T` in Eqn. (4.17) is 28.1, compared to 3.6 in Eqn. (4.19). Ignoring the endogeneity issue may give estimates that are precisely wrong, while IV estimates are approximately right.

Despite the difficulty in identifying compelling instruments, IV is popular because it is frequently the only identification technique available. We have used the approach to help measure the impact of microcredit in Thailand: Borrowers may be different from non-borrowers, but the Thailand Village Fund makes a fixed amount of credit available per village. In smaller villages, the probability of a loan (`T`) is higher, so village size can serve as an instrument for microcredit borrowing ([Haughton and Khandker 2009](#chapter4.xhtml#ref4_18)). We have also looked at the impact of different scripts in a fundraising telemarketing campaign. Not everyone picks up the phone, but calling someone is an instrument that helps drive whether one picks up the phone, while not influencing whether they donate, given that they pick up the phone ([Lo and Li 2021](#chapter4.xhtml#ref4_23)).

If we assume that everyone responds to treatment (such as a credit card offer) in the same way, we have the homogeneous response case, and the results may plausibly be generalized to the wider population, giving the results external validity. However, it is often the case that we have heterogeneous responses to treatment – women may respond differently compared to men, for instance – in which case we only have a LATE on the outcome, and there may be low external validity.

Consider again the campaign to offer credit cards. Using the terminology of [Angrist et al. (1996)](#chapter4.xhtml#ref4_3), some people may sign up for a credit card even without the offer (“always takers”), some may never accept another credit card (“never takers”), a few might give up credit cards when they get another offer (“defiers”), and the remaining subpopulation responds to the offer (“compliers”). When responses are heterogeneous and a number of assumptions are met ([Imbens 2014](#chapter4.xhtml#ref4_21)), the IV estimates only measure the effect of treatment on the compliers. This might be a special group, not necessarily representative of the population as a whole, and it may be difficult to identify, in which case the scope of application of the measure of impact is hard to determine ([Imbens 2014](#chapter4.xhtml#ref4_21)).

Page 97 The field of practical causal inference is rapidly expanding. The techniques discussed in [Chapters 3](#chapter3.xhtml) and [4](#chapter4.xhtml) provide an introduction to the field and should be enough to allow the user to get started with the estimation of causal effects.

## Notes

1. We assumed `GPA ∼ N(3,0.4)`, and `Y = 40 + 10 × GPA + N(0,10)`. [⏎](#chapter4.xhtml#en4_14b)
2. Here `Y = 40 + 7 × T + 10 × GPA + N(0,10)`, where `T` is the “treatment,” here induction into the honors program. [⏎](#chapter4.xhtml#en4_24b)

## References

* Abadie, Alberto. 2021. “Using Synthetic Controls: Feasibility, Data Requirements, and Methodological Aspects”. Journal of Economic Literature, 59(2): 391–425. [⏎](#chapter4.xhtml#b4ref4_1)
* Abadie, Alberto, and Javier Gardeazabal. 2003. “The Economic Costs of Conflict: A Case Study of the Basque Country”. American Economic Review, 93(1): 113–132. [⏎](#chapter4.xhtml#b4ref4_2)
* Angrist, Joshua, Guido Imbens, and Donald Rubin. 1996. “Identification of Causal Effects Using Instrumental Variables”. Journal of the American Statistical Association, 91: 444–472. [⏎](#chapter4.xhtml#b4ref4_3)
* Athey, Susan, and Guido Imbens. 2017. “The State of Applied Econometrics: Causality and Policy Evaluation”. Journal of Economic Perspectives, 31(2): 3–32. [⏎](#chapter4.xhtml#b4ref4_4)
* Bernal, James Lopez, Steven Cummins, and Antonio Gasparrini. 2019. “Difference in Difference, Controlled Interrupted Time Series and Synthetic Controls”. International Journal of Epidemiology, 48(6): 2062–2063. [⏎](#chapter4.xhtml#b4ref4_5)
* Bleemer, Zachary, and Aashish Mehta. 2022. “Will Studying Economics Make You Rich? A Regression Discontinuity Analysis of the Returns to College Major”. American Economic Journal: Applied Economics, 14(2): 1–22. [⏎](#chapter4.xhtml#b4ref4_6)
* Boonperm, Jirawan, Jonathan Haughton, and Shahidur Khandker. 2013. “Does the Village Fund Matter in Thailand? Evaluating the Impact on Incomes and Spending”. Journal of Asian Economics, 25: 3–16. [⏎](#chapter4.xhtml#b4ref4_7)
* Callaway, Brantly, and Petro Sant'Anna. 2021a. “Getting Started with the DID Package”. [https://www.stata.com/new-in-stata/difference-in-differences-DID-DDD/](https://www.stata.com/new-in-stata/difference-in-differences-DID-DDD/) \[Accessed Jan 6, 2022.\] [⏎](#chapter4.xhtml#b4ref4_8)
* Callaway, Brantly, and Pedro Sant'Anna. 2021b. “Difference-in-Differences with Multiple Time Periods”. Journal of Econometrics, 225(2): 200–230. [⏎](#chapter4.xhtml#b4ref4_9)
* Calonico, Sebastian, Matias Cattaneo, Max Farrell, and Rocio Titiunik. 2017. “Rdrobust: Software for Regression-Discontinuity Designs”. Stata Journal, 17: 372–404. [⏎](#chapter4.xhtml#b4ref4_10)
* Card, David. 1990. “The Impact of the Mariel Boatlift on the Miami Labor Market”. Industrial and Labor Relations Review, 43(2): 245–257. [⏎](#chapter4.xhtml#b4ref4_11)
* Card, David, and Alan Krueger. 1994. “Minimum Wages and Employment: A Case Study of the Fast-Food Industry in New Jersey and Pennsylvania”. American Economic Review, 84(4): 772–793. [⏎](#chapter4.xhtml#b4ref4_12)
* Page 98 Card, David, David Lee, Zhuan Pei, and Andrea Weber. 2015. “Inference on Causal Effects in a Generalized Regression Kink Design”. Econometrica, 83(6): 2453–2483. [⏎](#chapter4.xhtml#b4ref4_13)
* Cunningham, Scott. 2021. Causal Inference: The Mixtape. New Haven, CT: Yale University Press. [⏎](#chapter4.xhtml#b4ref4_14)
* Flammer, Caroline, and Pratima Bansal. 2017. “Does a Long-Term Orientation Create Value? Evidence from a Regression Discontinuity”. Strategic Management Journal, 38(9): 1837–1847. [⏎](#chapter4.xhtml#b4ref4_15)
* Fremeth, Adam, Guy Holburn, and Brian Richter. 2016. “Bridging Qualitative and Quantitative Methods in Organizational Research: Applications of Synthetic Control Methodology in the U.S. Automobile Industry”. Organization Science, 27(2): 462–482. [⏎](#chapter4.xhtml#b4ref4_16)
* Gelman, Andrew, and Guido Imbens. 2019. “Why High-Order Polynomials Should Not Be Used in Regression Discontinuity Designs”. Journal of Business and Economic Statistics, 37(3): 447–456. [⏎](#chapter4.xhtml#b4ref4_17)
* Haughton, Jonathan, and Shahidur Khandker. 2009. Handbook of Poverty and Inequality. Washington, DC: World Bank. [⏎](#chapter4.xhtml#b4ref4_18)
* Hsiao, C., H. S. Ching, and S. K. Wan. 2012. “A Panel Data Approach for Program Evaluation: Measuring the Benefits of Political and Economic Integration of Hong Kong with Mainland China”. Journal of Applied Econometrics, 27: 705–740. [⏎](#chapter4.xhtml#b4ref4_19)
* Imai, Kosuke, and In Song Kim. 2020. “On the Use of Two-Way Fixed Effects Regression Models for Causal Inference with Panel Data”. Political Analysis, 29: 405–415. [⏎](#chapter4.xhtml#b4ref4_20)
* Imbens, Guido. 2014. “Instrumental Variables: An Econometrician's Perspective”. Statistical Science, 29(3): 323–358. [⏎](#chapter4.xhtml#b4ref4_21)
* Imbens, Guido, and Thomas Lemieux. 2008. “Regression Discontinuity Designs: A Guide to Practice”. Journal of Econometrics, 142(2): 615–635. [⏎](#chapter4.xhtml#b4ref4_22)
* Lo, Victor S. Y., and Zhuang Li. 2021. “Causal Inference and Machine Learning for Outbound Strategy”. *Joint Statistical Meetings (JSM) Proceedings*. American Statistical Association. [⏎](#chapter4.xhtml#b4ref4_23)
