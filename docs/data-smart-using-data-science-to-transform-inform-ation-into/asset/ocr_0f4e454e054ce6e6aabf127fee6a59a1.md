four columns from the table. We’ll be using one of Excel’s new dynamic formulas for this one, called CHOOSECOLS, which lets you select specific columns from a table or range.

```
=CHOOSECOLS (TD_BAG [#Headers] ,1,2,3,4)
```

![](bbox=[0.13, 0.195, 0.45, 0.535])

# Figure 7.8: Updated rows sorted randomly

In this case, we’re pulling from the headers of our table. This will populate the headings for our sample. CHOOSECOLS lets you choose which columns you want from a given range. Since we want the first four, we just type in 1, 2, 3, and 4. You’ll see this populates the randomly sorted headers. If you’d like, you can refresh Power Query to see the headers indeed randomly change with each run.

Admittedly, typing each number 1–4 isn’t feasible when there’s a large amount of data. That’s where the SEQUENCE function can help us. We’ll use it in a second.

Let’s go ahead and grab the sample data itself. In cell A2, use the following formula:

```
=CHOOSEROWS (CHOOSECOLS (TD_BAG, SEQUENCE (4)) , SEQUENCE (666))
```

CHOOSECOLS(TD_BAG, SEQUENCE(4)) pulls back the first four columns of the TD_BAG table. Next, we wrap that in a CHOOSEROWS. This lets us choose specific rows we’re interested in from our returned columns.

If we want to pull the first 666 from each column, we can use SEQUENCE to generate the set of data in [1-666].

And, in case you’re wondering, we could rewrite our previous header pull =CHOOSECOLS(TD_BAG[#Headers],1,2,3,4) as =CHOOSECOLS(TD_BAG[#Headers],SEQUENCE(4)). The choice is yours.