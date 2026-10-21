![](bbox=[0.34, 0.12, 0.62, 0.7])

FIGURE 1.15 Executor task in tag sharding.

+   1. Find “Tag” variable using GetTag() //based on the tag of the input location//
+   2. Create “cursor” for input query //to access the desired documents from the database//
+   3. if (cursor!=empty)
+   
+   Begin
+       While (cursor!=empty)
+       Begin //retrieve the locations from the database//
+       R.append(document); //add the location to Result //
+       List
+       End
+   End
+   else
+       Add null to R
+   4. Return result list, R