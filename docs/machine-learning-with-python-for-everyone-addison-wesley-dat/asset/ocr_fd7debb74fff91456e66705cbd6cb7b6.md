to a constant. Constants are a specific, restricted type of *horizontal* line. Our yellow line which passes through y = −3 is one.

We can combine our ideas about np.dot with our ideas about lines and write some slightly different code to draw this graph. Instead of using the pair (m, b), we can write an array of values w = (w₁, w₀). One trick here: I put the w₀ second, to line up with the b. Usually, that’s how it is written in mathe se: the w₀ is the constant.

With the ws, we can use np.dot if we augment our xs with an extra column of ones. I’ll write that augmented version of xs as xs_p1 which you can read as “exs plus a column of ones.” The column of ones serves the role of the 1 in y = mx + b. Wait, you don’t see a 1 there? Let me rewrite it: y = mx + b = mx + b · 1. See how I rewrote b → b · 1? That’s the same thing we need to do to make np.dot happy. dot wants to multiply something times w₁ and something times w₀. We make sure that whatever gets multiplied by w₀ is a 1.

I call this process of tacking on a column of ones the *plus-one trick* or *+1 trick* and I’ll have more to say about it shortly. Here’s what the plus-one trick does to our raw data:

In [26]:

```
# np.c_[] lets us create an array column-by-column
xs = np.linspace(-3, 3, 100)
xs_p1 = np.c_[xs, np.ones_like(xs)]

# view the first few rows
display(pd.DataFrame(xs_p1).head())
```

|   | 0 | 1 |
|---|---|---|
| 0 | -3.0000 | 1.0000 |
| 1 | -2.9394 | 1.0000 |
| 2 | -2.8788 | 1.0000 |
| 3 | -2.8182 | 1.0000 |
| 4 | -2.7576 | 1.0000 |

Now, we can combine our data and our weights very concisely:

In [27]:

```
w = np.array([1.5, -3])
ys = np.dot(xs_p1, w)

ax = plt.gca()
ax.plot(xs, ys)

# styling
ax.set_ylim(-4, 4)
high_school_style(ax)
```