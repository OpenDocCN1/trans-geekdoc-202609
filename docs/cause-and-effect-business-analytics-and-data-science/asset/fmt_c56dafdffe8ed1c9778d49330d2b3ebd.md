
# Chapter Reading Overview

A suggested flow of reading the book chapters is outlined in [Figure 1.8](#chapter1.xhtml#fig1_8). [Chapter 2](#chapter2.xhtml) serves as a review of common statistical, econometric, and Machine Learning techniques, on which subsequent chapters on causal business analytics and uplift modeling are built. Readers who are familiar with these common techniques can skip to other chapters. [Chapter 3](#chapter3.xhtml) introduces causal business analytics (causal inference in business) with more standard methodologies such as randomized experiments (also known as A/B testing), potential outcomes approach, and propensity score matching. [Chapter 4](#chapter4.xhtml) describes additional causal inference techniques that are widely used in economics and sociology, including synthetic controls, double differences, and instrumental variables, but they can also be utilized in business. [Chapter 5](#chapter5.xhtml) discusses a powerful AI-based approach known as Directed Acyclic Graphs or Bayesian Networks that can be employed to discover and quantify causal relationships between variables, with or without prior knowledge of the likely causal pathways.

![Figure 1.8 Suggested flow of book chapters. ⏎](images/fig1_8.jpg)

Figure 1.8 Suggested flow of book chapters. [⏎](#chapter1.xhtml#b1fig1_8)

Uplift analytics is discussed in [Chapters 6](#chapter6.xhtml)–[9](#chapter9.xhtml). [Chapter 6](#chapter6.xhtml) introduces the concept of uplift analytics along with a simple modeling approach. [Chapter 7](#chapter7.xhtml) discusses the Test and Learn process for uplift, including sample size determination, experimental design, and measurement metrics. [Chapter 8](#chapter8.xhtml) provides an overview of prescriptive analytics for uplift, employing mathematical techniques to optimally match individuals to treatments. The discussion includes techniques for handling the uncertainty of model estimates, based on methods from Operations Research, Finance, and Risk Management. [Chapter 9](#chapter9.xhtml) discusses selected advanced topics in uplift analytics, including some of the latest uplift modeling techniques, developing models on observational data (without randomized experiments) by combining causal inference with uplift modeling, and integrating direct response data with experimental data for uplift modeling.

[Chapter 10](#chapter10.xhtml) takes us back to causal business analytics, where data are in the form of time series, with methodologies from Marketing Science, Econometrics, and Time Series Analysis. [Chapter 10](#chapter10.xhtml) discusses various advanced topics for analyzing time series and related data. [Chapter 11](#chapter11.xhtml) introduces Structural Equation Modeling (SEM), originally from Psychology and Psychometrics, which can be employed to handle business problems. We conclude the book with a discussion and summary in [Chapter 12](#chapter12.xhtml). Practical business problems and data are used for illustration throughout the book.

## Notes

1. Economists typically measure sensitivity using the own-price elasticity of demand, which is defined as $\\frac{\\partial lnS}{\\partial lnP}$ and has the virtue of being unit-free. [⏎](#chapter1.xhtml#en1_11b)

2. Using the previous fitted sales function from [Figure 1.5a](#chapter1.xhtml#fig1_5), where confounders are included, the price would be $6.09 and the daily profit would be `f(6.09) = (391.5 – 33*6.09) * (6.09 – 2) = $779.27`, resulting in a reduction of $23.38 in daily profit. [⏎](#chapter1.xhtml#en1_21b)

3. For simplicity, we assume that the control group receives no treatment, that is, remains uncontacted. In practice, the control group may receive an older treatment (e.g., a legacy intervention method) in marketing or a “placebo” in clinical trials. [⏎](#chapter1.xhtml#en1_31b)

## References

* Angrist, Joshua, and Jorn-Steffen Pischke. 2009. Mostly Harmless Econometrics: An Empiricist's Companion. Princeton, NJ: Princeton University Press. [⏎](#chapter1.xhtml#b1ref1_1)

* Angrist, Joshua, and Jorn-Steffen Pischke. 2014. Mastering Metrics: The Path from Cause to Effect. Princeton, NJ: Princeton University Press. [⏎](#chapter1.xhtml#b1ref1_2)

* Athey, S., and G. W. Imbens. 2015. “Machine learning methods for estimating heterogeneous causal effects”. Working Paper, Graduate School of Business, Stanford University. [⏎](#chapter1.xhtml#b1ref1_3)

* Cartwright, Nancy. 2007. Hunting Causes and Using Them: Approaches in Philosophy and Economics. New York, NY: Cambridge University Press. [⏎](#chapter1.xhtml#b1ref1_4)

* Cartwright, Nancy, and Jeremy Hardie. 2012. Evidence-Based Policy: A Practical Guide to Doing It Better. New York, NY: Oxford University Press. [⏎](#chapter1.xhtml#b1ref1_5)

* Dunning, Thad. 2016. Natural Experiments in the Social Sciences: A Design-Based Approach. Cambridge: Cambridge University Press. [⏎](#chapter1.xhtml#b1ref1_6)

* Gertler, Paul J., Sebastian Martinez, Patrick Premand, Laura B. Rawlings, and Christel M.J. Vermeersch. 2016. Impact Evaluation in Practice, 2nd edition. Washington, DC: World Bank Group. [⏎](#chapter1.xhtml#b1ref1_7)

* Glymour, Clark. 2001. The Mind's Arrows: Bayes Nets and Graphical Causal Models in Psychology. Cambridge, MA: MIT Press. [⏎](#chapter1.xhtml#b1ref1_8)

* Green, Paul E., and V. Srinivasan. 1990. “Conjoint Analysis in Marketing Research: New Developments and Directions”. Journal of Marketing, 54(4): 3–19. [⏎](#chapter1.xhtml#b1ref1_9)

* Hernan, Miguel A., and James M. Robins. 2020. Causal Inference. Boca Raton, FL: Taylor & Francis. [⏎](#chapter1.xhtml#b1ref1_10)

* Imbens, Guido W., and Donald B. Rubin. 2015. Causal Inference for Statistics, Social, and Biomedical Sciences: An Introduction. New York, NY: Cambridge University Press. [⏎](#chapter1.xhtml#b1ref1_11)

* Jackson, Robert, and Paul Wang. 1996. Strategic Database Marketing. Chicago, IL: NTC Publishing. [⏎](#chapter1.xhtml#b1ref1_12)

* Jordan, Michael I. 2019. “Artificial Intelligence – The Revolution Has Not Happened Yet”. *Harvard Data Science Review*, issue 1.1. [https://hdsr.mitpress.mit.edu/pub/wot7mkc1](https://hdsr.mitpress.mit.edu/pub/wot7mkc1) [⏎](#chapter1.xhtml#b1ref1_13)

* Lee, Myoung-Jae. 2005. Micro-Econometrics for Policy, Program, and Treatment Effects. New York, NY: Oxford University Press. [⏎](#chapter1.xhtml#b1ref1_14)

* Lee, Myoung-Jae. 2016. Matching, Regression Discontinuity, Difference in Differences, and Beyond. New York, NY: Oxford University Press. [⏎](#chapter1.xhtml#b1ref1_15)

* Lo, Victor S. Y. 2019a. “Searching for the Perfect Unicorn”. Informs: Analytics, 1(1). [https://doi.org/10.1162/99608f92.ba20f892](https://doi.org/10.1162/99608f92.ba20f892) [⏎](#chapter1.xhtml#b1ref1_16)

* Lo, Victor S. Y. 2019b. “Three Types of Analytics Used in Practice and their Links”. *CIO Review*. [⏎](#chapter1.xhtml#b1ref1_17)

* Meng, Xiao-Li. 2019. “Data Science: An Artificial Ecosystem”. Harvard Data Science Review, 1(1). [https://doi.org/10.1162/99608f92.ba20f892](https://doi.org/10.1162/99608f92.ba20f892) [⏎](#chapter1.xhtml#b1ref1_18)

* Morgan, Stephen, and Christopher Winship. 2015. Counterfactuals and Causal Inference Methods and Principles for Social Research, 2nd edition. New York, NY: Cambridge University Press.

* Rosenbaum, P. R. 2002. Observational Studies. New York, NY. Springer. [⏎](#chapter1.xhtml#b1ref1_19)

* Rosenbaum, P. R. 2010. Design of Observational Studies. New York, NY. Springer. [⏎](#chapter1.xhtml#b1ref1_20)

* Rosenbaum, Paul R., and Donald B. Rubin 1983. “The Central Role of the Propensity Score in Observational Studies for Causal Effects”. Biometrika, 70(1): 41–55.

* Rubin, D. B. 2006. Matched Sampling for Causal Effects. New York, NY: Cambridge University Press. [⏎](#chapter1.xhtml#b1ref1_22)
