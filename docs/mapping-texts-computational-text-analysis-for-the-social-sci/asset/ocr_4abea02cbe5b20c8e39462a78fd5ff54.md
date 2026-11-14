```
bigrams <- bigrams |>
  tolower() |>
  str_replace(pattern = " ",
              replacement = "_")
```

Again, let's use the %in% operator to create a logical index of which columns are "in" our dictionary. We'll add a new populist variable to our dataframe.

```
matched <- colnames(dtm_bin) %in% bigrams
dtm_sub <- dtm_bin[, matched]
df_pres$populist_bigram <- ifelse(rowSums(dtm_sub) > 0, 1, 0)
```

Find the proportion per year by political party. To do so, we tell R to group by both variables year and party, and then summarize our variables in the same way we did with the unigram dictionary.

```
df_plot <- df_pres |>
  group_by(year, party) |>
  summarize(total = n()),
         populist = sum(populist bigram),
         percent = populist / total)
```

Like before, we are mapping the percentage of populist speeches to the height of the bars, but we also map the color of the bars ( fill ) to the political party of the speakers (Figure 9.2).

```
df_plot |>
  ggplot(aes(x = year, y = percent, fill = party)) +
  geom_col(position = "dodge") +
  scale_y_continuous() +
  labs(title = "Populist Speeches by Party",
       y = "% Populist Speeches",
       x = NULL)
```

![](bbox=[0.1, 0.61, 0.9, 0.82])

Figure 9.2: Populist Speeches with Bigram Dictionary.