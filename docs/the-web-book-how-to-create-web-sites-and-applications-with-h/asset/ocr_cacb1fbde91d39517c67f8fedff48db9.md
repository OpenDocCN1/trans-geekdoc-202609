and quickly scan through the values of $room1, $room2, $room3 and $room4 to find out which are blank and which are "Y".

As you might expect, there's a handy shortcut, and that's to create an array of checkboxes. You'll remember the concept of PHP arrays from page 229. Here's a version of the above HTML code that uses a checkbox array:

```
Room 1 <input type="checkbox" name="rooms[]" value="1" /> <br>
Room 2 <input type="checkbox" name="rooms[]" value="2" /> <br>
Room 3 <input type="checkbox" name="rooms[]" value="3" /> <br>
Room 4 <input type="checkbox" name="rooms[]" value="4" /> <br>
```

Note that each checkbox now has the same name, which ends with 2 empty square brackets. Note too, that each checkbox has a unique value which corresponds to the room number. The above HTML displays the following, when included in a form:

![](bbox=[0.12, 0.425, 0.45, 0.52])

When the contents of the checkboxes is sent to the PHP code, the results will be in an array called $rooms. This array will contain *only* those checkboxes that were ticked (there's no way to retrieve a list of those that were not, which is sometimes annoying). The values in the array will be the same as the **value**= settings for those checkboxes. So, for example, if the visitor ticks boxes 2 and 4, the $rooms array will contain 2 elements (numbered 0 and 1, because arrays always start at 0). $rooms[0] will contain 2 (the first room selected) and $rooms[1] will contain 4.

Here's some PHP code to handle the above HTML. It steps through each of the entries in the $rooms array and displays the value:

```
$rooms = $_POST["rooms"];
$room_count = count($rooms);
echo "There were " . $room_count . " rooms chosen.<br>";
echo "The rooms you ticked were:<br>";
echo "<br>";
for ($i=0; $i <= count($rooms); $i++)
{
    echo $rooms[$i] . "<br>";
}
```