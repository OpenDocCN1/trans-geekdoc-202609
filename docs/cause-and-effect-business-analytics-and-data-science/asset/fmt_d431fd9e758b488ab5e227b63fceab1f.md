
The results are summarized in [Figure 9.8](#chapter9.xhtml#fig9_8) and [Table 9.7](#chapter9.xhtml#tbl9_7). Lift in sales is defined as Average Sales in Treatment minus Average Sales in Control. As Eqn. (8.11b) or (8.12b) indicates, the model system includes a combination of response probability models and sales models (conditional on response) Page 276to estimate the overall sales. Similar to other uplift modeling examples, the baseline model is the estimated probability from the treatment-only response model multiplied by the exponential of the log(sales) model using all treatment responders.

![Figure 9.8 Lift chart for various models. ⏎](images/fig9_8.jpg)

Figure 9.8 Lift chart for various models. [⏎](#chapter9.xhtml#b9fig9_8)

Table 9.8 Performance Metrics of Various Log(Sales) Models [⏎](#chapter9.xhtml#b9tbl9_8)

|  || Gini || Gini 15% || Gini Repeatability (R²) (%) |
| --- | --- | --- | --- |
| Baseline (Treatment Only) || 1.3274 || 0.1395 || 89.9 |
| --- | --- | --- | --- |
| Direct Response Model || 1.8164 || 0.1583 || 94.8 |
| Uplift Model || 1.2829 || 0.1215 || 93.5 |
| Integrated Model || 1.9491 || 0.1741 || 96.0 |

## 9.6 Concluding Remarks and Opportunities for Improvement

This chapter introduced a more recently developed uplift modeling technique, the `KLZ`, in [Section 9.2](#chapter9.xhtml#sec9_2), which has been empirically shown to be very useful, at least in limited data sets. [Sections 9.3](#chapter9.xhtml#sec9_3) and [9.4](#chapter9.xhtml#sec9_4) discuss a more general situation when randomized experiments are not available, and Page 277methodologies for uplift modeling on observational data, utilizing a combination of PS matching

Even though this chapter concludes the uplift modeling methodologies, there are many opportunities to further improve the techniques introduced in this chapter and [Chapter 6](#chapter6.xhtml):

1. **Advanced Statistical and Machine Learning Methods for Supervised Learning:** Although uplift modeling is a little different from regular supervised learning as it aims at modeling the difference between treatment and control response rates, it can still benefit from advanced techniques developed for *regular* supervised learning. For example, lasso and elastic net can possibly improve variable selection in the `KLZ` ([Section 9.2](#chapter9.xhtml#sec9_2)), Modified `KLZ` ([Section 9.4.2](#chapter9.xhtml#sec9_4_2)), or the Two Model Approach and the Treatment Dummy Method ([Sections 6.5](#chapter6.xhtml#sec6_5)), whether we are working with experimental data ([Chapter 6](#chapter6.xhtml) and [Section 8.2](#chapter8.xhtml#sec8_2)) or observational data ([Sections 9.3](#chapter9.xhtml#sec9_3) and [9.4](#chapter9.xhtml#sec9_4)). Likewise, these methods (Two Model Approach, Treatment Dummy, or `KLZ`) could possibly be improved with advanced techniques that can better capture nonlinear relationships and interaction effects such as random forests (e.g., [Guelman et al. 2014](#chapter9.xhtml#ref9_15)), boosted tree (`MART`), and neural network (see, e.g., [Hastie et al. 2013](#chapter9.xhtml#ref9_16)). Similarly, for uplift modeling on observational data, the PS model ([Section 9.4](#chapter9.xhtml#sec9_4)) has a binary dependent variable (treatment or control) that is commonly handled by logistic regression but could be improved with more advanced modeling techniques for detecting and capturing nonlinearities and interaction effects ([Westreich et al. 2010](#chapter9.xhtml#ref9_42)).

2. **Model Ensemble:** Similar to applying more advanced modeling techniques, the performance of all the methods described in this chapter could be empirically improved with model ensemble methods by averaging out available models. A commonly used method for improving any supervised learning is Bootstrap Aggregate or Bagging, using bootstrapping and averaging to arrive at a lower expected mean squared error (through lower variability with mostly unchanged bias; see, for example, [Hastie et al. 2013](#chapter9.xhtml#ref9_16)). Other model ensemble methods for uplift modeling have also been considered in the literature, for example, by [Grimmer et al. (2016)](#chapter9.xhtml#ref9_13).

3. There are software tools available for uplifting modeling which include a variety of techniques for comparison analysis, as summarized in [Table 9.9](#chapter9.xhtml#tbl9_9). Some software are applicable to experimental (`RCT`) data only, and others can be employed for both experimental Page 278or observational data, where propensity score matching (`PSM`)-inversely proportional weighting (`IPW`) is often applied to the latter. In particular, `grf` (generalized random forest) in `R` provides a random forest equivalent for uplift modeling and may be favored by academic researchers for publications given the strong theoretical support (see [Athey et al. 2019](#chapter9.xhtml#ref9_3); [Tibshirani et al. 2023](#chapter9.xhtml#ref9_39)). In commercial applications, `CausalML` developed by Uber and `EconML` developed by Microsoft Research (both in `Python`) appear to be attractive choices by business practitioners, especially given its coverage of techniques including tree-based methods such as random forest version for uplift as well as various “meta-learners” briefly described as follows (see [Kunzel et al. 2019](#chapter9.xhtml#ref9_22); CausalML 2023; EconML 2023; [Facure 2023](#chapter9.xhtml#ref9_11); [Molak 2023](#chapter9.xhtml#ref9_28), for further description):

Table 9.9 Summary of Available Software for Uplift Modeling [⏎](#chapter9.xhtml#b9tbl9_9)

| Open Source or Commercial || Uplift on RCT Data || Uplift on RCT or Observational Data |
| --- | --- | --- |
| **Open Source: R** || 
* Uplift (Gruelman 2015) – tree, `RF`
* Tools4uplift (2019) – two-model, interaction
* quint (2020) – tree, based on effect size
* mr_uplift (2020) – multiple treatments, neural net
 || 
* `grf` ([Athey et al. 2019](#chapter9.xhtml#ref9_3); [Tibshirani et al. 2023](#chapter9.xhtml#ref9_39)) – transformed outcome, tree, `RF`, `PSM-IPW`
* rlearner (2020) – meta learner, `PSM-IPW`
 |
| --- | --- | --- |
| **Open Source: Python** || 
* Pylift (Wayfair 2019) – transformed outcome
* scikit uplift (2022) – single model, two-model, transformed outcome
 || 
* CausalLift (2019) – two-model, `PSM-IPW`
* `CausalML` (Uber 2025) – tree, `RF`, meta learners, `PSM-IPW`
* `EconML` (Microsoft 2025) – `RF`, meta learners, `PSM-IPW`
 |
| **Commercial Software** || 
* JMP Pro: Uplift Model – tree
* SAS Enterprise Miner: Incremental Response Model – two-model, interaction
 ||  |

1. `S-learner`: A single (S) model capturing treatment effect as a dummy variable using machine learning, essentially the same as the Treatment Dummy variable approach in [Lo (2002)](#chapter9.xhtml#ref9_25) with flexibility on the choice of predictive modeling techniques.

2. `T-learner`: Developing two (T) separate models for treatment and control groups, respectively, which is the same as the Two Model approach previously discussed (e.g., [Lo and Pachamanova 2015](#chapter9.xhtml#ref9_26)), and machine learning techniques can be used.

3. `X-learner`: Similar to `T-learner`, X (Cross) learner estimates two separate machine learning models for treatment and control Page 279groups and uses them to predict the “counterfactual” estimates (i.e., estimated control response rates for the treatment group and estimated treatment response rates for the control group). Next, this approach proceeds to take the difference between the actual response and its counterfactual (estimated) rate for each individual and then estimate two separate models using the difference as the outcome variable for the treatment and control groups, respectively. Finally, the two estimates are combined in a weighted average for the `X-learner` model score.
