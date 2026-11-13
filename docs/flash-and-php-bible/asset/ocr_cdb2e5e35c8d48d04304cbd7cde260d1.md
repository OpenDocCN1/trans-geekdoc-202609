You may remember from the PHP section of this example that the data is returned in name/value object pairs. That data is stored in the data property of the newly created loader instance.

This data is passed into an instance of the URLVariables class, which creates an ActionScript Object so other portions of the script can handle the data.

```
var dataObj:URLVariables = new URLVariables(loader.data);
```

Now that the data is loaded, you can test it using a simple trace statement that should display the total entries returned.

```
trace("Total Albums: " + dataObj.total);
```

That trace call should display the following in the Output panel:

```
//Output: **Total Albums: 5**
```

This means the PHP file is being called and the data is being loaded properly from the database using PHP as the data handler in the middle.

You could end the script here, because it all works, but continue using a for.. loop to display the information from each album using a series of trace calls for simplicity.

The for.. loop is set up using the total property of the dataObj to determine how many times the loop should run.

```
for(var i:uint = 0; i < dataObj.total; i++)
{
...
}
```

The first trace within the for.. loop displays the current album being displayed. The current album number is created using the i variable of the loop with 1 added to it. The reason for this is because the i variable starts at zero, and for display purposes the first album should be 1.

```
trace("Album " + (i + 1));
```

The next trace statement is set up to display the current artist. The value is captured from the dataObj Object instance using a dynamic object reference. The "artist" name is appended to the i variable, which creates an instance name.

```
trace(" Artist: " + dataObj['artist' + i]);
```

The remaining trace statements are duplicates of the previous one, with the instance name and description slightly modified.

```
trace(" Album: " + dataObj['album' + i]);
trace(" Genre: " + dataObj['genre' + i]);
```

At this point, the loop is completed and so is the entire sample application. You can now test the example and should see the trace statements displayed in the Output panel, as shown in Figure 3.4.