selected variable, which is 1 for the approximately 50% of people who were randomly selected in the lottery to be able to apply for Medicaid.

```
> table(P$selected)
0 1
11629 11478
```

The additional medicaid variable is 1 if these selected people then actually enrolled for Medicaid. Not all those who were selected ended up actually enrolled; they might not have bothered applying, or they could have been found ineligible for a variety of reasons (e.g., if their income was higher than the state expected). Later in this chapter we introduce the concept of *instrumental variables* and use this to measure the direct effect of medicaid. The other variables shown here are household id—some people in the study shared a household—and numhh, the number of people from each household that applied for Medicaid.

The standard ATE estimate is available via two lines of R code:

```
> ybar <- tapply(P$doc_any_12m, P$selected, mean)
> ( ATE <- ybar['1'] - ybar['0'] )
1
0.05746606
```

We've estimated that being selected in the Medicaid application lottery leads to a 6 percentage point increase in the probability that you visit a PCP in the following year (y is binary so its expectation is a probability). This is statistically significant: we have 90% confidence of a 4.5- to 7-point increase in PCP visit rates due to lottery selection.

```
> nsel <- table(P[,c("selected")])
> yvar <- tapply(P$doc_any_12m, P$selected, var)
> ( seATE <- sqrt(sum(yvar/nsel)) )
[1] 0.006428387
> ATE + c(-2,2)*seATE
[1] 0.04460929    0.07032284
```

Oregon can plan for this range of increased PCP usage when it expands Medicaid eligibility to a wider population, and models that condition on PCP