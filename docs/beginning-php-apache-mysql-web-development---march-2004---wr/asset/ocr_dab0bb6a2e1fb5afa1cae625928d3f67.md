# Chapter 9

When retrieving data from the database, we will usually retrieve appropriate ids so that we can later insert or update the correct record. In this case, the id serves as the key to the array, making it easy to retrieve the values. We could have certainly used a multi-value array, but that gets a little more confusing, and its just not necessary here. Be sure you understand that many times in this application (and many apps using relational databases) you use the id as an array key.

Now we're going to do a little tricky. Because our list of powers could get quite large, we want to try to distribute them across multiple columns. However, we'd like to distribute them fairly evenly. The following 13 lines of code we do for this (if math is not interesting to you at all, or you simply don't want to know how this part of the code works, skip this section).

First, we get the count of powers in our array. Next, we set the threshold to 5 lines (after a second column will be created), and a maximum of columns (in this case, 3).

```
$numvar = count($powers);
$thresh = 5;
$maxcols = 3;
```

Next, we determine how many columns to create. Let's assume there are 7 powers to display. First, we divide the count by the (7/5), which gives us 1.4. Next, we use ceil() to round up to the nearest integer (ceil(1.4) = 2). Then we take the smaller of the two values (3 and 2), and store it in the $cols variable. In this example, $cols would create:

To show many powers into each column, we divide by the number of columns, and round up to the nearest. In this case, ceil(7/2) = 4. So, we'll have two columns, with four values in each column (the last column will contain the remainder of powers if there are less than four).

```
$powerch is a string that will contain each power, with a checkbox attached to it. For now, we initialize it to an empty string ''. $cols = min($maxcols,
$percol = ceil(count($powers)/$thresh));
$powerch = '';
```

Now we loop through each element of the $powers array, which contains the id as the key ($id), and in each loop, we add the <input> tag to create the checkbox, the id as the value, and the name of the power as the label. When our counter reaches a value that is divisible by $percol, we add a close table and start a new column.

```
$i = 0;
foreach($powers as $id => $p) {
  if (($i > 0) && ($i%$percol == 0)) {
    $powerch = "</td><ntd valign='top'>";
  }
  $powerch = "<input type='checkbox' name='powers[]'
  value='$id' <br />" . $powerch;
}
```

In our example, increments 0, 1, 2, and 3 up in the first column. When $i reaches 4 (the value of $percol), we start a new column. If this is confusing, don't worry. You can play around with it by

268