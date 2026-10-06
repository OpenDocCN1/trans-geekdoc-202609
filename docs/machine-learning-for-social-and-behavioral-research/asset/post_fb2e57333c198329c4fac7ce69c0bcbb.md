
this approach, the data are partitioned into $k$ nonoverlapping folds with $k-1$ folds used to estimate the model parameters and the $k$th fold to obtain fit information of the estimated model. This sequence is done $k$ times and the resulting values and their distributions can be compared.

Simulation research (e.g., Grimm, Ram, Shiyko, & Lo, 2013; Nylund, Asparukhov & Muthén, 2007; Tofghi & Enders, 2008) has failed to come a definitive conclusion as to which model fit index performs best across a variety of models (e.g., latent class analysis, latent profile analysis, growth mixture models), sample sizes, number of classes, and class differences. Thus, our recommendation follows Ram and Grimm's (2009) study, which identifies criteria (approximate likelihood ratio tests) and the substantive interpretation of the model parameter and the separation of latent classes (i.e., entropy). This sequence is then augmented by using $k$-fold validation to estimate the sensitivity of model estimation through multiple estimation with different folds of the data.

In addition to comparing the fit of the models with different constraints and classes, the quality of class assignment should be considered. This can be examined through the estimated posterior probabilities and the model's entropy. Often, the average posterior probabilities are calculated based on class assignment (i.e., most probable class assignment based on individual posterior probabilities) and entropy is reported. Entropy is a summary statistic of the posterior probabilities of class membership across participants.

Entropy (Asparukhov & Muthén, 2018) is defined as

> $Entropy = 1 + \frac{1}{N \ln(k)}} \left(\sum_{i=1}^{N} P(C_i = y_i) \ln(P(C_i = y_i))\right)$ (10.2)

for $i = 1$ to $N$ participants and $k = 1$ to $K$ classes, where $C_i$ is the latent class for participant $i$, and $y_i$ is a vector of observed latent class indicators. When entropy is close to 1, the posterior probabilities tend to be close to 1 or 0, which suggests that participants are well classified. When entropy is close to 0, some researchers have recommended a 0.80 threshold for entropy to consider a model; however, there are no theoretical grounds for this value.

Once an optimal model (or set of models) is determined, posterior probabilities of class membership can be estimated for each participant. Given the estimated parameters for each class, the likelihood of each participant belonging to each class can be estimated. These probabilities can then be taken into consideration associations between class membership with predictors and outcomes of class membership (see Asparhouv & Müthén, 2014). Accounting for these posterior probabilities when examining associations of the latent class variable explains the uncertainty in class membership.

## Implementation

Statistical programs to estimate mixture models have been around for many years; however

### 10.2.2 Illustrative Example

The analyzed data were restricted to a random sample of 500 participants from the Grit data. While the Grit Scale was used as outcome variables, the 10 items for each construct in the PIP were averaged to create a composite score for each of the five personality factors. These scores will be used as predictors of class membership.

The 12 Grit items were subjected to a latent class analysis. The Grit items were treated as ordinal and predicted to be conditionally independent within each class (i.e., items were uncorrelated within each class). Thus, any association between the items was assumed to be due to the latent class variable and class differences in the probability of responding in each category. This model specification follows the standard specification of the latent class model. Models with 1 through 5 classes were estimated and no covariates were included in the model when determining the number of classes (Stemann & Grimm, 2018 for discussions about the incorporation of covariates when performing class enumeration). Each model was estimated 10 times with different sets of starting values because using multiple sets of starting values helps identify the global maximum in the likelihood function, and also enables researchers to examine whether different starting values lead to the same set of parameter estimates. The latent class models were estimated using the polCA package in R.

## Results

