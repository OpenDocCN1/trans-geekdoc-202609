```
2 poly(firstpub, 2)1    0.111    0.0117    9.51   1.44e-20
3 poly(firstpub, 2)2    0.0490    0.0116    4.21   2.79e-   5
4 nonficprob        0.00409    0.00173    2.36   1.84e-   2
5 factor(us_national)True 0.000758 0.000898   0.844   3.99e-   1
```

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
```