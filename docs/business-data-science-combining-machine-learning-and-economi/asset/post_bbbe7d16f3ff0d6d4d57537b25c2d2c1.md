
entire set of candidate models will be completely different. This instability is the enemy of reliable model selection; fortunately, we can stabilize the algorithms by introducing the concept of penalization.

The key to modern statistics is regularization. This is the strategy of penalizing complexity so as to depart from optimality and stabilize a system. Recall that, for most classical statistics procedures, you are minimizing a deviance $d(\boldsymbol{\beta})$ (equivalently, maximizing a likelihood): $\hat{\boldsymbol{\beta}} = \underset{\boldsymbol{\beta}}{\mathrm{argmin}} \{ -\frac{2}{n} \log \mathrm{lh} (\boldsymbol{\beta}) \}$. A regularization strategy will instead involve minimizing a penalized deviance:

$$
\hat{\boldsymbol{\beta}} = \underset{\boldsymbol{\beta}}{\mathrm{argmin}} \left\{ -\frac{2}{n} \log \mathrm{lh} (\boldsymbol{\beta}) + \lambda \sum_k c(\beta_k) \right\}. \tag{3.3}
$$

Here, $c(\boldsymbol{\beta})$ is a cost on the size of the coefficient. In the case where $c(\boldsymbol{\beta}) = | \beta |$—the absolute value cost—we get the common and useful lasso estimator. It will play a major role in your data science life.

Let’s unpack Equation 3.3. We’ve simply added a penalty—the $\lambda \Sigma_k c(\beta_k)$ term—to the MLE deviance minimization of Equation 2.18. This penalty puts a cost on the size of each $\hat{\beta}_k$. That penalizes complexity, because the $\beta_k$ coefficients are what allow your predicted $\hat{y}$ values to move around with different input $x$ values. If you force them to all be close to zero, your $\hat{y}$ values will be shrunk toward $y-$, and the entire system moves around less—it is stable.

Another way to think about Equation 3.3 is through the lens of decision theory—a framework built around the idea that choices have costs. If you consider the decision-making process in classical statistics—focused on a two-stage process of estimation and hypothesis testing—what are the costs?

- **Estimation cost:** Deviance! This is the cost of distance between data and the model, and it is what you minimize to obtain the MLE.
- **Testing cost:** There is a fixed price placed on $\hat{\beta} \neq 0$. This is implicit in the hypothesis testing procedure, where you set $\hat{\beta}=0$ unless you have significant evidence otherwise. That is, the null is safe, and you need to pay to decide otherwise.

Thus, in classical statistics, the cost of $\hat{\beta}$ is the in-sample deviance plus a penalty for being away from zero. However, the cost of moving away from zero—the cost of instability—is hidden inside the hypothesis-testing scenario. Equation 3.3 makes both costs explicit.

What should the penalty function look like? First, $\lambda > 0$ is the penalty weight. It is a tuning parameter that needs to be selected in some data-dependent matter, and the final section of this chapter is focused on how to do this. For now let's consider it fixed. The rest of the penalty is determined by the shape of the cost function. In all cases, $c(\beta)$ will be lowest at $\beta = 0$, and you pay more for $|\beta| > 0$. This structure is implied by our preference for stability. Otherwise, the variety of options is wide; Figure 3.4 shows a few.

![Figure 3.4](img/315929ad4bddd26368466d02e06e2385_119_0.png)

> **FIGURE 3.4:** Common penalty functions: ridge $\beta^2$, lasso $|\beta|$, elastic net $\alpha\beta^2 + |\beta|$, and a “nonconvex” penalty $\log(1 + |\beta|)$.

Each of these encourages different sorts of model behavior. The ridge penalty, $\beta^2$, places little penalty on small values of $\beta$ but a rapidly increasing penalty on large values. This will be appropriate for scenarios where you believe each covariate has a small effect, with no big coefficients dominating the model. The lasso's absolute value penalty, $|\beta|$, places a constant penalty on deviations from zero. Moving $\beta$ from 1 to 2 costs the same as a move from 101 to 102. And the “elastic net” is an elaborate name for the simple combination of ridge and lasso.

