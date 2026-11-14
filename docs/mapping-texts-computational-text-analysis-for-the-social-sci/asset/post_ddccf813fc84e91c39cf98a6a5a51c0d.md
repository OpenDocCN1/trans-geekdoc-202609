
## 11 Extended Inductive

INDUCTIVE analysis entails finding *latent* groupings of texts (or text units) or relations between texts (or text units) without preconceived notions about those groupings or relations. This chapter continues down this path. In the following chapters, we extend our core methods and combine them in complex ways.

We'll return to topic modeling but focus on estimating how topic *engagement* and *content* vary by other covariates. For example, how have the topics covered in *The Washington Post* changed in the last decade? We'll also extend the term similarity measures discussed in **Text to Numbers** with **word embeddings**. We'll see that embeddings are flexible tools for finding relations between words and documents and mapping semantic changes. For example, how have authors used the “network” metaphor differently over two centuries (Yung 2021)?

### INFERENCE AND TOPIC MODELS

THIS SECTION NEEDS:

- tidyverse
- broom
- marginaleffects

### Predicting Topics with Covariates

In this section, we’ll cover a few ways researchers might include covariates (or “predictors,” or “independent variables”) into their topic model analysis.

We’ve done all the work to get our topics. We’ve chosen an algorithm— LDA, or perhaps something like CTM (Blei and Lafferty 2007), or maybe the biterm topic model for short texts (Yan et al. 2013) or one that allows us to supply keywords (Eshima et al. 2020). We’ve run the model with different *k*, comparing fit statistics across solutions. We’ve interpreted the topics. Now what? We can treat these topics like any other variable.

We can see how topics may shape other factors. For instance, we might test the effects of positive tax news from US presidential communications on private consumption and investment (Dybowski and Adämmer 2018). We can also see how other factors may shape topics. For example, we can use transcripts from Federal Open Market Committee meetings to assess if speakers with private banking experience were more likely to discuss finance (Fligstein et al. 2017).

Remember topic modeling results in two probability matrices: a document-topic matrix that shows the probability of documents across topics and a topic-word matrix that shows the probability of topics across the vocabulary. We assume most covariates are at the document or author level, so we'll focus on the document-topic probabilities.

Let's explore a topic model on English-language fiction between 1880 to 1999,¹ estimated by Underwood and colleagues (2022). This study considers the extent changes in culture are explained by “period”—for example, the culture of the 1980s—versus “cohort”—for example, those born in the 1980s. Their model includes 200 topics,² and each work has covariates such as first publication date and whether that author is/was American.

The topics were estimated for chunks of each work: each volume spans multiple rows, with each row corresponding to a (roughly) 10,000-word chunk. For the sake of space, we only include a subset. Instead of a random sample of rows, we randomly sample 1,000 unique works.

The supplementary file for the study contains the labels and keywords for each of the 200 topics. We'll focus on one topic—topic #3, labeled “late-20th-century US political thrillers.” Higher probabilities for this topic indicate a work is more likely to be in the US political thriller genre.

Say we want to assess time trends for this topic. Are newer or older works in the corpus more likely to be a (or written like) late-20th-century US political thrillers? Or, maybe we want to know whether author demographics are associated with this topic? Perhaps American authors are more likely to write on this topic than authors from elsewhere. Lastly, since some works exist in the “gray area” between fiction and nonfiction (Underwood et al. 2020:7), are works in this gray area more likely to be in this topic than in others? Let's investigate these questions now.

Let's run an OLS regression with this topic as the outcome.³ The predictors are the (1) date of first publication, a (2) dichotomous variable for whether the author is/was American (“False” or “True”), and the (3) probability the work was nonfiction. The topic of interest is “V6.” For the date, we'll allow the magnitude and/or direction to be nonlinear by adding a quadratic term ( poly(firstpub, 2) ).

```
data("stm_fiction_cohort", package="text2map.pretrained")
stm_fic <- stm_fiction_cohort |>
  mutate(us_national = factor(us_national))
lm(V6 ~ poly(firstpub, 2) + nonficprob + us_national,
   data = stm_fic) |> tidy()
```

| term | estimate | std.error | statistic | p.value |
|---|---|---|---|---|
| 1 (Intercept) | 0.00174 | 0.000590 | 2.95 | 3.26e-3 |
| 2 poly(firstpub, 2)1 | 0.111 | 0.0117 | 9.51 | 1.44e-20 |
| 3 poly(firstpub, 2)2 | 0.0490 | 0.0116 | 4.21 | 2.79e-5 |
| 4 nonficprob | 0.00409 | 0.00173 | 2.36 | 1.84e-2 |
| 5 factor(us_national)True | 0.000758 | 0.000898 | 0.844 | 3.99e-1 |

