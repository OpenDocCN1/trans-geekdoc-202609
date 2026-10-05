
## 9.2 Music popularity activity

popularity rates of 3.4% still occur by chance, even in a hypothetical world where no difference in popularity existed between the two genres. In other words, what is the role of sampling variation in this hypothesized world? To answer this question, we will again rely on a computer to run simulations.

### 9.2.2 Shuffling once

First, to imagine a hypothetical universe where there was no difference in the popularity of metal and deep house. In such a hypothetical universe, the genre of a song would have no bearing on their chances of popularity. Bringing back to our spotify_metal_deephouse data frame, the popular_or_not variable would be an irrelevant label. If these popular_or_not labels were irrelevant, we could randomly reassign them by "shuffling" to no consequence!

To illustrate this idea, let's narrow our focus to 52 songs of the 2000 that you saw earlier. The track_genre column shows what the original genre of the song was. Note that to keep this smaller dataset of 52 rows to be a representative sample of the 2000 rows, we have sampled such that the popularity rate for each metal and deep-house is close to the original rates of 0.563 and 0.529, respectively, prior to shuffling. This data is available in the spotify_52_original data frame in the moderndive package. We also remove the track_id column for simplicity. It is an identification variable that is not relevant for our analysis.

```
spotify_52_original |
select(track_id) |
head(10)
```

TABLE 9.3: Representative sample of metal and deep-house songs

| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | Jess Bays;Poppy Bascomb | Temptation (feat. Poppy Bascomb) | 63 | popular |
| metal | Whitesnake | Here I Call Again - 2018 Remaster | 69 | popular |
| metal | Blind Melon | No Rain | 1 | not popular |
| metal | Amended Sevenfold | Shepherd of Fire | 70 | popular |
| deep-house | Nora Van Elken | I Wanna Dance With Somebody (Who Loves Me) - | 56 | popular |
| metal | Breaking Benjamin | Ashes of Eden | 61 | popular |
| metal | Bon Jovi | Thank You For Loving Me | 67 | popular |
| deep-house | Starley; Bad Paris | Arms Around Me - Bad Paris Remix | 55 | popular |
| deep-house | The Him;Lissa | I Wonder | 43 | not popular |
| metal | Deftones | Ohms | 0 | not popular |

## 9 Hypothesis Testing

In our hypothesized universe of no difference in genre popularity, popularity is relevant and thus it is of no consequence to randomly “shuffle” the values of popular_or_not. The popular_or_not column in the spotify_52_shuffled data frame in the modernverse package shows one possible random shuffling.

```
spotify_52_shuffled |>
select(-track_id) |>
head(10)
```

TABLE 9.4: Shuffled version of popular_or_not in representative sample of metal and deep-house songs

| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | Jess Bays; Poppy Baskcomb | Temptation (feat. Poppy Baskcomb) | 63 | popular |
| metal | Whitesnake | Here I Go - 2018 Remaster | 69 | not popular |
| metal | Blind Melon | No Rain | 1 | popular |
| metal | Avenged Seven | Shepherd of Fire | 70 | not popular |
| deep-house | Nora Van Elken | I Wanna Dance With Sammy (Who Loves Me - Summer Edit) | 56 | popular |
| metal | Breaking Benjamin | Ashes of Eden | 61 | not popular |
| metal | Bon Jovi | Thank You For Loving Me | 67 | not popular |
| deep-house | Starley;Bad Paris | Arms Around Me - Bad Paris | 55 | not popular |
| deep-house | The Him;Lissa A | I Wonder | 43 | not popular |
| metal | Deftones | Ohms | 0 | not popular |

Observe in the popular_or_not column how the popular and not popular results are now listed in a different order. Some of the original popular now are not popular, some of the not popular are popular, and others are as the original.

Again, such random shuffling of the popular_or_not label only makes sense in our hypothesized universe of no difference in popularity between genres. Is there a tactile way for us to understand what is going on with this shuffling? One way would be using a standard deck of 52 playing cards, which we display in Figure 9.3.

![](img/445742518041017e8f01f11b0c3190d9_346_0.png)

FIGURE 9.3: Standard deck of 52 playing cards.

## 9.2 Music popularity activity

Since we started with equal sample sizes of 1000 songs for each genre, we can think about splitting the deck in half to have 26 cards in two piles (one for metal and another for deep-house). After shuffling these 52 cards as seen in Figure 9.4, we split the deck equally into the two piles of 26 cards. Then, we can flip the cards over-by-one, assigning 'popular' for each red card and 'not popular' for each black card keeping a tally of how many of each genre are popular.

