38.4.2 Empirical results . . . . . . . . . . . . . . . . 1504
38.4.3 Results analysis . . . . . . . . . . . . . . . . 1507
38.5 Conclusion . . . . . . . . . . . . . . . . . . . . . 1513
Bibliography . . . . . . . . . . . . . . . . . . . . . . 1513
Appendix 38A: Individual Copulas . . . . . . . . . . . 1516
Appendix 38B: Marginal Distributions . . . . . . . . . 1617

# Abstract

This chapter proposes a mixture copula framework for integration of different types of bank risks, which is able to capture comprehensively the nonlinearity, tail dependence, tail asymmetry and structure asymmetry of bank risk dependence. We analyze why mixture copula is well-suited for bank risk integration, discuss how to construct a proper mixture copula and present detailed steps for using mixture copula. In the empirical analysis, the proposed framework is employed to model the dependence structure between credit risk, market risk and operational risk of Chinese banks. The comparisons with seven other major approaches provide strong evidence of the effectiveness of the constructed mixture copulas and help to uncover several important pitfalls and misunderstandings in risk dependence modeling.

Keywords
Bank risk ● Credit risk ● Market risk ● Operational risk ● Risk management ● Risk dependence ● Risk integration ● Simple summation approach ● Variance–covariance approach ● Mixture copula ● Basel committee on banking supervision ● Tail dependence.

# 38.1 Introduction

Bank risk integration is always a great challenge for both researchers and practitioners because correlations between various types of bank risks are highly complicated (Basel Committee on Banking Supervision, BCBS, 2010; Baker and Filbeck 2015). Commercial banks face many types of risks, such as credit risk, market risk and operational risk (BCBS 2006). These risks are not independent; on the contrary, they are intrinsically related to each other (Breuer et al., 2010; Imbierowicz and Rauch, 2014). This becomes evident very early in banks’ day-to-day business and was realized fully when the subprime crisis started in 2007 (Hartmann, 2010; Gagliardini and Gourieroux, 2013). Therefore, when integrating different risk types, accurate descriptions of the dependencies between them are extremely important (BCBS, 2010; Grundke, 2013). However, the dependence structure between bank risks is rather difficult to capture because it is characterized by four sophisticated