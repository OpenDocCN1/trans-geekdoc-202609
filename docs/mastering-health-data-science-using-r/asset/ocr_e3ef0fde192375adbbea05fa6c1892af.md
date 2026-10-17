```
pain_body_map <- data.frame(part = names(pain_df)[2:75])
pain_body_map$num_patients <- colSums(pain_df[, 2:75])
pain_body_map$perc_patients <- pain_body_map$num_patients /
                              nrow(pain_df)

pain_body_map$avg_pain <- colSums(pain_df[, 2:75] *
                                  pain_df$PAIN_INTENSITY_AVERAGE) /
                          pain_body_map$num_patients

pain_body_map <- pain_body_map %>%
    mutate(region = case_when(
    part %in% c("X208", "X209", "X218", "X219", "X212",
                "X213", "X222") ~ "Back",
    part %in% c("X105", "X106", "X205", "X206") ~ "Neck",
    part %in% c("X107", "X110", "X207", "X210") ~ "Shoulders",
    part %in% c("X108", "X109", "X112", "X113") ~ "Chest/Abs",
    part %in% c("X126", "X127", "X228", "X229",
                "X131", "X132", "X233", "X234") ~ "Legs",
    part %in% c("X111", "X114", "X211", "X214", "X115", "X116",
                "X117", "X118", "X217", "X220") ~ "Arms",
    part %in% c("X119", "X124", "X221", "X226", "X125", "X128",
                "X227", "X230") ~ "Wrists/Hands",
    part %in% c("X215", "X216") ~ "Elbows",
    part %in% c("X135", "X136", "X237", "X238", "X133", "X134",
                "X235", "X236") ~ "Feet/Ankles",
    part %in% c("X129", "X130", "X231", "X232") ~ "Knees",
    part %in% c("X101", "X102", "X103", "X104", "X201", "X203",
                "X202", "X204") ~ "Head",
    part %in% c("X120", "X121", "X122", "X123", "X222", "X223",
                "X224", "X225") ~ "Hips"))

head(pain_body_map)
#>  part num_patients perc_patients avg_pain region
#> 1 X101          323        0.0646      6.69    Head
#> 2 X102          322        0.0644      6.82    Head
#> 3 X103          165        0.0330      6.86    Head
#> 4 X104          165        0.0330      6.95    Head
#> 5 X105          493        0.0986      6.90    Neck
#> 6 X106          507        0.1014      6.92    Neck
```

Within the theme we’ve chosen, we are able to update any of the theme options (see ?theme). In the following code, we use the theme() function to update the legend position to the bottom and the grid lines to light pink. Additionally, we add a horizontal line using the geom_hline() function (geom_vline() and geom_abline() can add vertical or diagonal lines, respectively) and add a text annotation using the annotate() function. The resulting plot shows the aver-