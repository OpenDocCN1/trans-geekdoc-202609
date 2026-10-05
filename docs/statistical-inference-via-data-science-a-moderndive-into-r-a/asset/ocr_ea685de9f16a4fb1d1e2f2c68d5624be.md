# 9.2 Music popularity activity 309

the other genres and popularity in the Learning checks. Let's explore this data by focusing on just metal and deep-house by looking at twelve randomly selected rows and our columns of interest. Note here that we also group selection so that three songs of the four possible groupings of track_genre and popular_or_not are selected.

```
spotify_metal_deephouse <- spotify_by_genre |>
filter(track_genre%in%c("metal", "deep-house")) |>
select(track_genre, artists, track_name, popularity, popular_or_not)
spotify_metal_deephouse |>
group_by(track_genre, popular_or_not) |>
sample_n(size = 3)
```

| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|--|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| metal | Slipknot | Psychosocial | 66 | popular |
| deep-house | BCX | Miracle In The Of My Heart – Original Mix | 41 | not popular |
| metal | | | | 0 | not popular |
| deep-house | Junge Jungle:Tyron Hapi | I'm The One – Tyron Hapi | 49 | not popular |
| metal | | Every Rose Has Thorn – Remastered 2003 | 0 | not popular |
| metal | Armored Dawn | S.O.S. | 54 | popular |
| deep-house | James Hype:Mia Pia:PSI | Good Luck (feat. Pia Mia) – PS1 Remix | 47 | not popular |
| metal | Hollywood Undead | Riot | 26 | not popular |
| metal | Breaking Benjamin | Ashes of Edhen | 61 | popular |

TABLE 9.2: Sample of twelve songs from the Spotify data.

The track_genre variable indicates which genre the song is classified under, the artists and track_name columns provide additional information about the track by providing the artist and the name of song, popularity is the metric mentioned earlier by Spotify, and popular_or_not is a categorical representation of the popularity color with value 50 (75th percentile of popularity) referring to popular and anything at or below 50 as not_popular. The decision made by the authors to call a song “popular” if it is above the 75th percentile of popularity is arbitrary and could be changed to any other value.

Let's perform an exploratory data analysis of the relationship between the two categorical variables track_genre and popular_or_not. Recall that we saw in Subsection 2.8.3 one way we can visualize such a relationship is using a stacked barplot.