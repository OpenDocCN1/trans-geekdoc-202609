```
baseline = dummy.DummyClassifier(strategy="uniform")

base_score = skms.cross_val_score(baseline,
    digits.data, digits.target==1,
    cv=10,
    scoring='average_precision',
    n_jobs=-1)
```

We evaluate our solutions with cross-validation on the digits dataset.

In [53]:

```
fig, ax = plt.subplots(figsize=(6,4))
ax.plot(base_score, label='base')
for name, model in classifier_parade.items():
    cv_scores = skms.cross_val_score(model,
        digits.data, digits.target,
        cv=10,
        scoring='f1_macro',
        n_jobs=-1) # all CPUs
    my_lbl = "{} ({:.3f})".format(name, cv_scores.mean())
    ax.plot(cv_scores, label=my_lbl, marker=next(markers))
ax.set_ylim(0.0, 1.1)
ax.set_xlabel('Fold')
ax.set_ylabel('Accuracy')
ax.legend(loc='lower center', ncol=2);
```

![](bbox=[0.22, 0.65, 0.78, 0.9])