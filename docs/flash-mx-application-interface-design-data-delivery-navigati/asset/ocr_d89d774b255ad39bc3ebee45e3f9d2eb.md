We then add another line to define the function that will export our recorded details into the correct array format:

```
exportAll = function () {
```

and set our initial output string to be clear:

```
exportStr = "";
```

The if statement here makes sure that there is something to export. If there isn't, Flash jumps ahead to the code after the else command.

```
if (changeFrame.length>0) {
```

We then have a chunk of code that defines the format that the exported code will take:

```
exportStr += "\r// export code begins // \r";
exportStr += "changeFrame = new Array ();\r";
exportStr += "rightPosX = new Array ();\r";
exportStr += "rightPosY = new Array ();\r";
exportStr += "leftPosX = new Array ();\r";
exportStr += "leftPosY = new Array ();\r";
exportStr += "rightRot = new Array ();\r";
exportStr += "leftRot = new Array ();\r";
exportStr += "caption = new Array ();\r";
exportStr += "////////////////////////////////// \r";
```

\r gives us a new line, and the += operator adds the new information to the end of the current value of the export string.

We then need some code that exports the data that has been recorded:

```
for (count=0; count<changeFrame.length;
count++) {
```

![](bbox=[0.066, 0.912, 0.982, 0.992])

We need to have the collection of different arrays exported for each instruction we have recorded. The for loop will do that by creating a count variable and comparing it to the length of the changeFrame array, exporting the arrays until count has the same value as the length of the array. We could have chosen any of our arrays to act as the indicator of the total length of arrays, but I've chosen changeFrame.

We then add some code that writes out the arrays from the details recorded:

```
exportStr += "changeFrame ["+count+"] = "
+ "+changeFrame[count]+",\r";
exportStr += "rightPosX ["+count+"] = "
+ "+rightPosX[count]+",\r";
exportStr += "rightPosY ["+count+"] = "
+ "+rightPosY[count]+",\r";
exportStr += "leftPosX ["+count+"] = "
+ "+leftPosX[count]+",\r";
exportStr += "leftPosY ["+count+"] = "
+ "+leftPosY[count]+",\r";
exportStr += "rightRot ["+count+"] = "
+ "+rightRot[count]+",\r";
exportStr += "leftRot ["+count+"] = "
+ "+leftRot[count]+",\r";
exportStr += "comment ["+count+"] = "
"\""+caption[count]+"\"\r";
exportStr += "////////////////////////////////// \r";
}
```

The caption export string needs to have quotation marks surrounding its exported content, so escaped quotes are added to that line before and after "+caption[count]+".