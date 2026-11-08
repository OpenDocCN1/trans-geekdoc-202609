
$e^{- \\epsilon} \\leq \\frac{P\_{M,\\theta}{(\\left. M\\left( x \\right) = y \\middle| s\_{i},\\theta \\right.)}}{P\_{M,\\theta}{(\\left. M\\left( x \\right) = y \\middle| s\_{j},\\theta \\right.)}} \\leq e^{\\epsilon}.$<mml:math><mml:msup><mml:mrow><mml:mi>e</mml:mi></mml:mrow><mml:mrow><mml:mo>&#8722;</mml:mo><mml:mi>&#1013;</mml:mi></mml:mrow></mml:msup><mml:mo>&#8804;</mml:mo><mml:mfrac><mml:mrow><mml:msub><mml:mrow><mml:mi>P</mml:mi></mml:mrow><mml:mrow><mml:mi>M</mml:mi><mml:mo>,</mml:mo><mml:mi mathvariant="normal">&#952;</mml:mi></mml:mrow></mml:msub><mml:mrow><mml:mo stretchy="false">(</mml:mo><mml:mrow><mml:mi>M</mml:mi><mml:mrow><mml:mo stretchy="true">(</mml:mo><mml:mi>x</mml:mi><mml:mo stretchy="true">)</mml:mo></mml:mrow><mml:mo>=</mml:mo><mml:mi>y</mml:mi><mml:mo>|</mml:mo><mml:msub><mml:mrow><mml:mi>s</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:mi mathvariant="normal">&#952;</mml:mi></mml:mrow><mml:mo stretchy="false">)</mml:mo></mml:mrow></mml:mrow><mml:mrow><mml:msub><mml:mrow><mml:mi>P</mml:mi></mml:mrow><mml:mrow><mml:mi>M</mml:mi><mml:mo>,</mml:mo><mml:mi mathvariant="normal">&#952;</mml:mi></mml:mrow></mml:msub><mml:mrow><mml:mo stretchy="false">(</mml:mo><mml:mrow><mml:mi>M</mml:mi><mml:mrow><mml:mo stretchy="true">(</mml:mo><mml:mi>x</mml:mi><mml:mo stretchy="true">)</mml:mo></mml:mrow><mml:mo>=</mml:mo><mml:mi>y</mml:mi><mml:mo stretchy="true">|</mml:mo><mml:msub><mml:mrow><mml:mi>s</mml:mi></mml:mrow><mml:mrow><mml:mi>j</mml:mi></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:mi mathvariant="normal">&#952;</mml:mi></mml:mrow><mml:mo stretchy="false">)</mml:mo></mml:mrow></mml:mrow></mml:mfrac><mml:mo>&#8804;</mml:mo><mml:msup><mml:mrow><mml:mi>e</mml:mi></mml:mrow><mml:mi>&#1013;</mml:mi></mml:msup><mml:mo>.</mml:mo></mml:math> (7.17)
![Equation](images/F00008Xsi138.png)(7.17)

Here, `s[i]`, `s[j]` ∈ `A`<mml:math><mml:msub><mml:mrow><mml:mi>s</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>s</mml:mi></mml:mrow><mml:mrow><mml:mi>j</mml:mi></mml:mrow></mml:msub><mml:mo>&#8712;</mml:mo><mml:mi>A</mml:mi></mml:math>![Equation](images/F00008Xsi139.png) are vectors of all protected attributes (e.g., gender, race, nationality), and `Θ`<mml:math><mml:mi mathvariant="normal">&#920;</mml:mi></mml:math>![Equation](images/F00008Xsi140.png) is a set of distributions `θ`,<mml:math><mml:mi mathvariant="normal">&#952;</mml:mi><mml:mo>,</mml:mo></mml:math>![Equation](images/F00008Xsi141.png) which could plausibly generate each instance `x`<mml:math><mml:mi>x</mml:mi></mml:math>![Equation](images/F00008Xsi142.png). Since the definition is inspired by differential privacy, we have used differential-privacy style notation, with `M(x)`<mml:math><mml:mi>M</mml:mi><mml:mrow><mml:mfenced open="(" close=")"><mml:mrow><mml:mi>x</mml:mi></mml:mrow></mml:mfenced></mml:mrow></mml:math>![Equation](images/F00008Xsi143.png) denoting the classifier, the output of which is a predicted class label `y`<mml:math><mml:mi>y</mml:mi></mml:math>![Equation](images/F00008Xsi144.png).

To make this somewhat scary equation concrete, let’s consider the following example, illustrated in [Fig. 7.7](#Ch007_261-315_B978044315888900008X.xhtml#f0040). Suppose that given an applicant’s score on a standardized test an applicant is hired if their test score is greater than a threshold `t`. Here, `t` = 10.5<mml:math><mml:mi>t</mml:mi><mml:mo>=</mml:mo><mml:mn>10.5</mml:mn></mml:math>![Equation](images/F00008Xsi145.png).

![Fig. 7.7 Group 0 (left) has a hiring rate of ¾, while Group 1 (right) has a hiring rate of 4/4. Since 0.75 < \\ 0.8 \\times 1Equation, there is evidence of disparate impact according to the 80% rule. Credit: James Foulds](images/F00008Xf07-07-9780443158889.jpg)

[Fig. 7.7](#Ch007_261-315_B978044315888900008X.xhtml#Bf0040) Group 0 (left) has a hiring rate of ¾, while Group 1 (right) has a hiring rate of 4/4. Since 0.75< 0.8 × 1<mml:math><mml:mn>0.75</mml:mn><mml:mo>&#60;</mml:mo><mml:mspace width="0.25em"/><mml:mn>0.8</mml:mn><mml:mo>&#215;</mml:mo><mml:mn>1</mml:mn></mml:math>![Equation](images/F00008Xsi193.png), there is evidence of disparate impact according to the 80% rule. Credit: James Foulds

Each group of applicant has a different distribution over scores. Both are a normal distribution with `σ` = 1<mml:math><mml:mi mathvariant="normal">&#963;</mml:mi><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:math>![Equation](images/F00008Xsi146.png), but Group 1 has a mean of 10 while Group 2 has a mean of 12.

Using the cumulative density function of a normal distribution, we can calculate the probability of the hiring outcomes for each group ([Table 7.4](#Ch007_261-315_B978044315888900008X.xhtml#t0025)).

### Table 7.4
Differential Fairness Example: Probability of Hiring Outcome Given Group.

| Probability of Hiring Outcome Given Group  |
| --- |
|   ||   || Group 1 || Group 2 |
| Outcome `y`<mml:math><mml:mi>y</mml:mi></mml:math>![Equation](images/F00008Xsi147.png) || Yes || 0.3085 || 0.9332 |
| --- | --- | --- | --- |
| No || 0.6915 || 0.0668 |

Credit: James Foulds

Then we calculate ratios and take the log, finding the worst case over `y`, `s[i]`, and `s[j]`<mml:math><mml:msub><mml:mrow><mml:mi>s</mml:mi></mml:mrow><mml:mrow><mml:mi>j</mml:mi></mml:mrow></mml:msub></mml:math>![Equation](images/F00008Xsi148.png) to determine `ϵ`<mml:math><mml:mi mathvariant="normal">&#1013;</mml:mi></mml:math>![Equation](images/F00008Xsi149.png) ([Table 7.5](#Ch007_261-315_B978044315888900008X.xhtml#t0030)).

### Table 7.5
Differential Fairness Example: Log-ratios of Probabilities.

| Log Ratios of Probabilities  |
| --- |