Works are collected from the HathiTrust Digital Library.

The authors used MALLET (Mimno 2013), a Java program, to estimate topics.

See Math Basics.

Note all our estimates are positive. Focusing on publication date (second and third terms), we see newer works are more likely to be late-20th-century US political thrillers—and this association grows larger over time.4 The probability of being nonfiction (fourth term) is positively associated with this topic. This is intuitive since political thrillers might include nonfiction details such as depictions of real political events and places. Being an American author (fifth term) seems to have a small effect, but still positive.

4 This should be the case. We'd have a puzzle if works in the 1800s engaged this topic.

Now let’s generate predicted probabilities. We’ll get probabilities for each publication year three times: once when the nonfiction probability equals the 25th percentile, then the 50th percentile (the median), and then the 75th percentile. Let’s prepare that outcome variable below.

```
# get the IQR value for the nonficprob variable
iqr_nonfic <- c(
  quantile(stm_fic$nonficprob, .25, na.rm = TRUE),
  quantile(stm_fic$nonficprob, .5, na.rm = TRUE),
  quantile(stm_fic$nonficprob, .75, na.rm = TRUE)
)
```

```
# create labels for the plot
lab_nfic <- c(
  "Nonfiction Probability at\\n25th Percentile",
  "Nonfiction Probability at\\n50th Percentile",
  "Nonfiction Probability at\\n75th Percentile"
)
names(lab_nfic) <- iqr_nonfic
```

Let’s add an interaction effect between the publication date and the nonfiction probability (and remove the quadratic publication term for simplicity). We’ll calculate these probabilities controlling for American nationality by assuming the author is American and focus on the latter portion of the 20th century.

```
df_md <- lm(V6 ~ firstpub * nonficprob + us_national, data = stm_fic)
df_prd <- predictions(model = df_md,
                      newdata = datagrid(
                        firstpub = seq(1975, 1999, by = 1),
                        nonficprob = iqr_nonfic,
                        us_national = "True")
)
```

Now, we can plot the probabilities. They are visualized in Figure 11.1.

```
df_prd |>
ggplot(aes(x = firstpub, y = estimate)) +
geom_ribbon(aes(ymin = conf.low, ymax = conf.high), alpha = .2) +
geom_line() +
facet_wrap(~nonficprob,
       labeller = labeller(nonficprob = lab_nfic)) +
labs(x = "Date of First Publication",
     y = "Engaging 'Late 20c US Political Thriller'") +
scale_x_continuous(breaks = seq(1975, 1995, by = 5))
```

![](img/ccc0ce559da97114ef913045f55e3801_202_0.png)

Figure 11.1: Predicted Probabilities.

A work of fiction is more likely to be in (or at least read like) a late-20th-century US political thriller in later years.

### Topic Prevalence, Conditional on Covariates

Above we used covariates to predict topics. The topic identification itself, though, isn't conditional on these covariates. Structural topic modeling, or STM (Roberts et al. 2019), incorporates document-level covariates in topic estimation and estimates the effects of these covariates on topic prevalence and topic content.

Let's briefly discuss the basics of STM so we can see where the prevalence and content covariates come into play in the data-generation process assumed by STM.⁵

STM is a probabilistic model.⁶ It attempts to reverse-engineer the data-generating process by finding the model that maximizes the likelihood of observing the documents' word counts that we do. Following Roberts and colleagues (Roberts et al. 2016:991; Roberts et al. 2019:2–3), we randomly draw a probability distribution for each document in the corpus from a logistic normal distribution that has been conditioned on that document's “prevalence” covariates.

Then, if there is a content covariate (which we discuss next), STM decomposes the document's topic distributions over the corpus vocabulary into two matrices and an array (Roberts et al. 2016:991). The

THIS SECTION NEEDS:

- tidyverse
- textclean
- textstem
- stringi
- tidytext
- text2map
- stm
- stminsights
- marginaleffects
- ggtern

⁵ STM builds on CTM, and reduces to it when there are no covariates. There are excellent statistical overviews (e.g., Roberts et al. 2016, 2019).

⁶ Like the LDA model we discussed in the previous chapter, see Core Inductive.
