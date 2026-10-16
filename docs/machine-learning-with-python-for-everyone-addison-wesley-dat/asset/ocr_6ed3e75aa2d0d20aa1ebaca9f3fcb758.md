```
In [44]:

k_data = metrics.pairwise.polynomial_kernel(data, data,
                                            degree=2) # squares
print('first example: ', data[0])

print('# features in original form:', data[0].shape)
print('# features with kernel form:', k_data[0].shape)

print('# examples in both:', len(data), len(k_data))
```

first example: [-2. -2.]
# features in original form: (2,)
# features with kernel form: (400,)
# examples in both: 400 400

That may have been slightly underwhelming and probably a bit confusing. When we applied the kernel to our 400 examples, we went from having 2 features to having 400 features. Why? Because kernels redescribe the data in terms of the relationship between an example and every other example. The 400 features for the first example are describing how the first example relates to every other example. That makes it a bit difficult to see what is going on. However, we can force the kernel features to talk. We'll do it by feeding the kernelized data to a prediction model and then graphing those predictions back over the original data. Basically, we are looking up information about someone by their formal name—Mark Fenner lives in Pennsylvania—and then associating the result with their nickname—Marco lives in Pennsylvania.

One other quick point: if you are reminded of covariances between pairs of features, you aren't too far off. However, kernels are about relationships between examples. Covariances are about relationships between features. One is between columns; the other is between rows.

```
In [45]:

fig, ax = plt.subplots(figsize=(4,3))

# learn from k_data instead of original data
preds = (linear_model.LogisticRegression()
        .fit(k_data, tgt)
        .predict(k_data))

ax.scatter(xs, ys, c=np.where(preds, 'r', 'b'), marker='.')
ax.set_aspect('equal')
```