ignore from the raw error. If it takes us to a negative value, then maxing against zero will throw it out. For example, if we have an absolute error of .5 (from a raw error of .5 or −.5) and we subtract 1, we end up with an adjusted error of −1.5. Maxing with 0, we take the 0. We're left with zero—no cost. If you squint your eyes a bit, and turn your head sideways, you might be able to see a pair of doors with hinges at the kinks in the prior graph. That's where the name for the hinge loss comes from. When we apply the hinge loss around a known target, we get a band where we don't care about small differences.

In [14]:

```
```python
threshold = 2.5

xs = np.linspace(-5,5,100)
ys_true = 3 * xs + 2

fig, ax = plt.subplots(1,1,figsize=(4,3))
ax.plot(xs, ys_true)
ax.fill_between(xs, ys_true-threshold, ys_true+threshold,
                color=(1.0,0,0,.25))

ax.set_xlabel('Input Feature')
ax.set_ylabel('Output Target');
```
```

![](bbox=[0.28, 0.55, 0.7, 0.78])

Now, imagine that instead of knowing the relationship (the blue line above), we only have some data that came from noisy measurements around that true line:

In [15]:

```
```python
threshold = 2.5

xs = np.linspace(-5,5,100)
ys = 3 * xs + 2 + np.random.normal(0, 1.5, 100)
```
```