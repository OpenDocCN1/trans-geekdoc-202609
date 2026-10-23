![](bbox=[0.125, 0.085, 0.72, 0.365])

Wow! Which learning rate should we choose? This doesn’t look like the typical graph for lr_find(). I would choose 1e-5 as a starting point because the function keeps steadily decreasing at this point. For the second value I choose the former learning-rate divided by 5 – as a rule of thumb.

Of course you also try different values and check if the model trains faster. Finding the right learning rate is often kind of an art...

```
learner.fit_one_cycle(5, slice(1e-5, lr/5))
```

| epoch | train_loss | valid_loss | accuracy_multi | time |
| 0 | 0.151312 | 0.145205 | 0.947647 | 00:04 |
| 1 | 0.139855 | 0.148743 | 0.946471 | 00:04 |
| 2 | 0.133714 | 0.146716 | 0.949412 | 00:04 |
| 3 | 0.124596 | 0.142307 | 0.948529 | 00:04 |
| 4 | 0.114884 | 0.139296 | 0.949412 | 00:04 |

And now we want to see some of the results our model produces:

```
learner.show_results(figsize=(15, 15))
```