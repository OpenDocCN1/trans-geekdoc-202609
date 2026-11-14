Let's prepare the data needed for our model. Here we will follow the steps required to delete a column that has missing values.

1. Find a search box on the top-left corner, enter Select Columns. Click the Select Columns in Dataset. This module allows you to include or exclude the columns.

2. Now, drag and connect the input port of Select Columns in Dataset module with the output port of let's say XYZdata module.

3. Click the Select Columns in Dataset module.

4. In the Properties pane, choose and click the Launch Column Selector.

5. On the left, click the With rules option.

6. Choose the All Columns option under the Begin with option.

7. Choose the Exclude option and Column names from the two dropdown lists you see. Then choose the Normalized losses option from the list of columns displayed on the screen.

8. To close the column selector window, click the tick mark button on the bottom right of the window.

9. At this point, except Normalized-losses, all the columns will pass through.

10. Just when you have connected the first two modules, drag the clean missing data module and combine it with the Select Columns in Dataset module in the experiment window.

11. Remove the rows with the missing values, select Remove entire row option under the Cleaning mode options in the Properties pane.

12. Double-click on the module named Clean missing data and type the comment “Remove missing value rows.”

13. Click the RUN button placed at the bottom of the page.

Now, you have successfully preprocessed the raw data.