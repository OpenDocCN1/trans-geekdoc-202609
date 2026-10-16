# Add Number of Copies and Number Reserved

Select the + after the `image_file` field to add two new fields to the end of the `movieListing` table.

For the `number_of_copies` field:

+   - In the **Column name** below `image_file`, enter `number_of_copies`
+   - Select the “Type” as int
+   - Enter **11** for the “Length”
+   - Check the box and enter **1** for “Default value”

And for the `number_reserved` field:

+   - In the **Column name** below `number_of_copies`, enter `number_reserved`
+   - Select the “Type” as int
+   - Enter **11** for the “Length”
+   - Check the box and enter **0** for “Default value”

Once you press **Save**, the table description should look like Figure 25.2. Now all the movies in our `movieListing` table have `number_of_copies` set to 1, and `number_of_reserved` set to 0 as shown in Figure 25.3.

![](bbox=[0.41, 0.1, 0.92, 0.36])

![](bbox=[0.62, 0.37, 0.92, 0.65])

![](bbox=[0.13, 0.67, 0.92, 0.88])