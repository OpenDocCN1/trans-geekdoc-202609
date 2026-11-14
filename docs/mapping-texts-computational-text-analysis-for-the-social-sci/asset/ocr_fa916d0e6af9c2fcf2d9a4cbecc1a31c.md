```
facet_wrap(~nonficprob,
       labeller = labeller(nonficprob = lab_nfic)) +
labs(x = "Date of First Publication",
     y = "Engaging 'Late 20c US Political Thriller'") +
scale_x_continuous(breaks = seq(1975, 1995, by = 5))
```

![](bbox=[0.07, 0.21, 0.66, 0.41])

Figure 11.1: Predicted Probabilities.

A work of fiction is more likely to be in (or at least read like) a late-20th-century US political thriller in later years.

# Topic Prevalence, Conditional on Covariates

Above we used covariates to predict topics. The topic identification itself, though, isn't conditional on these covariates. Structural topic modeling, or STM (Roberts et al. 2019), incorporates document-level covariates in topic estimation and estimates the effects of these covariates on topic prevalence and topic content.

Let's briefly discuss the basics of STM so we can see where the prevalence and content covariates come into play in the data-generation process assumed by STM.⁵

STM is a probabilistic model.⁶ It attempts to reverse-engineer the data-generating process by finding the model that maximizes the likelihood of observing the documents' word counts that we do. Following Roberts and colleagues (Roberts et al. 2016:991; Roberts et al. 2019:2–3), we randomly draw a probability distribution for each document in the corpus from a logistic normal distribution that has been conditioned on that document's “prevalence” covariates.

Then, if there is a content covariate (which we discuss next), STM decomposes the document's topic distributions over the corpus vocabulary into two matrices and an array (Roberts et al. 2016:991). The

+   THIS SECTION NEEDS:
+   * tidyverse
+   * textclean
+   * textstem
+   * stringi
+   * tidytext
+   * text2map
+   * stm
+   * stminsights
+   * marginaleffects
+   * ggtern

⁵ STM builds on CTM, and reduces to it when there are no covariates. There are excellent statistical overviews (e.g., Roberts et al. 2016, 2019).

⁶ Like the LDA model we discussed in the previous chapter, see Core Inductive.