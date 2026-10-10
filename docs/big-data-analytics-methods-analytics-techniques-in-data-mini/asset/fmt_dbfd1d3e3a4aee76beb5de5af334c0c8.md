
# Propensity Score Matching (PSM)

Propensity score matching (PSM) is a technique used to reduce the effects of confounding in observational studies. When we compare the effects of the treatment in a population, we want to be certain that the response to the treatment is based on the treatment, and not due to our selection bias. Hence we use PSM to determine the selection bias between two groups that respond positively and negatively to a treatment. It allows one to mimic some of the characteristics of randomized controlled trial studies. PSM works by matching treated and untreated observations on the estimated probability of being treated (propensity score).

PSM is implemented by matching one-to-one or pair matching, in which pairs of treated and untreated subjects are formed, such that matched subjects have similar values of the propensity score. Said differently, a propensity score is the probability that a person being assigned to a particular group given a set of observed covariates. Propensity scores are used to reduce selection bias by equating groups based on these covariates.

PSM estimates the effect of a treatment or drug by accounting for co-variables that predict receiving the treatment. This approach reduces bias due to confounding variables which can be found in the estimate of the treatment. Use PSM to account for systematic differences in baseline characteristics between treated and untreated subjects when estimating the effect of treatment on outcomes. The PSM method is available in several statistical packages including R as part of the `MatchIt` package.

Propensity score matching entails forming matched sets of treated and untreated subjects who share a similar value of the propensity score (Rosenbaum & Rubin 1983). Propensity score matching allows one to estimate the `average treatment effect of the treated` (ATT).

The most common implementation of propensity score matching is one-to-one or pair matching, in which pairs of treated and untreated subjects are formed, such that matched subjects have similar values of the propensity score. Although one-to-one matching appears to be the most common approach to propensity score matching, other approaches can be used. These are discussed at the end of this section. Unless stated otherwise, the following discussion is in the context of 1:1 matching.

Once a matched sample has been formed, the treatment effect can be estimated by directly comparing outcomes between treated and untreated subjects in the matched sample.

## Steps Used in Implementing PSM

1.  You need representative and comparable data for both treatment and comparison groups. You can run logistic regression if your data includes categorical data. To run the regression model, assume the dependent variable: `Y=1` for participate, or `Y=0` otherwise (not participate).

2.  Use a logit (or other discrete choice model) to estimate program participations as a function of observable characteristics.

3.  Use predicted values from logit to generate a propensity score `p(x[i])` for all treatment and comparison group members.

4.  **Match Pairs**: Individuals with similar covariates are matched together from both groups (from treatment group and comparison group).

5.  You need to determine a `tolerance limit`: how different can control individuals or subjects be and still be a match? You can choose any method like the nearest neighbor to match individuals from both groups.

6.  Once matches are made, we can calculate impact by comparing the means of outcomes across participants and their matched pairs.

The ideal comparison group is selected such that it matches the treatment group using either a comprehensive baseline survey or time invariant characteristics. The matches are selected on the basis of similarities in observed characteristics. Of course, this approach assumes no selection bias based on unobserved characteristics of subjects in the study.

In summary, for matching pairs, compare probability of data against what is predicted by regression. You can run logistic regression if your data includes categorical data. To run the regression model, assume the dependent variable: `Y=1` for participate, or `Y=0` otherwise (not participate). Then choose appropriate confounders (variables associated with treatment and outcome).

Next compute the propensity score: predicted probability `(p)` or `log[p/(1-p)]`. As the next step, `check` that the propensity score is balanced across treatment and comparison groups. Check that covariates are balanced across treatment and comparison groups using standardized differences to examine distributions. Next, match each participant to one or more non-participants in propensity score (using nearest neighbor matching or stratification matching or other methods). You must verify that covariates are balanced across treatment and comparison groups in the matched sample. Finally, you can apply multivariate analysis based on the new data sample.

## 6.35 Adherence Analysis Method

The `adherence analysis method` is often used in healthcare to measure patient adherence to a given practice or medication regimen. It measures the degree to which patients follow the treatment and recommendation of their health professionals. This method is used across many disease conditions. Adherence analysis studies have shown that patient in-adherence average is about 50%.

Adherence can be measured across time: longitudinal, cross-sectional and retrospectively. Adherence may be measured by regimen: medication, health-behavior, appointment-keeping and similar regimen. Adherence analysis performs correlation analysis between treatment and patient outcomes. It calculates the `r effect size` in the data and can identify what factors are correlated to adherence. For example, an adherence analysis shows that patient adherence is highly correlated to physician's communication skills.

## 6.36 Meta-analysis Methods

Meta-analysis is the systemic examination of multiple studies. This form of analysis typically combines results from multiple research articles about the same type of data and the same hypothesis. For example, let's assume that you're performing meta-analysis on the impact of electric cars on local economy. Some research might claim that electric cars have a positive impact while some might conclude the opposite. Both have applied rigorous scientific and statistical methods and data analytics to reach different conclusions. So, how do you reconcile these articles? This is where meta-analysis comes in.

To perform meta-analysis, data from these multiple studies are compiled from prior publications, research papers and data bases. Each article may have a different statistical significance and effect size that must be considered. There are certain Inclusion-Exclusion criteria applied in this type of analysis. Common Inclusion-Exclusion criteria include:

*   Studies that are peer-reviewed are preferred. You may decide to include only these articles in your meta-analysis
*   Time horizon of studies. You may choose articles that are more recent, say in the last 5 years and exclude any research result older than 5 years.
*   Population demographics: Geographic and language. You may include all populations globally, or limit your meta-analysis to certain populations or languages. The strength and the power of your meta-analysis depends on these choices.

For meta-analysis, you must consider coding the articles and determine the effect size of each prior study in these articles. This is known as article coding and effect size extraction. The article coding and effect size extraction applies the following steps:
