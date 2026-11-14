Go ahead and copy the Optimization Model tab into a new sheet, called Relaxed Quality. You don’t have to change a whole lot to make this work.

Take a moment and think about how you might change things around to accommodate the new relaxed quality objective and cost constraint. Don’t peak ahead until your head hurts!

The first thing you do is pop $1,117,000 as the cost limit in cell D2 near the old objective. Also, copy and paste values of the old minima and maxima for taste and color into columns H and I, respectively. And in column G on rows 27 through 30, add a new decision variable called % Relaxed.

Now consider how you might use the Brix/Acid relaxation decision in cell G27 to relax the lower bound of 11.5. Currently, the allowable band of Brix/Acid is 11.5 to 12.5, which is a width of 1 unit. So, a 10 percent broadening at the bottom of the constraint would make the minimum 11.4.

Following this approach, replace the minimum in B27 with this formula:

```
=H27-G27*(I27-H27)
```

This takes the old minimum, now in H27, and subtracts from it the percent relaxation times the distance of the old maximum from the old minimum (I27 minus H27). You can copy this formula down through row 30. Similarly, implement the relaxed maximum in column F. (Hint: use =I27+G27*(I27-H27) in F27)

For the objective, take the average of the relaxation decisions in G27:G30. Placing this calculation in cell E2, the new sheet now looks like in Figure 9.20.

![](bbox=[0.135, 0.585, 0.825, 0.93])

Figure 9.20: Relaxed quality model