Penalties like the log penalty on the far right are special because they have *diminishing bias*: they place extreme cost on the move from zero to small values of $\beta$, but for large values the rate of penalty change is small. These penalties encourage lots of zeros in your fit while allowing large signals to be estimated without any bias. Such nonconvex penalties are favored by theoretical statisticians, but they need to be treated with care in practice because they introduce many of the instability and computational issues that we observe with stepwise regression. Indeed, you can interpret stepwise regression as solving for a penalized deviance under $L0$ costs, where $c(\beta) = \mathbb{1}_{[\beta \neq 0]}$. The problems of subset selection—needing to refit a completely different model every time you add a variable— are extreme versions of the problems associated with any nonconvex penalty scheme.

An advantage of the lasso is that it gives the least possible amount of bias on large signals while still retaining the stability of a convex penalty like the ridge. Another massive advantage of the lasso, and of all the three right “spiky” penalties in Equation 3.2, is that it will yield automatic variable screening. That is, some of the solved $\hat{\beta}_{k}$ values will be exactly equal to zero —not close to zero, but zero as in “they are not in the model, so you don’t need to store or think about them.” The reason that this happens is illustrated in Figure 3.5: the deviance is smooth while the absolute value function is pointy, and the minimum of their sum can be at zero if the penalty dominates. Any penalty that involves a $|\beta|$ term will do this—for example, all but ridge in Figure 3.4.

![Figure 3.5](img/315929ad4bddd26368466d02e06e2385_120_0.png)

> **FIGURE 3.5:** Illustration of penalized deviance minimization leading to $\hat{\beta} = 0$.

In summary, there are *many* penalty options. As you will see, the lasso is a fantastic default. You can think of it as a baseline and consider others only if you have a strong reason to do so.

THE LASSO ALONE CANNOT DO MODEL SELECTION. Rather, it provides a mechanism to *enumerate* a number of candidate models to choose among. A lasso regularization path minimizes, for a *sequence* of penalties $\lambda_{1} > \lambda_{2} \ldots > \lambda_{T}$, the penalized log likelihood:

$$
-\frac{2}{n} \log \mathrm{lh}(\boldsymbol{\beta}) + \lambda \sum_{j} |\beta_{j}| \tag{3.4}
$$

This provides a sequence of estimated regression models, with coefficients $\hat{\beta}_1$ . . . $\hat{\beta}_T$. Given this sequence, model selection tools are used to choose best $\hat{\lambda}$. For example, you can do an out-of-sample experiment to compare performance across the different penalties.

### **ALGORITHM 6 Lasso Regularization Path**

Begin with $\lambda_1 = \min \{ \lambda : \hat{\beta}_{\lambda} = 0 \}$.  
For $t = 1$ . . . $T$:

- Set $\lambda_t = \delta\ \lambda_{t-1}$ for $\delta \in (0, 1)$.
- Find $\hat{\beta}_t$ to optimize Equation 3.4 under penalty $\lambda_t$.

Algorithm 6 outlines this simple recipe. You start with $\lambda_1$ just big enough that $\hat{\beta}_1 = 0$. This is always possible, via the formula

$$
\lambda_1 = \max_{k=1} \left\{ \frac{\left[ \partial \left[ -\frac{2}{n} \log \text{lh}(\beta) \right] \right]^p}{\partial \hat{\beta}_k} \right\}.
$$

Most software will find this starting point automatically. You then iteratively shrink $\lambda$ while updating $\hat{\beta}_{\lambda}$, where $\hat{\beta}_{\lambda}$ denotes the solution to Equation 3.4 under penalty weight $\lambda$. A crucial detail here is that the coefficient updates are smooth in $\lambda$; that is,

$$
\hat{\beta}_t \approx \hat{\beta}_{t-1} \text{ for } \lambda_t \approx \lambda_{t-1}.
$$

This leads to both *speed* and *stability* for the lasso algorithm. The speed comes from the fact that each update $\hat{\beta}_{t-1} \rightarrow \hat{\beta}_t$ is small and hence fast. Stability is the mirror image of this property: even if the selected $\lambda$ changes across data samples, it will remain in a local neighborhood, and the selected $\hat{\beta}$ will thus also stay in a small neighborhood. Unlike for subset selection, jitter to your data does not lead to big changes in the $\hat{y}$ prediction rules.

The whole enterprise is easiest to understand visually. For illustration, we introduce the *browsed* dataset containing web browsing logs for 10,000 people. We’ve extracted a year’s worth of browser logs for the 1000 most heavily trafficked websites. Each browser in the sample spent at least \$1 online in the same year. As an example regression, we can treat total online spending as the response of interest and regress this onto the percent of time