![](img/445742518041017e8f01f11b0c3190d9_347_0.png)

FIGURE 9.4: Shuffling a deck of cards.

Let's repeat the same exploratory data analysis we did for the original spotify_metal_deeouse data on our spotify_52_original and spotify_52_shuffled data frames. We create a subplot visualizing the relationship between track_genre and the new shuffled popular_or_not variable, and compare this to the original version in Figure 9.5.

```
ggplot(spotify_52_shuffled, aes(x = track_genre, fill = popular_or_not)) +
geom_bar() +
labs(x = "Genre of track")
```

![](img/445742518041017e8f01f11b0c3190d9_347_1.png)

FIGURE 9.5: Barplots of relationship of genre with 'popular or not' (left) and shuffled 'popular or not' (right).

The difference in metal house popularity rates is now different. Compared to the original data in the left barplot, the new “shuffled” data in the right barplot has popularity rates that are actually in the opposite direction as they were. This is because the shuffling process has removed any relationship between genre and popularity. Let’s also compute the proportion of tracks that are now “popular” in the popular_or_not column for each genre:

```
spotify_52_shuffled |
group_by(track_genre, popular_or_not) |
tally()

# A tibble: 4 x 3
# Groups: track_genre [2]
track_genre popular_or_not n
<chr> <chr> <int>
1 deep-house not popular 10
2 deep-house popular 16
3 metal not popular 13
4 metal popular 13

So in this case of a hypothetical universe of no difference in genre popularity, on the other hand, 16/26 = 0.5 = 50% of metal songs were popular. Let's compare these two values. It appears that metal tracks were popular at a rate that was 0.5 – 0.615 = –0.115 = –11% different than deep house songs. Observe how this difference in rates is not the same as the difference in rates of 0.034 = 3.4% we observed. This is once again due to sampling variation. Can we better understand the effect of this sampling variation? By repeating the shuffling several times!

### 9.2.3 What did we just do?

What we demonstrated in this activity is the statistical procedure known as hypothesis testing using a permutation test. The term “permutation” is the mathematical term for “shuffling”: taking a series of values and reordering them randomly, as you did with the playing cards. In fact, permutations are another form of resampling, like the bootstrap method performed in Chapter 8. While the bootstrap method involves resampling with replacement, permutation methods involve resampling without replacement.

We do not need to restrict our analysis to a dataset of 52 rows only. It is useful to manually shuffle the deck of cards and assign values of popular or not to different songs, but the same ideas can be applied to each of the 2000 tracks in spotify_metal_deeouse data. We can think of this data as an inference about an unknown difference in population proportions with the 200 tracks being our sample. We denote this as $p_m - p_d$, where $p_m$ is the population proportion of songs with metal names being popular and $p_d$ is the equivalent for deep house songs. Recall that this is one of the scenarios for inference we have seen so far in Table 9.5.

## 9.3 Understanding hypothesis tests

TABLE 9.5: Scenarios of sampling for inference

| Scenario | Population parameter | Notation | Point estimate | Symbol(s) |
|---|---|---|---|---|
| 1 | Population proportion | $p$ | Sample proportion | $\hat{p}$ |
| 2 | Population mean | $\mu$ | Sample mean | $\bar{X}$ or $\hat{\mu}$ |
| 3 | Difference in population proportions | $p_1 - p_2$ | Difference in sample proportions | $\hat{p}_1 - \hat{p}_2$ |

So, based on our sample of $n_m = 1000$ metal tracks and $n_f = 1000$ deep house tracks, the point estimate for $p_m - p_d$ is the *difference in sample proportions*

> $\hat{p}_m - \hat{p}_f = 0.563 - 0.529 = 0.034 = 3.4\%$.

This difference in favor of metal songs of 0.034 is greater than 0, suggesting metal songs are more popular than deep house songs. However, the question we ask ourselves “is this difference meaningfully greater than 0?”, or can we just attribute it to *sampling variation*? Much like the terminology, notation, and definitions relating to sampling you saw in Section 7.2, there are a lot of terminology, notation, and definitions related to hypothesis testing as well. Some of this was introduced in Section 9.1. Learning this may seem like a very daunting task at first. However, with practice, practice, and more practice, anyone can master them.
