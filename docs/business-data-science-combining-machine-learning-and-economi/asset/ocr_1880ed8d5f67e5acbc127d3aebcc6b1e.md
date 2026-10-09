We can also compare the topic regression to a lasso where the overall rating is regressed onto raw token counts. **Figure 8.7** shows results of OOS validation for each approach, and we see that the topic regression outperforms the token regression. There is a useful low-dimensional factor structure in the review text, and this factor structure is directly relevant to the response of interest: overall quality. In this case, we gain estimation efficiency by doing unsupervised dimension reduction before running the lasso.

![](bbox=[0.18, 0.26, 0.88, 0.58])

FIGURE 8.7: Comparison of topic regression and a lasso onto the raw token counts $x_{ij}.$

# MULTINOMIAL INVERSE REGRESSION (MNIR)

Between text regression and topic modeling, you are now equipped to use text to predict some $y$ or to build models for latent unobserved factors in text. Another task that comes up often in social science is understanding how text connects to a *set* of related covariates. For example, you might want to connect the we8there reviews simultaneously to all five aspect ratings, allowing you to determine which content is predictive of ratings on, say, atmosphere *separate* from food or service.