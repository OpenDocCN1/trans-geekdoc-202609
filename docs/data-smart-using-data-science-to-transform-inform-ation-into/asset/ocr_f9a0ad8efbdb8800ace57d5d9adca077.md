Looking over the impurity values, for my workbook (yours will likely be different due to the random sort), the winning feature is Prenatal Yoga.

# Recording the Winner

All right, so prenatals won on this sample for me. You probably got a different winner, which you should record somewhere. Our next step will be to record a winner. The data as it stands won’t get us there completely. We’ll need to figure who the winner is and the column it belongs to. We’ll use this information later as you’ll see.

To get started, in cells G13:G17, we’ll create the following labels running vertically down the range: Min Value, Winner Col, Column Name, Col ID, Pregnant. Then in the adjacent cells in column H we’ll add the following formulas corresponding to their respective label in Column G:

+   • Min Value: =MIN(I10:L10)
+   First, we’ll need to figure out which column is the winner. The MIN function will give us this value.

+   • Winner Col: =MATCH(H13,I10:L10,0)
+   Next, we’ll need MATCH this value back into that same list of impurity results. This function will give us the column number pulled from out sample.

+   • Column Name: =INDEX(A1#,H14)
+   From here, we can figure out the name of that column. This is what INDEX helps us do.

+   • Col ID: =MATCH(H15,TrainingData[#Headers], 0)
+   Now, to get the location of this column on the original dataset, we’ll have to match the column name into the header section of our Excel table that holds the training data.

+   • Pregnant =INDEX(I6:L6,H14)

Finally, we’ll need to understand if this column indicates pregnancy.

So now, in cells N1 and N2, label them as Winner and Pregnant Is. You’ll save the winning stump in column O. Start with saving the winning column number in cell O1. You can just set this equal to cell H16:

```
=H16
```

This would be the value that has the lowest impurity (in my case that’s 15).

Similarly, in O2 you can put whether 0 or 1 is associated with pregnancy. Luckily, we just calculated this value. So, set it equal to cell H17.

```
=H17
```

The winning decision stump and its pregnancy-associated node are then called out, as pictured in Figure 7.14.