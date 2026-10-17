```
tbl_summary(tb_df, by = "tb",
            label = list(
              tb = "Tuberculosis",
              age_group = "Age Group",
              hiv_pos = "HIV Positive",
              ever_smoke = "Ever Smoked",
              past_tb = "Past TB",
              male = "Male",
              hs_less = "High School or Less Educ.",
              two_weeks = "Two Weeks Symptoms",
              diabetes = "Diabetes",
              num_symptoms = "Number of Symptoms"
            )) %>%
add_overall() %>%
as_gt() %>%
cols_width(everything() ~ "55pt")
```

| Characteristic | Overall, N = 1,405¹ | TB Negative, N = 704¹ | TB Positive, N = 701¹ |
|---|---|---|---|
| Age Group | | | |
| [15,25) | 205 (15%) | 121 (17%) | 84 (12%) |
| [25,35) | 286 (20%) | 120 (17%) | 166 (24%) |
| [35,45) | 338 (24%) | 136 (19%) | 202 (29%) |
| [45,55) | 305 (22%) | 158 (22%) | 147 (21%) |
| [55,99) | 271 (19%) | 169 (24%) | 102 (15%) |
| HIV | | | |
| Positive | | | |
| 0 | 808 (59%) | 503 (73%) | 305 (45%) |
| 1 | 556 (41%) | 186 (27%) | 370 (55%) |
| Unknown | 41 | 15 | 26 |
| Ever | | | |
| Smoked | | | |
| 0 | 899 (64%) | 483 (69%) | 416 (60%) |
| 1 | 496 (36%) | 213 (31%) | 283 (40%) |
| Unknown | 10 | 8 | 2 |
| Past TB | | | |
| 0 | 1,186 (84%) | 613 (87%) | 573 (82%) |
| 1 | 219 (16%) | 91 (13%) | 128 (18%) |
| Male | | | |
| 0 | 669 (48%) | 394 (56%) | 275 (39%) |
| 1 | 736 (52%) | 310 (44%) | 426 (61%) |
| Diabetes | | | |