```
loss = np.abs(error)

fig, ax = plt.subplots(1,1,figsize=(4,3))
ax.plot(error, loss)

ax.set_xlabel('Raw Error')
ax.set_ylabel('Abs Loss');
```

![](bbox=[0.28, 0.3, 0.66, 0.55])

How can we ignore errors up to a certain threshold? For example, let's write code that ignores absolute errors that are less than 1.0:

In [11]:

```
an_error = .75
abs_error = abs(an_error)
if abs_error < 1.0:
    the_loss = 0.0
else:
    the_loss = abs_error
print(the_loss)
```

0.0

Now we are going to get fancy. Pay close attention. We can rewrite that with some clever mathematics. Here's our strategy:

+   1. Subtract the threshold value from the absolute error.
+   2. If the result is is bigger than zero, keep it. Otherwise, take zero instead.