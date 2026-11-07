
## Mixed Model in Python
We can fit a mixed model in Python using `statsmodels`. We adapt the following example from `statsmodels.org` where the growth curves of pigs are modeled. The response variable in the following is the `weight` of each pig, while the predictor is `time`. Hence, we wish to model `weight` as a function of `time`, but with the recognition that data are nested (i.e., correlated) within each pig. That is, measurements within each pig will be more similar than measurements between pigs. Thus, `pig`, which we will name “`group`” below, is a random effect:

```
import statsmodels.api as sm
import statsmodels.formula.api as smf
data = sm.datasets.get_rdataset(“dietox”, “geepack”).data
data
Out[85]:
```

|  || Pig || Evit || Cu || Litter || Start || Weight || Feed || Time |

| --- | --- | --- | --- | --- | --- | --- | --- | --- |

| 0 || 4601 || Evit000 || Cu000 || 1 || 26.5 || 26.50000 || NaN || 1 |

| --- | --- | --- | --- | --- | --- | --- | --- | --- |

| 1 || 4601 || Evit000 || Cu000 || 1 || 26.5 || 27.59999 || 5.200005 || 2 |

| 2 || 4601 || Evit000 || Cu000 || 1 || 26.5 || 36.50000 || 17.600000 || 3 |

| 3 || 4601 || Evit000 || Cu000 || 1 || 26.5 || 40.29999 || 28.500000 || 4 |

| 4 || 4601 || Evit000 || Cu000 || 1 || 26.5 || 49.09998 || 45.200001 || 5 |

| .. || ... || ... || ... || ... || ... || ... || ... || ... |

| 856 || 8442 || Evit000 || Cu175 || 24 || 25.7 || 73.19995 || 83.800003 || 8 |

| 857 || 8442 || Evit000 || Cu175 || 24 || 25.7 || 81.69995 || 99.800003 || 9 |

| 858 || 8442 || Evit000 || Cu175 || 24 || 25.7 || 90.29999 || 115.200001 || 10 |

| 859 || 8442 || Evit000 || Cu175 || 24 || 25.7 || 96.00000 || 133.200001 || 11 |

| 860 || 8442 || Evit000 || Cu175 || 24 || 25.7 || 103.50000 || 151.400002 || 12 |

```
[861 rows x 8 columns]
```

```
md = smf.mixedlm(“Weight ~ Time”, data, groups=data[“Pig”])
```

Above we have specified a model of `weight` as a function of `time`, but nested within `pig` (`groups = data["Pig"]`). We now obtain a summary of the model:

```
mdf = md.fit()
print(mdf.summary())
Mixed Linear Model Regression Results
========================================================
Model:  MixedLM Dependent Variable: Weight 
No. Observations: 861  Method:  REML 
No. Groups:  72  Scale:  11.3669
Min. group size:  11  Log-Likelihood:  -2404.7753
Max. group size:  12  Converged:  Yes
Mean group size:  12.0
--------------------------------------------------------
   Coef.  Std.Err.  z  P>|z| [0.025 0.975]
--------------------------------------------------------
Intercept  15.724  0.788  19.952  0.000 14.179  17.268
Time  6.943  0.033  207.939  0.000  6.877  7.008
Group  Var 40.394  2.149
========================================================
```

203

We see from the output that `time` is a statistically significant predictor of the `weight` of pigs (`p` < 0.001). We can also see that there is variance due to `pig` (i.e., `group`) equal to 40.394 (`Group Var = 40.394`). We also see from the output that the model was fit by `REML` (`restricted maximum likelihood`), which is usually the preferred method of estimation for a host of models.