The fit statistics and entropy for the 1- 5-class latent class models are contained in Table 10.1. The table contains the deviance, the AIC, the BIC, and the entropy. Note that the polCA package does not provide the approximate likelihood ratio tests and cannot implement k-fold cross-validation, so this information is not provided. The 1-class model contains 48 estimated parameters. The 48 estimated parameters include 4 thresholds separating the 5 response options for each of the 12 items of the Grit scale. The 1-class model provides baseline statistics that serve as the standard to improve upon adding latent classes. The 2-class model has 97 parameters, which includes 48 estimated thresholds for each class, and the intercept (threshold) for the latent class variable that separates the two classes. The 2-class model based on the information criteria was an improvement over the 1-class model. The information criteria were mixed when comparing the 3- and 4-class models. In our experience, the AIC is a better index when the sample size is fairly low, whereas the BIC is a better fit index with larger sample sizes. We, therefore, side the BIC given sample size, and however.

TABLE 10.1. Model Fit Statistics for Latent Class Models

| | Deviance | Parameters | AIC | BIC | Entropy |
|---|---|---|---|---|---|
| 1-Class Model | 17,636 | 48 | 17,732 | 17,934 | - |
| 2-Class Model | 16,525 | 97 | 16,719 | 17,128 | 0.85 |
| 3-Class Model | 16,184 | 146 | 16,476 | 17,091 | 0.87 |
| 4-Class Model | 16,925 | 195 | 16,315 | 17,137 | 0.87 |
| 5-Class Model | 15,721 | 244 | 16,209 | 17,238 | 0.86 |

TABLE 10.2. Parameter Estimates in the Probability Scale for Class 1 / 2 / Class 3

| Item | P(1) | P(2) | P(3) | P(4) | P(5) |
|---|---|---|---|---| |
| 1 | .00/.05/.01 | .05/.09/.09 | .12/.36/.46 | .30/.20/.31 | 50/.32/.13 |
| 2 | .12/.73/.18 | 22/.14/.41 | 35/.09/.30 | 21/.05/.11 | 11/.02/.01 |
| 3 | .08/.60/.12 | 11/.24/.26 | 26/.32/.25 | 45/.01/.23 | 12/.02/.01 |
| 4 | .04/.15/.08 | 12/.24/.34 | 32/.37/.32 | 34/.00/.16 | 34/.00/.16 |
| 5 | .08/.74/.16 | 13/.34/.35 | 29/.00/.28 | 32/.15/.21 | 31/.30/.05 |
| 6 | .00/.07/.02 | .00/.18/.15 | 16/.19/.28 | 32/.25/.31 | 57/.29/.19 |
| 7 | .02/.54/.03 | .06/.33/.31 | 26/.07/.38 | 49/.07/.20 | 18/.00/.02 |
| 8 | .03/.64/.13 | 11/.31/.39 | 17/.35/.49 | 43/.07/.12 | 22/.00/.08 |
| 9 | .00/.13/.01 | .02/.26/.26 | 19/.22/.27 | 37/.15/.22 | 44/.11/.02 |
| 10 | .02/.27/.01 | .06/.29/.32 | 31/.15/.45 | 23/.10/.22 | 51/.11/.08 |
| 11 | .14/.47/.02 | 21/.34/.24 | 32/.31/.45 | 31/.02/.21 | 03/.02/.08 |
| 12 | .00/.07/.02 | .12/.14/.13 | 13/.32/.45 | 28/.19/.33 | 57/.27/.08 |

In the 3-class model, approximately 50% of the sample was in class 1 with 20% in class 2 and 30% in class 3. The class-specific parameter estimates were translated to the predicted probability of responding in each response category. These probabilities are contained in Table 10.2. Given these predicted probabilities, we can begin to determine the nature of the three classes. Class 1 is the largest, this class had the highest mean response on all items, except item 11, which asked about the frequency of having an interest in new pursuits. Class 2 tended to have low mean responses to interests and projects changing from year to year. Thus, Class 2 was more easily distracted and participants' level of commitment was more average. Class 3 had participants who responded in the low categories to questions about diligence and overcoming setbacks; this class tended to have participants whose interests changed less than Class 2.
