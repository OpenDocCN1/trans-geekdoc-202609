```
```python
ax.set_xlabel("# People")
ax.set_ylabel("Cost\\n(Parking Only)");
```
```

![](bbox=[0.22, 0.24, 0.78, 0.51])

In a math class, we would write this as total_cost = 40.0. That is, regardless of the number of people—moving back and forth along the x-axis at the bottom—we pay the same amount. When mathematicians start getting abstract, they reduce the expression to simply y = 40. They will talk about this as being “of the form” y = c. That is, the height or the y-value is equal to some constant. In this case, it’s the value 40 everywhere. Now, it doesn’t do us much good to park at the show and not buy tickets—although there is something to be said for tailgating. So, what happens if we have to pay $80 per ticket?

In [22]:

```
```python
people = np.arange(1, 11)
total_cost = 80.0 * people + 40.0
```
```

Graphing this is a bit more complicated, so let’s make a table of the values first:

In [23]:

```
```python
# .T (transpose) to save vertical space in printout
display(pd.DataFrame({'total_cost':total_cost.astype(np.int)},
                     index=people).T)
```
```

|  | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|---|---|---|---|
| **total_cost** | 120 | 200 | 280 | 360 | 440 | 520 | 600 | 680 | 760 | 840 |