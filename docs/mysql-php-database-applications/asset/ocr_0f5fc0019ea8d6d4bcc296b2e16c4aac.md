![](bbox=[0.139, 0.083, 0.802, 0.453])

# Figure 3-9: Table where using sum() would be helpful

To get the total from each state you'd run the following query:

```
select state, sum(contribution) from contributions group by state;
```

# min()

The min() function pulls out the lowest value in each grouping. To find the lowest contribution from any state just make a small change to the previous query:

```
select state, min(contribution) from contributions group by state;
```

# max()

As you probably guessed, max() will return the highest value in a group:

```
select state, max(contribution) from contributions group by state;
```

# avg()

avg () returns the average of the group:

```
select state, sum(contribution) from contributions group by state;
```

You can throw all these together to create a pretty useful query, as Figure 3-10 and the following query show: