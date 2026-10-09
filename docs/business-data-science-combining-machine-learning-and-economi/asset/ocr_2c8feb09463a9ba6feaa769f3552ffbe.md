access when predicting public health can use this information to project the societal benefits of increased access to health insurance.

The OHIE data also contain weights that can be used to map from the sample of individuals in the experiment to the future treatment population. For example, perhaps young people are harder to reach for a phone survey and they are underrepresented in the sample (in both treatment and control groups—this is a different issue than covariate imbalance). We need to worry about such differences because individual subjects do not all respond the same way to treatment. In this scenario, the *weighted* means will be more representative of the treatment effect for the average eligible Oregonian than $\overline{Y}_1 - \overline{Y}_0$. This is a basic form of the heterogeneous treatment effect modeling that is covered in later sections. Here, the adjustment makes little difference—only 2/10 of a percentage point change in estimated ATE:

```
```python
> nsel_w <- tapply(weights, $selected, sum)
> ybar_w <- tapply(weights*$pdoc_any_12m, $selected, sum)/nsel_w
> ( ATEweighted <- ybar_w['1'] - ybar_w['0'] )

1
0.05539111
```
```

This sort of reweighting, to map from the sample to the population of interest, is a standard step in many statistical analyses. For example, political pollsters are always battling to figure out how their sample of potential voters maps to the characteristics of the future voting population. An interesting contemporary overview of this area by Andrew Gelman and coauthors tackles the problem of using abundant survey through nontraditional venues—e.g., via the Microsoft Xbox gaming platform—for insight about voting intentions of the wider population. As pollsters’ recent lack of success demonstrates (e.g., Trump, Brexit), the sample-to-population mapping problem is a tricky one.

For many business settings, this is less of an issue because you are able to sample representatively from your customers. In such a setting, it is tough to find a treatment effect estimator for randomized designs that will perform better than $\overline{Y}_1 - \overline{Y}_0$. However, there are alternatives. Most prominently, *regression adjustment* is sometimes advocated as offering a reduced-variance version of the $\widehat{\mathrm{ATE}}$ from Equation 5.2. With observable covariates $x_i$ for each individual (e.g., gender, race, online activity), a regression adjustment first fits a linear model for each treatment group: