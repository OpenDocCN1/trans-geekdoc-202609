```
axes[0].plot(bound_xs, bound_ys, 'k')
axes[0].set_title('Classification')

axes[1].pcolormesh(xs, ys, r_tgt,cmap='binary')
axes[1].set_aspect('equal')
axes[1].set_title('Regression');
```

![](bbox=[0.2, 0.35, 0.8, 0.58])

Before we compute any statistics here, let's think about this scenario for a minute. If you tell me the value of y and it is less than zero, I know an awful lot about the result: it's always blue (for classification) or white (for regression). If y is bigger than zero, we don't get as much of a win, but as y keeps increasing, we get a higher likelihood of red (in the left figure) or black (in the right figure). For x, a value greater or less than zero doesn't really mean much: things are perfectly balanced about the x-axis.

That said, we can look at the information-based metric for c_tgt which is calculated using mutual_info_classif:

```
In [21]:

print(ftr_sel.mutual_info_classif(data, c_tgt,
    discrete_features=False, random_state=42))

[0.0947 0.1976]
```

The relative values for the r_tgt regression problem are broadly similar to those for mutual_info_regression:

```
In [22]:

print(ftr_sel.mutual_info_regression(data, r_tgt.flat,
    discrete_features=False))

[0.0512 0.4861]
```

These values line up well with our intuitive discussion.