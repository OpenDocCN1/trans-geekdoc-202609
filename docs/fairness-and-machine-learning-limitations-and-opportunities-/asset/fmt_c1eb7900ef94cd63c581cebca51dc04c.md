
In the language of our formal framework, mediation analysis aims to decompose a total causal effect into path-specific components. We will illustrate the concepts in the basic three-variable case of a mediator, although the ideas extend to more complicated structures.

There are two different paths from *X* to *Y*. A direct path and a path through the mediator *Z* ([figure 5.11](#chapter_5.xhtml#fig5-11)). The conditional expectation 𝔼\[*Y| X* = *x*\] lumps together influence from both paths. If there were another confounding variable in our graph influencing both *X* and *Y*, then the conditional expectation would also include whatever correlation is the result of confounding. We can eliminate the confounding path by virtue of the do-operator 𝔼\[*Y|* do(*X* := *x*)\]. This gives us the total effect of the action *X* := *x* on *Y*. But the total effect still conflates the two causal pathways, the direct effect and the indirect effect. We will now see how we can identify the direct and indirect effects separately.

![Figure 5.11Causal graph with mediator Z.](images/fig5-11.png)

[Figure 5.11](#chapter_5.xhtml#fig5_11)Causal graph with mediator *Z*.

We dealt earlier with the direct effect as it did not require any counterfactuals. Recall, we can hold the mediator fixed at level *Z* := *z* and consider the effect of treatment *X* := 1 compared with no treatment *X* := 0 as follows:

![](images/pg138-1.png)

We can rewrite this expression in terms of counterfactuals equivalently as:

![](images/pg139-1.png)

To be clear, the expectation is taken over the background variables in our structural causal models. In other words, the counterfactuals inside the expectation are invoked with an elementary setting *u* of the background variables, that is, *Y*[*X*:=1*,Z*:=*z*](*u*) − *Y* [*X*:=0*,Z*:=*x*](*u*), and the expectation averages over all possible settings.

The formula for the direct effect above is usually called *controlled direct effect*, since it requires setting the mediating variable to a specified level. Sometimes it is desirable to allow the mediating variable to vary as it would had no treatment occurred. This too is possible with counterfactuals and it leads to a notion called *natural direct effect*, defined as

![](images/pg139-2.png)

The counterfactual *Y*[*X*:=1*,Z*:=*Z*[*X*:=0]] is the value that *Y* would obtain had *X* been set to 1 and had *Z* been set to the value *Z* would have assumed had *X* been set to 0.

The advantage of this slightly mind-bending construction is that it gives us an analogous notion of *natural indirect effect*:

![](images/pg139-3.png)

Here we hold the treatment variable constant at level *X* := 0, but let the mediator variable change to the value it would have attained had treatment *X* := 1 occurred.

In our three-node example, the effect of *X* on *Y* is unconfounded. In the absence of confounding, the natural indirect effect corresponds to the following statement of conditional probability (involving neither counterfactuals nor do-interventions):

![](images/pg139-4.png)

In this case, we can estimate the natural direct and indirect effect from observational data.

The technical possibilities go beyond the case discussed here. In principle, counterfactuals allow us to compute all sorts of path-specific effects even in the presence of (observed) confounders. We can also design decision rules that eliminate path-specific effects we deem undesirable.

### Counterfactual Discrimination Criteria

Beyond their application to path analysis, counterfactuals can also be used as a tool to put forward normative fairness criteria. Consider the typical setup of chapter 3. We have features *X*, a sensitive attribute *A*, an outcome variable *Y*, and a predictor *Ŷ*.

One criterion that is technically natural would say the following: For every possible demographic described by the event *E* := {*X* := *x, A* := *a*} and every possible setting *a*′ of *A*, we ask that the counterfactual *Ŷ*[*A*:=*a*](*E*) and the counterfactual *Ŷ*[*A*:=*a*′](*E*) follow the same distribution.

Introduced as *counterfactual fairness* \[[187](#references.xhtml#ref-187)\], we refer to this condition as *counterfactual demographic parity*, since it’s closely related to the observational criterion *conditional demographic parity*. Recall, conditional demographic parity requires that in each demographic defined by a feature setting *X* = *x*, the sensitive attribute is independent of the predictor. Formally, we have the conditional independence relation *Ŷ* ⊥ *A | X*. In the case of a binary predictor, this condition is equivalent to requiring for all feature settings *x* and groups *a, a*′:

![](images/pg140-1.png)

The easiest way to satisfy counterfactual demographic parity is for the predictor *Ŷ* to use only nondescendants of *A* in the causal graph. This is analogous to the statistical condition of using only features that are independent of *A*.

In the same way that we defined a counterfactual analogue of demographic parity, we can explore causal analogues of other statistical criteria in chapter 3. In doing so, we need to be careful to separate technical questions about the difference between observational and causal criteria from the normative content of the criterion. Just because a causal variant of a criterion might get around some statistical issues of noncausal correlations does not mean that the causal criterion resolves normative concerns or questions with its observational cousin.

### Counterfactuals in the Law

We’ll now scratch the surface of a deep subject in legal scholarship that we return to in chapter 6 after developing greater familiarity with the legal background. The subject is the relationship of causal counterfactual claims and legal cases of discrimination. Many technical scholars see support for a counterfactual interpretation of United States discrimination law in various rulings by judges that seem to have invoked counterfactual language. Here’s a quote from a popular textbook on causal inference \[[188](#references.xhtml#ref-188)\]:

U.S. courts have issued clear directives as to what constitutes employment discrimination. According to law makers, “The central question in any employment-discrimination case is whether the employer would have taken the same action had the employee been of a different race (age, sex, religion, national origin etc.) and everything else had been the same.” (In Carson vs Bethlehem Steel Corp., 70 FEP Cases 921, 7th Cir. (1996).)

Unfortunately, the situation is not so simple. This quotation invoked here—and in several other technical papers on the topic—expresses the opinion of judges in the 7th Circuit Court at the time. This court is one of thirteen United States courts of appeals. The case has little precedential value; the quotation cannot be considered a definitive statement on what employment discrimination means under either Title VII or Equal Protection law.

More significant in US jurisprudence is the standard of “but-for causation” that has gained support through a 2020 US Supreme Court decision relating to sex discrimination in the case *Bostock v. Clayton County*. In reference to the Title VII statute about employment discrimination in the Civil Rights Act of 1964, the court argued:

While the statute’s text does not expressly discuss causation, it is suggestive. The guarantee that each person is entitled to the “same right … as is enjoyed by White citizens” directs our attention to the counterfactual—what would have happened if the plaintiff had been White? This focus fits naturally with the ordinary rule that a plaintiff must prove but-for causation. (*Comcast Corp. v. NAT. ASSN. AFRICAN AMERICAN-OWNED*, 140 S. Ct. 1009, 589 U.S., 206 L. Ed. 2d 356 \[2020\])
