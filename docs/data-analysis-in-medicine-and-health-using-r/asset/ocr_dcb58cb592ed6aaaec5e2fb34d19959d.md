```
ggplot(data = pep, aes(x = age, fill = gender)) + 
  geom_histogram(binwidth = 5, aes(y = .density..),
                                 position = "identity", alpha = 0.45) +
  geom_density(aes(linetype = gender), alpha = 0.65) +
  scale_fill_grey() + 
  xlab("Age") +
  ylab("Density") + 
  labs(title = "Density distribution of age for outcome and gender",
       caption = "Source : Peptic ulcer disease data") + 
  theme_bw() + 
  facet_wrap(~ outcome)
```

![](bbox=[0.198, 0.345, 0.802, 0.618])

We can provide the summary statistics to complement the plots or vice versa.

```
pep%%%

group_by(outcome, gender) %%%
  summarize(mean_age = mean(age, na.rm = TRUE),
            sd_age = sd(age, na.rm = TRUE))
```

```
## `summarise()` has grouped output by 'outcome'. You can override this with
## `.groups` argument.

## # A tibble: 4 x 4
## # Groups: outcome [2]
## ## outcome gender mean_age sd_age
## ## <chr> <chr> <dbl> <dbl>
```