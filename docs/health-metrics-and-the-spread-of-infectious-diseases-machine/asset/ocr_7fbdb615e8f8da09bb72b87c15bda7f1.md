# Example: Rabies

```
p2 <- rabies %%
# apply a scale transformation to the numeric variables
mutate(year = as.integer(year),
across(where(is.double, scale)) = %%
gpgplot(aes(x = year, group = location, linetype = ) +
geom_line(aes(y = dx_rabies),
  linewidth = 1) +
geom_line(aes(y = dalys_rabies))
```

![](bbox=[0.116, 0.246, 0.883, 0.432])

+   (a) Not scaled

+   (b) Scaled and centred

**Figure 7.1** Not Scaled and Centred

Creating new features from existing ones provide additional predictive power. Then, combine the cause vector in one way to obtain two for death rates due to rabies and all causes, scale and centre the numeric variables to obtain homogeneous data to use in the model.

```
all_causes <- hmsidwr::rabies %%
filter(year >= 1990 & year <= 2018) %%
select(-upper, -lower) %%
pivot_wider(names_from = measure, values_from = val) %%
filter(!cause == "Rabies") %%
renamename(dx_allcauses = Deaths, dalys_allcauses = DALYS) %%
select(-cause))
```

```
dat <- rabies %%
full_join(all_causes, by = c("location", "year"))
```

```
dat %%
head()
# A tibble: 6 x 6
# location year dx_rabies dalys_rabies dx_allcauses dalys_allcauses
# <chr>    dbl     dbl         dbl         dbl             dbl
# 1 Asia 1990 0.599 33.1 1179 50897
# 2 Asia 1992 0.575 31.9 1151 49532
# 3 Asia 1994 0.554 30.7 1120 40804
# 4 Asia 1991 0.585 32.3 1166 50412
# 5 Asia 1995 0.551 30.5 1116 47766
# 6 Asia 1997 0.502 27.9 1072 46164.
```