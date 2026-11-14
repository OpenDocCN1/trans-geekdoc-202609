| A | B |
|---|---|
| Min Prediction | Max Prediction |
| -0.347 | 1.251 |
| | |
| Probability Cutoff for Pregnant Classification | Positive Predicted Value |
| -0.35 | 0.06 |
| -0.30 | 0.06 |
| -0.25 | 0.06 |
| -0.20 | 0.06 |
| -0.15 | 0.06 |
| -0.10 | 0.06 |
| -0.05 | 0.06 |
| 0.00 | 0.07 |
| 0.05 | 0.07 |
| 0.10 | 0.07 |
| 0.15 | 0.08 |
| 0.20 | 0.09 |
| 0.25 | 0.10 |

Figure 6.25: Precision calculations on the test set

Copying this calculation down through the other cutoff values, you should see it increase (see Figure 6.26). Once a cutoff value of 0.85 is reached, 100 percent of not-pregnant customers in the test set are appropriately predicted.

# False Positive Rate

The false positive rate is another common metric looked at to understand model performance. Since you already have the true negative rate, this can quickly be calculated as 1 minus the true negative rate. Label cell D4 as False Positive Rate and fill in the cells beneath as 1 minus the value in the adjacent cell in C. For D5, that's written as follows:

```
=1-C5
```

Copying this formula down, you can see that as the cutoff value increases, you get less false positives. In other words, you're committing fewer false positive (aka Type I) errors.

# True Positive Rate

The final metric you can calculate on your model's performance is called true positive rate. Depending upon your field, it might go by the names recall or sensitivity. I know what you're thinking: they should just pick one name and stick with it, right?