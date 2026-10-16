Again, we’ll get started by generating some synthetic data. The generation process is a hint more complicated. You might remember that the linear regression part of logistic regression was producing the log-odds. To get to an actual class, we have to convert the log-odds into probabilities. If we’re simply interested in the target classes, we can use those probabilities to pick classes. However, when we select a random value and compare it to a probability, we don’t get a guaranteed result. We have a probability of a result. It’s a random process that is inherently noisy. So, unlike the noiseless regression data we used above, we might see benefits from regularization.

In [12]:

```
logreg_ftr = np.random.uniform(5,15, size=(100,))

true_wgts = m,b = -2, 20
line_of_logodds = m*logreg_ftr + b
prob_at_x = np.exp(line_of_logodds) / (1 + np.exp(line_of_logodds))

logreg_tgt = np.random.binomial(1, prob_at_x, len(logreg_ftr))

logreg_ftrs_p1 = np.c_[logreg_ftr,
                    np.ones_like(logreg_ftr)]

logreg_table = pd.DataFrame(logreg_ftrs_p1,
                            columns=['ftr_1','ones'])
logreg_table['tgt'] = logreg_tgt
display(logreg_table.head())
```

|   | ftr_1 | ones | tgt |
|---|---|---|---|
| 0 | 8.7454 | 1.0000 | 1 |
| 1 | 14.5071 | 1.0000 | 0 |
| 2 | 12.3199 | 1.0000 | 0 |
| 3 | 10.9866 | 1.0000 | 0 |
| 4 | 6.5602 | 1.0000 | 1 |

Graphically, the classes—and their probabilities—look like

In [13]:

```
fig, ax = plt.subplots(figsize=(6,4))
ax.plot(logreg_ftr, prob_at_x, 'r.')
ax.scatter(logreg_ftr, logreg_tgt, c=logreg_tgt);
```