our customers have been able to purchase, and it all shows up in just that one command.

While this is something that is impressive, you may notice when you look at the output that there are a number of NaN's in the output. This is going to stand for Not a Number and will show us where there is not a value in place for us to work with. In many cases, we want to change this so that it says something like 0 instead of the NaN. We can do this with the function of fill_value as we see in the code below:

```
report = SALES.pivot_table(values=['quantity'],index=['Account Name'],columns=['category'], fill_value=0, aggfunc=np.sum)
report.head(n=10)
```

When you check out the output on this one, it should be a little bit nicer and cleaner to look at. We are going to then take this to one more step before we finish up. This will help us to see some more of the power that will show up with the pivot_table. For this one, we are going to work with some coding that will show us how much ins ales we were able to do:

```
report = SALES.pivot_table(values=['ext price','quantity'],index=['Account Name'],columns=['category'], fill_value=0,aggfunc=np.sum)
report.head(n=10)
```

It is even possible for us to take all of this and output it to Excel. We do need to go through a few steps to make this happen, such as converting all