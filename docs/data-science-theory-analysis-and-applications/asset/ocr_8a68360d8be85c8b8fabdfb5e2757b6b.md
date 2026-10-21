```
Begin
    While (cursor!=empty)
    Begin
    //retrieve the locations from the database//
    R.append(document); //add the location to
Result List//
    End
End
Add null to R
```

4. Return result list, R

# 3. Algorithm—Range Join Query Using Zone Sharding

**Input:** The location is taken as input, i.e., the latitude and longitude.
**Output:** Result List, R, i.e., locations in a particular range, are retrieved.

+   1. Find “zone” variable //based on the zone of the input location//
+   2. Create cursor A, B for input query //to access the desired documents from the database//
+   3. if(cursor A!= empty || cursor B!=empty)

```
Begin
While(cursor A!=empty)
    Begin
    //retrieve the locations from the
database//
    R.append(document); //add the
location to Result List//
    End
While(cursor B!=empty)
    Begin
    //retrieve the locations from the database//
    R.append(document); //add the location to
Result List//
    End
End
Add null to R
```

4. Return result list, R

# 4. Algorithm—k-NN Query Using Zone Sharding

**Input:** The location, i.e., the latitude and longitude and k value, is taken as input.
**Output:** Result List, R, i.e., k nearest locations in a particular range are retrieved.

+   1. Find “k” variable //number of nearest locations//
+   2. Find “zone” variable //based on the zone of the input location//
+   3. Create “cursor” for input query //to access the desired documents from database//
+   4. if(cursor!=empty)

```
Begin
    While(cursor!=empty)
    Begin
    if(k==0) break;
```