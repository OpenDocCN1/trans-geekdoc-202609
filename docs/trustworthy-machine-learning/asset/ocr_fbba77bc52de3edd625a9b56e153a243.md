![](bbox=[0.104, 0.092, 0.89, 0.218])

**Figure 6.1. Organization of the book.** This third part focuses on the first attribute of trustworthiness, *competence and credibility*, which maps to machine learning models that are well-performing and accurate. Accessible caption. A flow diagram from left to right with six boxes: part 1: introduction and preliminaries; part 2: data; part 3: basic modeling; part 4: reliability; part 5: interaction; part 6: purpose. Part 3 is highlighted. Parts 3–4 are labeled as attributes of safety. Parts 3–6 are labeled as attributes of trustworthiness.

Specifically, this chapter focuses on:

+   - selecting metrics to quantify the basic performance of your decision function (including ones that summarize performance across operating conditions),
+   - testing whether your decision function is as good as it could ever be, and
+   - differentiating performance in risk assessment problems from performance in binary decision problems.

# ### 6.1 Selecting Decision Function Metrics

You, the ThriveGuild data scientist, are faced with the *binary detection* problem, also known as the *binary hypothesis testing* problem, of predicting which loan applicants will default, and thereby which applications to deny.² Let *Y* be the loan approval decision with label *y* = 0 corresponding to deny and label *y* = 1 corresponding to approve. Feature vector *X* contains employment status, income, and other attributes. The value *y* = 0 is called a *negative outcome* and the value *y* = 1 is called a *positive*. The random variables for the features and label are governed by the pmfs given the special name *likelihood functions* pₓ|ᵧ(*x* | *y* = 0) and pₓ|ᵧ(*x* | *y* = 1), as well as by prior probabilities p₀ = P(*Y* = 0) and p₁ = P(*Y* = 1) = 1 − p₀. The basic task is to find a *decision function* γ: 𝒳 → {0,1} that predicts a label from the features.³

# #### 6.1.1 Quantifying the Possible Events

There are four possible events in the binary detection problem:

+   1. the decision function predicts 0 and the true label is 0,
+   2. the decision function predicts 0 and the true label is 1,