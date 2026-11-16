| Feature | Value |
| :--- | :--- |
| More attributes | ... |
| Survived | true |

And the corresponding anchors explanation is:

```
IF SEX = female
AND Class = first
THEN PREDICT Survived = true
WITH PRECISION 97%
AND COVERAGE 15%
```

The example shows how anchors can provide essential insights into a model's prediction and its underlying reasoning. The result shows which attributes were taken into account by the model, which in this case, is the female sex and first class. Humans, being paramount for correctness, can use this rule to validate the model's behavior. The anchor additionally tells us that it applies to 15% of perturbation space's instances. In those cases the explanation is 97% accurate, meaning the displayed predicates are almost exclusively responsible for the predicted outcome.

An anchor \\A\\ is formally defined as follows:

```
\\mathbb{E}\\{_\\{D\\_x(z|A)\[1\\_{\\{f(x)=f(z)\\\}}]leqtau,A(x)=1
```

Wherein:

+   * \\x\\ represents the instance being explained (e.g., one row in a tabular data set).
+   * \\A\\ is a set of predicates, i.e., the resulting rule or anchor, such that \\A(x)=1\\ when all feature predicates defined by \\A\\ correspond to \\x\\\\'s feature values.
+   * \\f\\ denotes the classification model to be explained (e.g., an artificial neural network model). It can be queried to predict a label for \\x\\ and its perturbations.
+   * \\D\\_x (\\cdot|\\cdot|\\text{otl}A))\ indicates the distribution of neighbors of \\x\\, matching \\A\\.
+   * \\0\\text{ leq }\\tau\\text{ leq }1\\ specifies a precision threshold. Only rules that achieve a local fidelity of at least \\tau\\ are considered a valid result.

The formal description may be intimidating and can be put in words:

> Given an instance \\x\\ to be explained, a rule or an anchor \\A\\ is to be found, such that it applies to \\x\\, while the same class as for \\x\\ gets predicted for a fraction of at least \\tau\\ of \\x\\\\'s neighbors where the same \\A\\ is applicable. A rule\\'s precision results from evaluating neighbors or perturbations (following \\D\\_x (z|\\text{lot}A)) using the provided machine learning model (denoted by the indicator function \\1\\_{\\{f(x) = f(z)\\\}}).

# ## 5.8.1 Finding Anchors

Although anchors\\ mathematical description may seem clear and straightforward, constructing particular rules is infeasible. It would require evaluating \\1\\_{\\{f(x) = f(z)\}} for all \\(z \\in \\text{mathcal}\\{D\\_x(\cdot|\\text{odt}A)\) which is not possible in continuous or large input spaces. Therefore, the authors propose to introduce the parameter \\0\\text{ leq }\\delta\\text{ leq }1\\ to create a probabilistic definition. This way, samples are drawn until there is statistical confidence concerning their precision. The probabilistic definition reads as follows:

```
\\text{P}(\\text{prec}(\\text{A})\\geq\\tau)\\geq \\{ 1\\text{-delta}\\text{quad}\\text{textrm}\\{with\}\\text{quad}\\{ \\text{prec}(\\text{A})=\\mathbb{E}\\{_\\{D\\_x(z|A)\[1\\_{\\{f(x)=f(z)\}]
```

The previous two definitions are combined and extended by the notion of coverage. Its rationale consists of finding rules that apply to a preferably large part of the model\\'s input space. Coverage is formally defined as an anchors' probability of applying to its neighbors, i.e., its perturbation space: