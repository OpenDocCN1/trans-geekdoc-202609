summary(aov(data=LongForm,C), Y ~ C*row + Error(id/C))) #ignores Script

Error: id

| Df Sum Sq Mean Sq F value Pr(>F)|
| row | 3 | 10.38 | 3.458 | 1.795 | 0.189 |
| Residuals | 16 | 30.82 | 1.927 |

Error: id:

| Df Sum Sq Mean Sq F value Pr(>F)|
| C | 3 | 5.95 | 1.984 | 7.555 | 0.000308 *** |
| C:row | 9 | 44.24 | 4.916 | 18.719 | 6.87e-13 *** |
| Residuals | 48 | 12.61 | 0.263 |

summary(aov(data=LongFormT, Y ~ Script*row + Error(id/Script)))

Error: id

| Df Sum Sq Mean Sq F value Pr(>F)|
| row | 3 | 10.38 | 3.458 | 1.795 | 0.189 |
| Residuals | 16 | 30.82 | 1.927 |

Error: id:Script

| Df Sum Sq Mean Sq F value Pr(>F)|
| Script | 3 | 42.46 | 14.154 | 53.894 | 2.13e-15 *** |
| Script:row | 9 | 7.74 | 0.859 | 3.273 | 0.00352 ** |
| Residuals | 48 | 12.61 | 0.263 |

summary(aov(data=LongFormT, Y-V*Script + Error(id/Script)))

Error: id

| Df Sum Sq Mean Sq F value Pr(>F)|
| Residuals | 19 | 41.2 | 2.168 |

Error: id:Script

| Df Sum Sq Mean Sq F value Pr(>F)|
| V | 1 | 40.54 | 40.54 | 113.603 | 3.45e-15 *** |
| Script | 2 | 1.92 | 0.96 | 2.691 | 0.0764 |
| Residuals | 57 | 20.34 | 0.036 |

Putting the analyses together, remembering SS_{BCR} = SS_{CR} - SS_{T} - SS_{C} and T, V,
T/V and C are tested against WSR:

| Source | df | SS | MS | F | p |
| Row | 3 | 10.38 | 3.458 | 1.80 | .189 |
| S/R | 16 | 30.82 | 1.927 | | |
| Script (T) | 3 | 42.46 | 14.154 | 53.894 | <001 |
| Valence (V) | 1 | 40.45 | 40.45 | 154.15 | .000 |
| T/V | 2 | 1.92 | .96 | 3.65 | .035 |
| C | 3 | 5.95 | 1.984 | 7.55 | .000 |
| BCR | 6 | 1.783 | .297 | | |
| WSR | 48 | 12.606 | .263 | | |