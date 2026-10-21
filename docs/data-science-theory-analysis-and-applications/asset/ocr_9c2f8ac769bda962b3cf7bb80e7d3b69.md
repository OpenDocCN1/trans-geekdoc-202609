![](bbox=[0.3, 0.14, 0.7, 0.75])

FIGURE 1.16 Master task in zone sharding.

# 3. Algorithm—Range Join Query Using Range Sharding

Input: The location is taken as input, i.e., the latitude and longitude.

Output: Result List, R, i.e., locations in a particular range are retrieved.

+   1. Find “Tag” variable using GetTag() //based on the tag of the input location//
+   2. Create “cursor A, B” for input query //access the desired documents from the database//
+   3. if (cursor A!= empty || cursor B!=empty)

```
Begin
    While (cursor A!=empty)
    Begin
    //retrieve the locations from the database//
    R.append(document); //add the location to
Result   //
```