### 4.3.4 Mixed Models in R
We now run the same mixed model on the pig data using `lmer()` in `lme4` ([Bates](#ref.xhtml#re_CIT000023) et al., 2015). The package `lme4` has extensive mixed modeling capacities and is highly recommended for all things mixed models. We also load the package `geepack` (Hojsgaard et al., [2006](#ref.xhtml#re_CIT000155)) which contains the pig data:

```
> library(lme4)
> library(geepack)
> print(summary(lmer(‘Weight ~ Time + (1|Pig)’, data=dietox)))
```

Note that the designation `(1|Pig)` communicates the nesting or hierarchical structure of the data, such that `weight` is being modeled as a function of `time`, but nested within `pig`, where `pig` is a random effect, which implies in this case that it is a level 2 variable and that we wish to model the variance of its residuals. That is, our output should return a variance due to `pig`, since the model holds that pigs were randomly sampled from a larger population of potential pigs that could have appeared in the sample.

We now view output from the model:

```
Linear mixed model fit by REML [‘lmerMod’]
Formula: Weight ~ Time + (1 | Pig)
Data: dietox
REML criterion at convergence: 4810
Scaled residuals:
  Min  1Q  Median  3Q  Max
-4.712  -0.570  -0.094  0.488  4.773
Random effects:
Groups  Name  Variance  Std.Dev.
Pig  (Intercept)  40.4  6.36
Residual  11.4  3.37
Number of obs: 861, groups: Pig, 72
Fixed effects:
  Estimate Std.  Error  t value
(Intercept)  15.7235  0.7881  19.9
Time  6.9425  0.0334  207.9
Correlation of Fixed Effects:
  (Intr)
Time -0.275
```

204

We note that the output is the same as we obtained in Python, only the `group` effect is given under its own random effects category (i.e., “`Pig`”), along with the residual variance (11.4) just below it.

The package `nlme` (Pinheiro et al., [2023](#ref.xhtml#re_CIT000289)) can also be used to fit mixed models, as well as the `VCA` package ([Schuetzenmeister and Dufey, 2024](#ref.xhtml#re_CIT000330)). R’s capacity to fit increasingly complex mixed models is virtually unlimited using these and related packages in R.

## 4.4 Multilevel Modeling
The standard linear model typically estimated by least-squares regression is appropriate for independent observations, which implies that errors will also typically be independent. That is, it is assumed that `ε[i]`, `ε[i′]` are independent for `i` ≠ `i′`. The standard linear model is usually not appropriate, or at minimum severely compromised, when this assumption is violated.

One type of dependency that naturally arises in applied settings is that of clustering, where `ε[i]`, `ε[i′]` are not independent for `i` ≠ `i′`. A classic example of where this type of clustering or dependency surfaces is in classrooms within a school, where students may share the same teacher. We say students are nested within classrooms. It would be unreasonable to expect that errors within classrooms are not related. However, this is only one potential source of nesting in the hierarchy that we may consider. Classrooms exist in schools, and schools exist in states. That is, schools within the same state, and their errors, are likely not independent of one another. As we build the nesting hierarchy from scores to groups, we develop a multilevel structure to observations, thus the name multilevel modeling. Multilevel modeling allows one to deal with the non-independence of errors that manifest at each level of the hierarchy.

### 4.4.1 A Garbled Mess of Jargon
The jargon and confusion of words and terminology that surrounds random, mixed, and multilevel modeling is nothing short of extraordinary. Historically, statistics is a discipline that has always had a difficult time having consistency in how it defines its terms because many concepts arise independently in different applied disciplines. Mixed models may arise independently in ecology, for instance, while also being developed (or “rediscovered”) in sociology as well. Slightly different names may be given to the models, which makes learning (and teaching) them very difficult for the newcomer. It’s as if in addition to learning the rather difficult method one has to become keen on how the vocabulary differs by area of specialization. This not only applies to mixed models, it applies to many statistical techniques; jargon can easily ruin your day in attempting to learn them.

It is exceptionally important however when discussing these models to be very exact and precise regarding what we are referring to. Multilevel models are often casually referred to as hierarchical linear models, random-effects models, mixed models, and other identifiers, and it can become greatly confusing for the newcomer to these models to appreciate or understand what these models are all about beyond these generalities.205
